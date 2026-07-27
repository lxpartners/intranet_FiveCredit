# Five Credit — Intranet (MkDocs + Cloudflare Pages)

Site de documentação interna, gerado a partir de ficheiros Markdown nesta pasta `docs/`. Todo o conteúdo real
da Five Credit (Book de Comunicação, Fluxo de Trabalho, Política de Compliance, Procedimentos Comercial e
Risco) já está incluído.

## Como isto funciona

- **Editar conteúdo** = editar um ficheiro `.md` dentro de `docs/` e enviar (`git push`). Não há botão
  "editar" dentro do site — quem tem acesso de escrita ao repositório GitHub é quem edita.
- **Ver o site** = qualquer pessoa com o URL publicado, a menos que ativem o Cloudflare Access (ver abaixo).
- **Login individual** = não existe um sistema de contas próprio (isto é um site estático). Para pedir
  autenticação individual antes de qualquer pessoa ver o site, usa-se o **Cloudflare Access** — gratuito até
  50 utilizadores.

## Novidades desta versão

- **Modo escuro** — botão no cabeçalho para alternar entre claro/escuro
- **Data real de "última atualização"** — cada página mostra a data da sua última alteração real, tirada do
  histórico do Git (não uma data escrita à mão)
- **Botão de imprimir/exportar** — em cada página, e uma página especial "Exportar / Imprimir tudo" que junta
  o site inteiro num único documento para imprimir ou guardar em PDF
- **Glossário**, **Prazos e Obrigações Recorrentes**, **Segurança da Informação** e **Continuidade de
  Negócio** — quatro secções novas, em "Geral" e "Compliance"
- **Menu reorganizado por equipa** — Comercial, Risco, Compliance e Geral, cada um com submenu

⚠️ Nota técnica: a data de "última atualização" só funciona corretamente se o projeto estiver dentro de um
repositório Git com histórico (o que já é o caso, visto que já o publicaram no GitHub). Isto já foi testado
e confirmado a funcionar.

## Ver localmente antes de publicar (opcional)

Requer Python instalado ([python.org](https://python.org)).

```bash
pip install -r requirements.txt
mkdocs serve
```

Abrir [http://localhost:8000](http://localhost:8000).

## Publicar

### 1. Enviar para o GitHub

```bash
git init
git add .
git commit -m "Primeira versão"
```

Criar um repositório vazio em [github.com/new](https://github.com/new), depois:

```bash
git remote add origin <URL do repositório>
git branch -M main
git push -u origin main
```

### 2. Ligar ao Cloudflare Pages

- No dashboard da Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
- Escolher o repositório que acabaram de publicar
- Nas definições de build:
  - **Framework preset:** None
  - **Build command:** `pip install -r requirements.txt && mkdocs build`
  - **Build output directory:** `site`
- **Save and Deploy**

Ao fim de um ou dois minutos, a Cloudflare dá um URL do tipo `nome-do-projeto.pages.dev` — já é o site publicado.
Cada novo `git push` para o repositório volta a publicar automaticamente.

### 3. (Opcional, mas recomendado) Adicionar login individual — Cloudflare Access

1. No dashboard da Cloudflare → **Zero Trust** → **Access** → **Applications** → **Add an application**
2. Escolher **Self-hosted**, e indicar o domínio do site (o `.pages.dev` ou um domínio próprio)
3. Criar uma política: por exemplo, "permitir emails que terminem em `@fivecredit.pt`"
4. Guardar

A partir daí, qualquer pessoa que abra o site tem de autenticar (normalmente com um código enviado para o
email da empresa) antes de conseguir ver qualquer página — isto é o que dá o "login individual" que
discutimos, sem precisar de um sistema de contas próprio.

## Estrutura do projeto

```
mkdocs.yml              # configuração do site e menu de navegação
requirements.txt         # dependências (mkdocs-material + plugins de data e impressão)
overrides/               # pequena correção de tradução (caixa de pesquisa)
docs/
  index.md               # página inicial
  book-comunicacao/       # 20 templates de email, por categoria
  fluxo-trabalho/         # 6 fases do processo de candidatura
  compliance/             # política de compliance, RGPD*, continuidade de negócio
  comercial/              # procedimentos comerciais
  risco/                  # procedimentos de risco
  rgpd/                   # proteção de dados
  reclamacoes/            # livro de reclamações
  equipa/                 # contactos e onboarding
  geral/                  # glossário, prazos e obrigações recorrentes
  seguranca/              # segurança da informação
```
<sub>* RGPD tem pasta própria (`rgpd/`) mas aparece no menu dentro do separador Compliance.</sub>

## Adicionar uma página nova

1. Criar um novo ficheiro `.md` dentro da pasta correspondente em `docs/`
2. Adicionar uma linha em `mkdocs.yml`, dentro de `nav:`, a apontar para esse ficheiro
3. `git add . && git commit -m "Nova página" && git push`

## Nota de segurança

O conteúdo da Política de Compliance deve ser revisto pelo Responsável de Compliance antes de ser tratado
como a versão oficial em uso.
