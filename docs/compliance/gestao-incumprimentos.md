# Gestão de Incumprimentos

Processo a seguir desde a primeira falha do débito direto de uma prestação até ao eventual
encaminhamento do processo para o Departamento de Contencioso.

O fluxo tem duas fases:

1. **Cobrança amigável** — falha do débito direto, avisos por email e interpelação por transferência
   bancária, ainda dentro do mesmo mês da falha.
2. **Gestão de incumprimentos** — a partir do momento em que a dívida não é regularizada depois do
   3º email, o processo passa a ser organizado por número de prestações em falta, com cartas registadas,
   preenchimento de livrança e, no limite, encaminhamento para contencioso.

## Calendário de SLAs

| Prazo | Situação | Ação |
|---|---|---|
| D | 1ª tentativa de débito direto falha (insuficiência de fundos — código AM04) | Sistema regista a falha |
| D+1 | O pagamento não ocorreu | É definida uma nova data de pagamento |
| D+2/3 | — | [Email 1](#email-1-aviso-de-falha-de-debito-direto-d23) — aviso de falha ao cliente |
| D+15 | O pagamento continua em falta (2ª falha do mês) | [Email 2](#email-2-aviso-de-mora-2a-falha-de-debito-no-mes-d15) — aviso de mora, com pedido de comprovativo |
| — | Cliente não regulariza | [Email 3](#email-3-interpelacao-para-pagamento-por-transferencia-bancaria) — interpelação com IBAN em anexo, pagamento no próprio dia |
| D+30 | 1 prestação em falta e 1 prestação em atraso | [3 prestações em falta](#3-prestacoes-em-falta-d30) — 1ª carta de interpelação |
| D+60 | 2 prestações em falta e 1 prestação em atraso | [Aviso aos 60 dias](#aviso-aos-60-dias-antes-do-encaminhamento-para-contencioso-d60) — último email antes do contencioso |
| D+90 | Incumprimento definitivo | [4 prestações em atraso](#4-prestacoes-em-atraso-d90) — nova carta com preenchimento da livrança; processo de contencioso gerido pela Algebra |

## 1ª falha de débito direto (D)

Motivo: insuficiência de fundos — código AM04. A prestação mensal do Plano de Financiamento não é
cobrada por débito direto. O sistema regista a falha e desencadeia o envio automático do primeiro aviso
ao cliente. Em D+1 é definida uma nova data de pagamento para se proceder ao débito do montante em
atraso.

### Email 1 — Aviso de Falha de Débito Direto (D+2/3)

Destinatário: cliente · Canal: email

??? note "Modelo — 1ª falha do mês"
    **Assunto:** *(preencher)*

    ```
    Exmos. Sr/Sra,

    Informamos que a Five Credit não conseguiu debitar, a prestação n.º x do seu Plano de Financiamento, no valor de € xxx,xx, por insuficiência de fundos (AM04).

    No próximo dia xx efetuaremos uma nova tentativa de débito do valor: € xxx,xx.

    Provisione a conta bancária com o IBAN PTxxx e evite o incumprimento do seu contrato de financiamento e custos adicionais.

    Alertamos que, se o incumprimento persistir, será efetuada comunicação à Central de Responsabilidades de Crédito do Banco de Portugal, nos termos da legislação aplicável, com as inerentes consequências.

    Relembramos que, o seu Plano de Financiamento e respetivas amortizações, poderão ser consultados, a todo o tempo, na Plataforma CreditScore. Em caso de dúvida, contacte-nos através dos canais disponíveis.

    Muito obrigado.
    Equipa Five Credit
    ```

## 2ª falha de débito direto (mesmo mês)

Motivo: insuficiência de fundos — código AM04. Na data indicada no Email 1, a nova tentativa de cobrança
volta a falhar — é a segunda falha da mesma prestação, no mesmo mês.

### Email 2 — Aviso de Mora — 2ª Falha de Débito no Mês (D+15)

Destinatário: cliente · Canal: email · **Pede-se o envio do comprovativo de pagamento**

??? note "Modelo — 2ª falha do mês"
    **Assunto:** *(preencher)*

    ```
    Exmo. Sr/Sra,

    Informamos que, pela segunda vez no presente mês, não foi possível proceder ao débito da prestação n.º x do seu Plano de Financiamento, no valor de €xxx,xx, por insuficiência de fundos (código AM04).

    Anexamos abaixo o IBAN para que possa proceder à transferência do montante em dívida e solicitamos, por favor, o envio do respetivo comprovativo de pagamento.

    IMPORTANTE: Alertamos que a falta de pagamento no prazo estipulado configura situação de mora, dando lugar à aplicação de juros de mora e à cobrança de comissão de recuperação de valores em dívida, nos termos legais.

    Adicionalmente, informamos que será efetuada comunicação à Central de Responsabilidades de Crédito do Banco de Portugal, nos termos da legislação aplicável, com as consequentes implicações para a sua situação creditícia.

    Permanecemos ao dispor para quaisquer esclarecimentos adicionais.

    Relembramos que, o seu Plano de Financiamento e respetivas amortizações, poderão ser consultados, a todo o tempo, na Plataforma CreditScore. Em caso de dúvida, contacte-nos através dos canais disponíveis.

    Com os melhores cumprimentos,
    Equipa Five Credit
    ```

    📎 Anexo: IBAN para transferência bancária (ver [comprovativo de NIB / IBAN e SWIFT-BIC](#comprovativo-de-nib-iban-e-swift-bic))

## Cliente não regulariza o valor em dívida até à data estipulada

Os montantes em falta continuam por liquidar depois do prazo indicado no Email 2, mesmo tendo havido
contactos anteriores por telefone e por email.

### Email 3 — Interpelação para Pagamento por Transferência Bancária

Destinatário: cliente · Prazo: **pagamento no próprio dia** · Conta de origem: titulada pela empresa

??? note "Modelo — interpelação com anexo IBAN"
    **Assunto:** *(preencher)*

    ```
    Exmos. Senhores,

    Não obstante os nossos anteriores contactos — por telefone e por email — verificamos que a prestação n.º x, se mantém em atraso desde o dia x do corrente mês.

    Informamos que, deverão proceder à liquidação da prestação em falta, no montante total de xxx,xx€, através de transferência bancária, durante o dia de hoje, para o IBAN indicado no documento em anexo.

    Relembramos que o pagamento deverá ser efetuado a partir de uma conta titulada pela empresa, devendo o respetivo comprovativo ser enviado para este endereço de email logo após a operação.

    Alertamos ainda que, na ausência de pagamento dentro do prazo indicado, a situação será comunicada à Central de Responsabilidades de Crédito do Banco de Portugal, com o consequente impacto negativo na vossa situação creditícia.

    Agradecemos a vossa atenção e colaboração no sentido de evitar consequências adicionais.

    Com os melhores cumprimentos,
    Equipa Five Credit
    ```

    📎 Anexo obrigatório: comprovativo de NIB / IBAN e SWIFT-BIC — ver secção abaixo.

#### Comprovativo de NIB / IBAN e SWIFT-BIC

Documento a anexar ao Email 3, com o extrato de conta do banco (Bankinter) titulada pela Five Credit:

| Campo | Valor |
|---|---|
| Nome da conta | Sub Fundo 1 PME Restart |
| NIB | 0269 0510 0020 5023 1742 4 |
| IBAN | PT50 0269 0510 0020 5023 1742 4 |
| BIC / SWIFT | BKBKPTPLXXX |

!!! warning "Confirmar o extrato antes de anexar"
    Gerar sempre um extrato de NIB/IBAN/BIC atualizado junto do banco antes de anexar ao Email 3 — não
    reutilizar prints antigos, para garantir que os dados da conta estão corretos.

## Falha na liquidação da dívida após o Email 3

O processo transita do circuito de cobrança amigável para o módulo de **Gestão de Incumprimentos**,
organizado por número de prestações em falta.

## 3 prestações em falta (D+30)

**1ª Carta de Interpelação** — Canal: correio registado com aviso de receção + email

1. Enviar a **1ª carta de interpelação**, por correio registado com aviso de receção, com o pedido de
   liquidação dos valores em falta antes da nova prestação (4ª prestação)
2. No mesmo momento do envio dessa carta, enviar também um **email para `legal@fivecredit.pt`** ao
   cliente com:
    - `five@fivecredit.pt` e `legal@fivecredit.pt` em CC
3. Enviar email para **`OfficeSupport@algebracapital.pt`**, usando o template **"Email Interpelação Office
   Support"** (ver [Book de Comunicação — Procedimentos](../book-comunicacao/procedimentos.md))
4. Entregar a carta física junto da equipa de Office Support, no 5º andar, com o carimbo da Circle Capital
   SGOIC, S.A.

## Aviso aos 60 dias, antes do encaminhamento para contencioso (D+60)

Se o incumprimento se mantiver ao fim de **60 dias** desde o seu início, é enviado ao cliente um último
email de aviso, antes de o processo ser encaminhado para o Departamento de Contencioso:

??? note "Modelo — aviso aos 60 dias"
    **Assunto:** *(preencher)*

    ```
    Exmo. Senhor/Senhora,

    Na sequência das nossas comunicações anteriores e do plano de regularização acordado, verificámos que, para além da prestação com vencimento em xx/xx/xxxx, no montante de xxx,xx €, relativa à prestação de março, se encontra igualmente em falta a prestação com vencimento em xx/xx/xxxx, no montante de xxx,xx €, relativa à prestação de (mês em causa).

    Mais uma vez chamamos a atenção para a necessidade de cumprimento rigoroso do plano definido. A manutenção destas prestações em atraso poderá implicar, sem nova comunicação, o encaminhamento imediato do processo para o nosso Departamento de Contencioso, com o consequente desencadeamento dos competentes procedimentos legais para cobrança judicial da dívida, nos termos já anteriormente transmitidos.

    Solicitamos, assim, que proceda à regularização integral das prestações em falta com a máxima urgência e que nos remeta o respetivo comprovativo de pagamento, bem como os comprovativos das prestações subsequentes logo que liquidadas, de modo a permitir a atualização da sua situação em sistema.

    Ficamos a aguardar a sua resposta com a maior brevidade.

    Com os melhores cumprimentos, Equipa Five Credit
    ```

## 4 prestações em atraso (D+90)

**Nova Carta de Interpelação, com preenchimento da Livrança**

- Enviar **nova carta de interpelação** — desta vez já com o **preenchimento da livrança** associada ao
  contrato.

## Desfecho — encaminhamento do processo

Na ausência de regularização, o processo é encaminhado para o **Departamento Financeiro** e, se
aplicável, para o **Departamento de Contencioso** (gerido pela Algebra), com o desencadeamento dos
procedimentos legais para cobrança judicial da dívida e a correspondente comunicação à **Central de
Responsabilidades de Crédito do Banco de Portugal**.

!!! warning "Confirmar antes de tornar oficial"
    Este fluxo segue o documento interno *Fluxo de Comunicação em Situação de Incumprimento* (25 de
    agosto de 2026, uso interno). Confirmar sempre com o Responsável de Compliance os valores exatos
    (datas, montantes, número de prestação, IBAN) antes de enviar qualquer uma destas comunicações,
    substituindo os campos com `x`/`xxx,xx` pelos dados reais de cada processo.
