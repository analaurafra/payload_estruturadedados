# Contract Template — Digital Account Opening (Company)

**Fintech partner:** `{{fintechNome}}`  
**Proposal:** `{{idProposta}}`  
**Date:** `{{dataCriacao}}`

---

## 1. Qualification of the Company

By this instrument, the company **`{{dadosEmpresa.razaoSocialEmpre}}`**, registered under CNPJ **`{{dadosEmpresa.cnpjEmpresa}}`**, requests the opening of an account in the modality **`{{dadosEmpresa.tipoContaEmpresa}}`**.

---

## 2. Partners and Legal Representatives

The following partners/representatives are qualified and authorized to act for the company:

`{{#each sociosRepresentantes}}`

- **Name:** `{{nomeRepresentante}}`  
  **CPF:** `{{cpfRepresentante}}`  
  **Role / Profession:** `{{cargoRepresentante}}`  
  **Share:** `{{porcentagemSociedadeRep}}%`

`{{/each}}`

---

## Conditional: Joint Signature Requirement

`{{#if legendasCondicional.necessitaAssinaturaConjunta}}`

> ⚠️ **Restrictive clause for movement:**  
> Since `necessitaAssinaturaConjunta` is `{{legendasCondicional.necessitaAssinaturaConjunta}}`, movements and approval of financial transactions on this PJ account require joint signature and mutual consent of more than one qualified managing partner listed in section 2.

`{{/if}}`

---

## 3. Fees and Contracted Limits

The client acknowledges the contracted service package below:

| Package | Service | Unit Cost | Daily Limit |
|---|---:|---:|---:|
`{{#each tarifasELimitesContratados}}`
| `{{tipoPacote}}` | `{{servico}}` | `{{custo}}` | `{{#if limiteDiario}}R$ {{limiteDiario}}{{else}}No set limit{{/if}}` |
`{{/each}}`

---

*Converted from the original HTML Handlebars template to Markdown for documentation and review.*
