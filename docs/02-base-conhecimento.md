# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Para que serve no FinBot |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores, ou seja, dar continuidade de forma mais eficiente |
| `perfil_investidor.json` | JSON | Personalizar as explicações sobre as dúvidas e necessidades de aprendizado do cliente |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponíveis para que eles possam ser ensinados ao cliente |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

O produto Fundo Imobiliário (FII) foi adicionado em substituição ao Fundo Multimercado, sem retirar nenhum outro produto. 
Agora os produtos apresentados aqui são do meu conhecimento.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

```python
import pandas as pd
import json

# --- Lendo arquivos CSV ---
# transações financeiras
transacoes = pd.read_csv("transacoes.csv", encoding="utf-8")
print("Transações:")
print(transacoes.head(), "\n")

# histórico de atendimento
historico_atendimento = pd.read_csv("historico_atendimento.csv", encoding="utf-8")
print("Histórico de Atendimento:")
print(historico_atendimento.head(), "\n")

# --- Lendo arquivos JSON ---
# perfil do investidor
with open("perfil_investidor.json", "r", encoding="utf-8") as f:
    perfil_investidor = json.load(f)
print("Perfil do Investidor:")
print(perfil_investidor, "\n")

# produtos financeiros
with open("produtos_financeiros.json", "r", encoding="utf-8") as f:
    produtos_financeiros = json.load(f)
print("Produtos Financeiros:")
print(produtos_financeiros, "\n")

```
### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

[Sua descrição aqui]

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
