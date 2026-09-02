# Calendário

Prazos de reporte regulatório (CMVM, Banco de Portugal) e eventos da equipa. Clicar num dia com eventos
para ver os detalhes. Ver também: [Prazos e Obrigações Recorrentes](prazos-obrigacoes.md).

<div id="fc-calendar"></div>

<style>
#fc-calendar { font-family: inherit; max-width: 760px; margin: 1.5rem 0; }
.fc-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 12px; }
.fc-header h2 { margin: 0; font-size: 1.1rem; font-weight: 700; text-transform: capitalize; }
.fc-nav-btn {
  background: var(--md-primary-fg-color, #1a3fd4); color: #fff; border: none; border-radius: 6px;
  width: 32px; height: 32px; font-size: 16px; cursor: pointer; display: flex; align-items: center; justify-content: center;
}
.fc-nav-btn:hover { opacity: 0.85; }
.fc-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 4px; }
.fc-daylabel { text-align: center; font-size: 0.7rem; font-weight: 700; text-transform: uppercase; color: var(--md-default-fg-color--light, #888); padding: 4px 0; }
.fc-day {
  min-height: 64px; border: 1px solid var(--md-default-fg-color--lightest, #e0e0e0); border-radius: 6px;
  padding: 4px; font-size: 0.75rem; cursor: default; background: var(--md-default-bg-color, #fff);
}
.fc-day.fc-empty { border: none; background: none; }
.fc-day.fc-today { border: 2px solid var(--md-primary-fg-color, #1a3fd4); }
.fc-day.fc-has-events { cursor: pointer; }
.fc-day.fc-has-events:hover { background: var(--md-code-bg-color, #f5f5f5); }
.fc-daynum { font-weight: 600; }
.fc-dot { display: inline-block; width: 6px; height: 6px; border-radius: 50%; margin: 2px 2px 0 0; }
.fc-dot.cmvm { background: #1a3fd4; }
.fc-dot.bdp { background: #b06a10; }
.fc-dot.equipa { background: #0f7a5c; }
.fc-dot.outro { background: #7a5cff; }
.fc-legend { display: flex; gap: 14px; flex-wrap: wrap; margin-top: 10px; font-size: 0.75rem; }
.fc-legend span { display: inline-flex; align-items: center; gap: 5px; }
#fc-details {
  margin-top: 14px; padding: 10px 14px; border-radius: 8px; background: var(--md-code-bg-color, #f5f5f5);
  font-size: 0.85rem; display: none;
}
#fc-details h4 { margin: 0 0 6px; font-size: 0.85rem; }
#fc-details ul { margin: 0; padding-left: 18px; }
</style>

<script>
// ── EVENTOS ──────────────────────────────────────────────────────────
// Três formas de adicionar um evento — escolher a que se aplica e copiar uma linha:
//
// 1) Repete todos os meses, no mesmo dia:
//      { title: "Nome do evento", type: "outro", repeat: "monthly", day: 15 }
//
// 2) Repete todos os anos, na mesma data:
//      { title: "Nome do evento", type: "cmvm", repeat: "yearly", month: 3, day: 31 }
//
// 3) Acontece uma única vez, numa data específica:
//      { title: "Nome do evento", type: "equipa", date: "2026-09-15" }
//
// "type" define a cor do ponto: "cmvm", "bdp", "equipa" ou "outro".

const fcEvents = [
  // Prazos recorrentes já em vigor (ver também: Prazos e Obrigações Recorrentes)
  { title: "Reporte Anual PBC/FT à CMVM (Apêndice 2)", type: "cmvm", repeat: "yearly", month: 3, day: 31 },
  { title: "Relatório anual de eficácia do controlo (Compliance)", type: "cmvm", repeat: "yearly", month: 5, day: 31 },
  { title: "Faturação mensal — emissão de faturas", type: "outro", repeat: "monthly", day: 5 },
  { title: "Guia de pagamento do Imposto de Selo", type: "bdp", repeat: "monthly", day: 20 },

  // Eventos únicos — adicionar aqui abaixo
];

(function () {
  const monthNames = ["janeiro","fevereiro","março","abril","maio","junho","julho","agosto","setembro","outubro","novembro","dezembro"];
  const dayLabels = ["Dom","Seg","Ter","Qua","Qui","Sex","Sáb"];
  let current = new Date();
  current.setDate(1);

  const root = document.getElementById("fc-calendar");

  function eventsOnDay(y, m, d) {
    return fcEvents.filter((e) => {
      if (e.repeat === "monthly") return e.day === d;
      if (e.repeat === "yearly") return e.month === m + 1 && e.day === d;
      return e.date === `${y}-${String(m + 1).padStart(2, "0")}-${String(d).padStart(2, "0")}`;
    });
  }

  function render() {
    const year = current.getFullYear();
    const month = current.getMonth();
    const firstWeekday = new Date(year, month, 1).getDay();
    const daysInMonth = new Date(year, month + 1, 0).getDate();
    const todayStr = new Date().toISOString().slice(0, 10);

    let html = `
      <div class="fc-header">
        <button class="fc-nav-btn" id="fc-prev" aria-label="Mês anterior">‹</button>
        <h2>${monthNames[month]} ${year}</h2>
        <button class="fc-nav-btn" id="fc-next" aria-label="Mês seguinte">›</button>
      </div>
      <div class="fc-grid">`;

    dayLabels.forEach((d) => (html += `<div class="fc-daylabel">${d}</div>`));

    for (let i = 0; i < firstWeekday; i++) html += `<div class="fc-day fc-empty"></div>`;

    for (let d = 1; d <= daysInMonth; d++) {
      const dateStr = `${year}-${String(month + 1).padStart(2, "0")}-${String(d).padStart(2, "0")}`;
      const dayEvents = eventsOnDay(year, month, d);
      const isToday = dateStr === todayStr;
      const hasEvents = dayEvents.length > 0;
      html += `<div class="fc-day ${isToday ? "fc-today" : ""} ${hasEvents ? "fc-has-events" : ""}" ${hasEvents ? `data-date="${dateStr}"` : ""}>
        <div class="fc-daynum">${d}</div>
        <div>${dayEvents.map((e) => `<span class="fc-dot ${e.type}"></span>`).join("")}</div>
      </div>`;
    }

    html += `</div>
      <div class="fc-legend">
        <span><span class="fc-dot cmvm"></span> CMVM</span>
        <span><span class="fc-dot bdp"></span> Banco de Portugal / Fiscal</span>
        <span><span class="fc-dot equipa"></span> Equipa</span>
        <span><span class="fc-dot outro"></span> Outro</span>
      </div>
      <div id="fc-details"></div>`;

    root.innerHTML = html;

    document.getElementById("fc-prev").onclick = () => {
      current.setMonth(current.getMonth() - 1);
      render();
    };
    document.getElementById("fc-next").onclick = () => {
      current.setMonth(current.getMonth() + 1);
      render();
    };

    root.querySelectorAll(".fc-has-events").forEach((el) => {
      el.addEventListener("click", () => {
        const dateStr = el.getAttribute("data-date");
        const [y, m, dd] = dateStr.split("-").map(Number);
        const events = eventsOnDay(y, m - 1, dd);
        const details = document.getElementById("fc-details");
        details.innerHTML = `<h4>${String(dd).padStart(2,"0")}/${String(m).padStart(2,"0")}/${y}</h4><ul>${events.map((e) => `<li>${e.title}</li>`).join("")}</ul>`;
        details.style.display = "block";
      });
    });
  }

  render();
})();
</script>

!!! info "Como adicionar um evento"
    Editar a lista `fcEvents` no início do código desta página (`docs/geral/calendario.md`) — escolher um dos
    três formatos explicados nos comentários (repete todos os meses, repete todos os anos, ou acontece uma
    vez numa data específica) e copiar a linha correspondente. Eventos que se repetem só precisam de ser
    adicionados **uma vez** — aparecem automaticamente em todos os meses ou anos seguintes.
