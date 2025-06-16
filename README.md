<h1 align="center">💼 Projeto Excel – Financial Empire</h1>

## 📄 Descrição

Este trabalho foi elaborado como resposta a um desafio voltado à aplicação prática de fórmulas e recursos de formatação condicional no Excel. A proposta central consistiu em analisar diferentes cenários e, com base no prazo de investimento informado, determinar automaticamente o perfil do investidor correspondente.

---

## 📊 Estrutura da Planilha

A planilha contém uma tabela com projeções de patrimônio e rendimento para diversos horizontes de tempo. O usuário informa o número de anos, e a planilha retorna o valor de Patrimônio Acumulado e o Rendimento.

### 🧾 Exemplo de dados:

| Cenários             | Patrimônio Acumulado | Rendimento    |
|----------------------|----------------------|----------------|
| Quanto em 2 anos?  | R$ 17.637,09           | R$ 114,64      |
| Quanto em 5 anos?  | R$ 53.947,13           | R$ 350,66      |
| Quanto em 10 anos? | R$ 154.906,68          | R$ 1.006,89    |
| Quanto em 20 anos? | R$ 697.442,34          | R$ 4.533,38    |
| Quanto em 30 anos? | R$ 2.597.585,99         | R$ 16.884,31    |

---

## 🔍 Recomendação de Investimentos
Com base no perfil de investidor identificado (Conservador, Moderado ou Agressivo), a planilha utiliza a função PROCV (VLOOKUP) para buscar automaticamente uma alocação sugerida de investimentos entre diferentes tipos de ativos.

Essas sugestões são exibidas em porcentagens de distribuição recomendada para cada classe de investimento, conforme o perfil detectado.

## 🧠 Lógica aplicada
Ao classificar o perfil (célula C32, por exemplo), a planilha procura na tabela de perfis e retorna as alocações recomendadas para as seguintes categorias:

- **PAPEL** – Renda Fixa e Títulos Públicos
- **TIJOLO** – Fundos Imobiliários (FIIs) de tijolo
- **HÍBRIDOS** – Fundos mistos (renda fixa + variável)
- **FOFs** – Fundos de Fundos (ex: FII de FII)
- **DESENVOLVIMENTO** – Fundos com foco em incorporação e valorização futura
- **HOTELARIAS** – Segmento específico de fundos ligados a empreendimentos hoteleiros

A planilha realiza automaticamente o **desmembramento do valor informado para investimento mensal**, sugerindo **quanto investir em cada categoria de FII**, conforme o perfil selecionado.

A função `VLOOKUP` (`PROCV`) é utilizada para localizar a **porcentagem recomendada de alocação** em cada tipo de FII com base em:

- O **perfil selecionado** (ex: "Moderado")
- O **tipo de FII** (ex: PAPEL, TIJOLO, etc.)

### 🧾 Exemplo prático

| Tipo de FII       | Percentual Sugerido | Valor a Investir |
|-------------------|---------------------|------------------|
| PAPEL             | 30%                 | R$ 195,00        |
| TIJOLO            | 35%                 | R$ 227,50        |
| HÍBRIDOS          | 10%                 | R$ 65,00         |
| FOFs              | 5%                  | R$ 32,50         |
| DESENVOLVIMENTO   | 10%                 | R$ 65,00         |
| HOTELARIAS        | 10%                 | R$ 65,00         |
| **Total**         | **100%**            | **R$ 650,00**    |

### 🧩 Fórmula usada

```excel
=PROCV($C$32&"-"&B36;TabelaPerfis!$A:$D;4;FALSO)
```

> A fórmula busca uma combinação de perfil + tipo (ex: “Moderado-PAPEL”) dentro da **tabela auxiliar “TabelaPerfis”**, e retorna o percentual correspondente.  
> Esse percentual é multiplicado pelo valor informado para calcular automaticamente o valor ideal para aplicar em cada categoria.

---

## 🎯 Objetivo da Planilha

- Automatizar a **classificação do perfil de investidor** com base no tempo de investimento
- Exibir automaticamente os **cenários projetados de patrimônio e dividendos**
- Sugerir alocação de recursos conforme o perfil de risco
- Aplicar conceitos de lógica, busca dinâmica e visualização clara de dados

---

## 🛠 Tecnologias e Funções Utilizadas

- **Microsoft Excel**
- **Fórmulas**:
  - `SE`
  - `PROCV (VLOOKUP)`
  - Multiplicações diretas (`percentual × valor total`)
- **Formatação Condicional**
- Organização estética de dados

---

## 📌 Observações

Este projeto tem fins exclusivamente educacionais. Os dados de rendimento e patrimônio foram estimados apenas para ilustrar o uso das ferramentas do Excel.  
Para uso real em finanças, recomenda-se consultar especialistas certificados.
