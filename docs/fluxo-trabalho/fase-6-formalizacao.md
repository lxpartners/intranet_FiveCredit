# Fase 6 — Formalização

Intervenientes possíveis: **Empresa**, **Compliance**, **Board**, **Suporte**, **Departamento
Financeiro**

## 18 — Informação Contratual & Formalização
*Dados pré-contratuais*

O candidato confirma os dados dos Avalistas e Representantes da empresa no questionário pré-contratual,
bem como a conta bancária da Empresa onde irá ser creditado o financiamento e debitadas as prestações.

- Clica no link que recebeu no e-mail
- Confirma todos os dados anteriormente colocados
- Submete
- Sai

**Responsável:** Empresa · **Sistema:** Creditscore · **Email(s):** Email 20

## 18.1 — Backoffice — Formalização do contrato
*Compliance e Board*

O Compliance irá analisar todos os detalhes e aprovar o KYC. Após verificação, o Board aprova a
disponibilização do contrato na plataforma para consulta do Candidato através do processo de
formalização.

- Confirmar os dados e guardar
- Após tudo confirmado, clicar em "Submeter"
- Abre automaticamente o Contrato em formato PDF
- Perfil Board (2 de 3): aceitação ou rejeição do contrato
- Após validação, o contrato fica disponível na plataforma para consulta do cliente

**Responsável:** Compliance, Board · **Sistema:** Creditscore · **Email(s):** Email 21

## 19 — Download e Upload do Contrato
*Assinatura e entrega*

O contrato fica disponível na plataforma para consulta e/ou download pelo cliente, que irá receber email
para efeitos de agendamento de assinatura do contrato. Depois de toda a documentação assinada, o
Departamento de Compliance revê a conformidade da documentação, digitaliza e envia ao cliente que deverá
fazer upload na plataforma de forma a finalizar o processo e despoletar o envio dos fundos.

!!! note "Agendamento do contrato"
    Para efeitos da formalização, o representante da empresa deverá fazer-se acompanhar de:

    - Documento(s) de identificação (passaporte, conforme indicado no contrato)
    - Carimbo da Empresa (caso este exista), para efeitos de assinatura do contrato e subscrição da
      livrança
    - Fotocópia certificada da ata de aprovação da celebração do financiamento garantido por livrança e
      comprovativa dos poderes de representação (ou, alternativamente, o livro de atas para efeitos de
      consulta)
    - Se aplicável, original ou fotocópia certificada da procuração comprovativa dos poderes de
      representação

- Upload do Contrato, da Autorização de Débito Direto e da Livrança
- Formato PDF
- Clicar em "Submeter"

**Responsável:** Empresa, Compliance · **Sistema:** Creditscore · **Email(s):** Email

## 19.1 — Backoffice — Download e Upload do Contrato
*Aprovação final e instrução de transferência*

Após o carregamento pela Empresa da documentação na plataforma, o Departamento de Compliance verifica a
sua conformidade e solicita por email ao Departamento Financeiro que prossiga com a transferência.
Simultaneamente, é dada a validação pelo Suporte na plataforma, e a candidatura passa ao estado
"Completo".

- Aceder à candidatura
- Selecionar "Aprovar"
- Confirmar aprovação
- Enviar email de `compliance@circlecapital.pt` para o Departamento Financeiro, com o Board em CC,
  detalhando o montante a creditar e os dados do beneficiário:

    - Montante de Crédito
    - Comissão Única
    - I.S. Comissão Única
    - I.S. Concessão de Crédito
    - Nome do beneficiário
    - NIF
    - IBAN a Creditar
    - Banco do Beneficiário
    - Data Valor Débito
    - Data Valor Crédito
    - Descritivo no beneficiário (n.º do contrato, ex.: FIVE01-111222)

- O Departamento Financeiro inicia a transferência

**Responsável:** Compliance, Suporte, Departamento Financeiro · **Sistema:** Creditscore ·
**Email(s):** Email

## 20 — Backoffice — Imposto de Selo
*Apuramento mensal*

Com base no Reporte Financeiro elaborado automaticamente a partir do Credit Cover e enviado mensalmente à
EY, o Departamento Financeiro:

- Considera as colunas "Stamp", "Stamp on Loan" e "Stamp on Fees"
- Apura o valor do I.S.
- Envia para o Contabilista Certificado (EY)
- Confirma internamente a informação enviada pelo Contabilista Certificado
- Submissão da DMIS pelo Contabilista Certificado
- Envio de guia para pagamento até ao dia 20 do mês + 1

**Responsável:** Suporte, Departamento Financeiro · **Sistema:** N.A. · **Email(s):** Email

## 21 — Backoffice — Faturação
*Reporte financeiro mensal*

Com base no Reporte Financeiro, o Departamento Financeiro:

- Reporte automático do credit cover enviado à EY
- EY envia para a Fivecredit
- Credit cover envia posteriormente as faturas para o respetivo cliente

**Responsável:** Suporte, Departamento Financeiro · **Sistema:** N.A. · **Email(s):** Email

## 22 — Backoffice — Débitos Diretos
*Marathon → Bankinter → Sibs*

Com o processo de formalização finalizado na plataforma, para os contratos "Performing":

- D − 5: a Marathon envia informação para o Bankinter
- Bankinter » Sibs
- A plataforma envia email automático à Empresa com informação da 1.ª tentativa de débito
- Em caso de insucesso da 1.ª tentativa: o credit cover calcula automaticamente os juros e envia a
  informação ao departamento responsável pelos Débitos Diretos (IT), para que seja feita uma nova
  tentativa de débito

!!! note "Atualização de processo"
    O pré-aviso deixou de ter dois momentos (D-15 e D-5), passando a existir apenas o envio a D-5. Foi
    também definido o procedimento para a 2.ª tentativa de débito: cálculo automático de juros através do
    credit cover, com envio ao departamento de IT.

**Responsável:** Suporte, Marathon · **Sistema:** N.A. · **Email(s):** Credit Cover

## 23 — Procedimento de Incumprimentos

Em caso de incumprimento no pagamento das prestações, é seguido um procedimento de acompanhamento e
notificação ao cliente antes de o processo ser escalado internamente — incluindo os avisos de falha de
débito direto, as interpelações por email e correio registado, e o eventual encaminhamento para o
Departamento de Contencioso.

O fluxo completo, com todos os modelos de email e o calendário de SLAs (D+1 a D+90), está documentado em
[Compliance → Gestão de Incumprimentos](../compliance/gestao-incumprimentos.md).

**Responsável:** Suporte, Departamento Financeiro · **Sistema:** Creditscore · **Email(s):** Email de
aviso de incumprimento (60 dias)
