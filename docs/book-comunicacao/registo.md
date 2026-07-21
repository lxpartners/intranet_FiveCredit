# Book de Comunicação — Registo

??? note "01 — Autenticação de Email no Processo de Registo"
    **Código:** `SIGNUP-EMAIL-VALIDATION`

    **Assunto:** Five Credit – Criação de conta e validação de email.

    **Corpo:**
    ```
    Olá,

    Bem-Vindo ao Portal Five Credit!

    Recebemos um pedido de registo com este email. Por motivos de segurança é importante confirmar a sua identidade.

    Para continuar o processo de registo, por favor, insira o seguinte Código, no campo indicado na Plataforma.

    {{validationcode}}

    Muito obrigado.
    Equipa Five Credit
    ```

??? note "02 — Confirmação de Registo"
    **Código:** `SIGNUP-FINISHED`

    **Assunto:** Five Credit – Confirmação de registo de conta

    **Corpo:**
    ```
    Exmo(a) {USER-NAME},

    Damos-lhe as boas-vindas à plataforma da Five Credit. O seu registo foi concluído com sucesso!

    Para efetuar a sua candidatura a um financiamento Five Credit, entre através do link disponibilizado no email.

    LER COM ATENÇÃO:

    Requisitos
    O produto de financiamento Five Credit destina-se a PMEs com mais de 3 anos de atividade e 100.000 euros de faturação.

    Para efetuar a candidatura vai precisar de:
    — Código de acesso à Certidão do Registo Comercial (CRC) da sua empresa
    — Informar o seu Contabilista Certificado de que irá receber um email com um link, para aceder à plataforma e carregar informação financeira necessária à análise do financiamento.

    Se, após uma validação inicial passar à fase seguinte, ser-lhe-á solicitado o upload de informação dos sites: Banco de Portugal, Segurança Social, Autoridade Tributária.

    Muito obrigado e até breve,
    Equipa Five Credit
    ```
