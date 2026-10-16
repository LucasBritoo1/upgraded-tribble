# 🎮 Dashboard de Vendas — Xbox Game Pass

Dashboard interativo em **Excel** que analisa as vendas de assinaturas do **Xbox Game Pass** e dos complementos **EA Play Season Pass** e **Minecraft Season Pass**, usando tabelas dinâmicas, segmentação de dados e gráfico.

> **Período de cálculo:** 01/01/2024 a 31/12/2024

---

## 📌 Objetivo

Responder perguntas de negócio sobre o faturamento das assinaturas, transformando uma base de assinantes em um painel visual de fácil leitura.

## ❓ Perguntas de negócio

| # | Pergunta |
|---|----------|
| 1 | Qual o faturamento total de vendas de planos anuais (todas as assinaturas agregadas)? |
| 2 | Qual o faturamento total de vendas de planos anuais, separado por **com** e **sem** renovação automática? |
| 3 | Qual o total de vendas de assinaturas do **EA Play**? |
| 4 | Qual o total de vendas de assinaturas do **Minecraft Season Pass**? |

## 📂 Estrutura da planilha

O arquivo `Dashboard_de_Vendas_do_Xbox.xlsx` é organizado em 4 abas:

| Aba | Conteúdo |
|-----|----------|
| **Assets** | Paleta de cores (verdes do Xbox e cor de fundo), logos e ícones usados no visual do dashboard |
| **Bases** | Base de dados (`Tabela1`) com 295 assinantes |
| **Cálculos** | Tabelas dinâmicas e gráfico que respondem às perguntas de negócio |
| **Dashboard** | Painel final com indicadores (cards), gráfico e filtro |

## 🗃️ Base de dados

A tabela **Bases** contém 295 registros, com IDs de assinante de 3231 a 3525 e datas de início de 01/01/2024 a 16/12/2024.

| Coluna | Descrição |
|--------|-----------|
| Subscriber ID | Identificador do assinante |
| Name | Nome do assinante |
| Plan | Plano: `Core`, `Standard` ou `Ultimate` |
| Start Date | Data de início da assinatura |
| Auto Renewal | Renovação automática (`Yes` / `No`) |
| Subscription Price | Preço do plano (Core = 5, Standard = 10, Ultimate = 15) |
| Subscription Type | Periodicidade: `Monthly`, `Quarterly` ou `Annual` |
| EA Play Season Pass | Contratou o EA Play? (`Yes` / `No`) |
| EA Play Season Pass Price | Preço do EA Play (30 quando contratado) |
| Minecraft Season Pass | Contratou o Minecraft Season Pass? (`Yes` / `No`) |
| Minecraft Season Pass Price | Preço do Minecraft Season Pass (20 quando contratado) |
| Coupon Value | Valor do cupom de desconto |
| Total Value | Valor total da assinatura |

**Regra do valor total:**

```
Total Value = Subscription Price + EA Play Season Pass Price + Minecraft Season Pass Price − Coupon Value
```

### Distribuição da base

| Plano | Assinantes | Periodicidade | Assinantes |
|-------|-----------:|---------------|-----------:|
| Core | 101 | Monthly | 139 |
| Standard | 96 | Quarterly | 85 |
| Ultimate | 98 | Annual | 71 |

## 🧮 Análises (aba Cálculos)

Três tabelas dinâmicas alimentadas pela `Tabela1`, todas conectadas à mesma segmentação de dados:

- **`tbl_annual_total`**: soma de *Total Value* por *Auto Renewal* (Perguntas 1 e 2)
- **`tbl_easeasonpass_total`**: soma de *EA Play Season Pass* por *Plan* (Pergunta 3)
- **`Tabela dinâmica9`**: soma de *Minecraft Season Pass Price* por *Plan* (Pergunta 4)

Há também um gráfico de barras por plano, usado no dashboard.

## 📊 Dashboard

O painel apresenta:

- **Cards de indicadores:** total de assinaturas EA Play Season Pass, total de assinaturas Minecraft Season Pass e total de assinaturas Xbox Game Pass
- **Gráfico de barras** por plano
- **Segmentação de dados (slicer) por *Subscription Type*:** filtra todas as tabelas dinâmicas ao mesmo tempo (Monthly, Quarterly ou Annual)
- **Cabeçalho** com título, saudação e data de atualização

### Resultados com o filtro `Monthly`

| Indicador | Valor |
|-----------|------:|
| Faturamento total (Monthly) | R$ 3.571,00 |
| ↳ Sem renovação automática | R$ 2.824,00 |
| ↳ Com renovação automática | R$ 747,00 |
| EA Play Season Pass | R$ 1.350,00 |
| Minecraft Season Pass | R$ 1.800,00 |

### Resultados por periodicidade

| Periodicidade | Total Value | EA Play | Minecraft |
|---------------|------------:|--------:|----------:|
| Annual | R$ 1.754,00 | R$ 600,00 | R$ 940,00 |
| Monthly | R$ 3.571,00 | R$ 1.350,00 | R$ 1.800,00 |
| Quarterly | R$ 2.308,00 | R$ 990,00 | R$ 1.140,00 |
| **Total geral** | **R$ 7.633,00** | **R$ 2.940,00** | **R$ 3.880,00** |

> Os valores do dashboard mudam conforme a opção escolhida no filtro de *Subscription Type*.

## 🛠️ Ferramentas e recursos utilizados

- Microsoft Excel
- Tabelas do Excel (`Tabela1`)
- Tabelas dinâmicas
- Segmentação de dados (slicer)
- Gráfico de barras
- Formas, imagens e ícones para o layout do dashboard

## ▶️ Como usar

1. Abra o arquivo `Dashboard_de_Vendas_do_Xbox.xlsx` no Excel (versão 2010 ou superior, por causa da segmentação de dados).
2. Vá até a aba **Dashboard**.
3. Use o filtro **Subscription Type** para alternar entre Monthly, Quarterly e Annual.
4. Para atualizar os dados, edite a aba **Bases**, depois vá em **Dados > Atualizar Tudo** para recalcular as tabelas dinâmicas.

## 👤 Autor

**Lucas Pereira Alves de Brito**
Técnico em Eletroeletrônica | Desenvolvimento Front-End
