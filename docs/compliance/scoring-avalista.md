# Scoring do Avalista

Processo para calcular o scoring de um avalista, através da ferramenta interna de scoring.

## Endpoint

```
https://ojhgxowjgk.execute-api.eu-west-1.amazonaws.com/dev/docs#/scoring/score_individual_score_individual_post
```

## Campos a enviar

| Campo | Descrição | Exemplo |
|---|---|---|
| `nif` | NIF do avalista | `"000000000"` |
| `age` | Idade do avalista | `47` |
| `rendimento_global` | Rendimento global, segundo a declaração de IRS | `11060` |
| `valor_patrimonial` | Valor patrimonial indicado na evidência de património | `0` |
| `loan_amount` | Valor do empréstimo | `25000` |
| `five_existing_guarantee` | Remanescente a pagar, se já existir um empréstimo a decorrer | `25000` |
| `name` | Nome do avalista | `"Nome Exemplo"` |

## Exemplo de pedido

```json
{
  "nif": "000000000",
  "age": 47,
  "rendimento_global": 11060,
  "valor_patrimonial": 0,
  "loan_amount": 25000,
  "five_existing_guarantee": 25000,
  "name": "Nome Exemplo"
}
```

!!! info "Exemplo com dados fictícios"
    O NIF e o nome acima foram substituídos por valores fictícios — não usar dados reais de clientes ou
    avalistas em documentação interna, para respeitar a [Política de Proteção de Dados (RGPD)](../rgpd/protecao-dados.md).
