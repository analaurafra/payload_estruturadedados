# Template: Model Contract — Fiduciary Alienation Guarantee

This file is a Markdown conversion of the HTML Handlebars template.

---

## Basic Fields

- **Reference date:** `{{dataAtual}}`
- **Operation value:** R$ `{{valorEmprestimo}}`

---

## Creditor

- **Credor Fiduciário:** `{{credorFiduciario.nomeCredorFiduciario}}` — CNPJ: `{{credorFiduciario.cnpjCredorFiduciario}}`

## Debtor (inside creditor object)

- **Devedor Principal:** `{{credorFiduciario.dadosDevedor.razaoSocialDevedor}}` — CNPJ: `{{credorFiduciario.dadosDevedor.cnpjDevedor}}`
- **Interveniente Fiduciante:** `{{credorFiduciario.dadosDevedor.dadosFiducianteGarantidor}}`

## Legal Representatives (repeats for each item in `credorFiduciario.dadosRepresentates`)

- `{{#each credorFiduciario.dadosRepresentates}}`
  - `{{nomeRepresentante}}` (CPF: `{{cpfRepresentante}}`) — Cargo: `{{cargoRepresentante}}`
  `{{/each}}`

---

## Clause Four — Assets Alienated as Guarantee

In guarantee of the debt, the following assets registered in the system are fiduciarily alienated:

**Table (repeat for each item in `credorFiduciario.dadosBens`)**

- **Type:** `{{tipoDoBem}}`
- **Description:** `{{descricaoDoBem}}`
- **Registration (Matrícula):** `{{matriculadoBem}}`
- **Registry Office (Cartório):** `{{nomeCartorioBem}}`
- **Appraisal / Value:** R$ `{{valorAvaliacaoBem}}`

---

## Conditional: Default and Delay

`{{#if credorFiduciario.legendaCondicional.credorInadimplente}}`

- **Clause Five — Default and Delay**  
  The debtor is in default for **`{{diasEmAtraso}} days`**.

  `{{#if credorFiduciario.legendaCondicional.notificacaoDeInadimplencia}}`

  - **Paragraph (Extrajudicial Execution):** The creditor is authorized to notify the guarantor `{{credorFiduciario.dadosDevedor.dadosFiducianteGarantidor}}` through the registry office `{{credorFiduciario.dadosBens.0.nomeCartorioBem}}` for consolidation of the property of the assets listed above.

  `{{/if}}`

`{{/if}}`

---

## Tools used

- https://jsonlint.com/
- https://jsoncrack.com/editor
- https://handlebarsjs.com/examples

---

*Converted from HTML template to Markdown for documentation and easier review.*