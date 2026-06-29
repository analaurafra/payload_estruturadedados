# Protótipo de Contrato: Alienação Fiduciária (Completo - PF, PJ e Cônjuge)

**Instrumento:** Instrumento Particular de Constituição de Garantia Fiduciária

---

## Dados do Contrato

- **Contrato nº:** `dadosContrato.idContrato`
- **Emissão:** `dadosContrato.dataEmissaoContrato`
- **Valor total do crédito:** R$ `dadosContrato.valorEmprestimo`

## Devedor Principal

- **Nome / Razão Social:** `dadosDevedorPrincipal.razaoSocialDevedor`
- **CNPJ:** `dadosDevedorPrincipal.cnpjDevedor`
- **Endereço:** `dadosDevedorPrincipal.enderecoLogradouroDevedor`, nº `dadosDevedorPrincipal.numeroDevedor`, `dadosDevedorPrincipal.complementoDevedor`
- **Bairro / Cidade / UF / CEP:** `dadosDevedorPrincipal.bairroDevedor` - `dadosDevedorPrincipal.cidadeDevedor`/`dadosDevedorPrincipal.ufDevedor`, CEP: `dadosDevedorPrincipal.cepDevedor`

---

## Fiduciantes Garantidores (repetir para cada item do array `dadosFiducianteGarantidor`)

### Regra condicional: tipo de pessoa (PF vs PJ)

- Se `tipoPessoa == "PJ"`:
  - **Fiduciante (Pessoa Jurídica):** `razaoSocialFiduciantePJ`
  - **CNPJ:** `cnpjFiduciantePJ`
  - **Endereço:** `enderecoFiduciantePJ`, nº `numeroFiduciantePJ`, Bairro `bairroFiduciantePJ`, `cidadeFiduciantePJ`/`ufFiduciantePJ`
  - **Representante(s):** `nomeRepresentantePJ` — Nacionalidade: `nacionalidadeRepresentantePJ`, Profissão: `profissaoRepresentantePJ`, RG: `rgRepresentantePJ`, CPF: `cpfRepresentantePJ`

- Se `tipoPessoa == "PF"`:
  - **Fiduciante (Pessoa Física):** `nomeFiducianteGarantidor`
  - **Nacionalidade / Profissão:** `nacionalidadeFiducianteGarantidor` / `profissaoFiducianteGarantidor`
  - **Documentos:** RG `rgFiducianteGarantidor`, CPF `cpfFiducianteGarantidor`
  - **Endereço:** `enderecoFiducianteGarantidor`, nº `numeroFiducianteGarantidor`, Bairro `bairroFiducianteGarantidor`, `cidadeFiducianteGarantidor`/`ufFiducianteGarantidor`
  - **Estado Civil:** `estadoCivilFiducianteGarantidor`
  - **Regime de Bens (se houver):** `regimeDeBensFiducianteGarantidor`

### Cônjuge Anuente (Regra de negócio)

- Se `legendaCondicional.assinaturaConjuge == true` e `estadoCivilFiducianteGarantidor` é "Casada" ou "Casado", incluir qualificação do cônjuge:
  - **Nome:** `dadosConjuge.nomeConjuge`
  - **RG / Órgão emissor:** `dadosConjuge.rgConjuge` / `dadosConjuge.orgaoEmissorConjuge`
  - **CPF:** `dadosConjuge.cpfConjuge`

#### Direitos e deveres do cônjuge conforme o regime de bens

- Se `regimeDeBensFiducianteGarantidor` for "Comunhão de Bens" ou "Comunhão Parcial":
  - Parágrafo Primeiro: dever de conservação e solidariedade; responsabilidade solidária com o Fiduciante.

- Se `regimeDeBensFiducianteGarantidor` for "Participação Final nos Aqüestos":
  - Parágrafo Segundo: direito de preferência na excussão (remição ou aquisição da quota-parte).

---

## Bens Alienados em Garantia (repetir para cada item do array `dadosDosBens`)

- **Tipo do bem:** `tipodoBem`
- **Descrição legal:** `descricaoDoBem`
- **Localização:** `logradouroDoBem`, nº `numeroDoBem` - `cidadeDoBem`/`ufDoBem`, CEP: `cepDoBem`
- **Registro imobiliário:** Matrícula nº `matriculaDoBem` perante o `nomeDoCartorioDoBem` da Comarca de `comarcaDoBem`

---

## Credor Fiduciário

- **Nome:** `dadosCredorFiduciario.nomeCredorFiduciario`

---

## Condições de Inadimplência e Consolidação

### Regra condicional: notificação em cartório

- Se `legendaCondicional.notificacaoCartorioAtiva == true`, incluir a cláusula sobre inadimplência e consolidação:

> CLÁUSULA SEGUNDA - DA INADIMPLÊNCIA E CONSOLIDAÇÃO
>
> Ocorrendo a impontualidade no pagamento de qualquer parcela do empréstimo aqui pactuado, fica o Credor Fiduciário expressamente autorizado a acionar o competente `nomeDoCartorioDoBem` (do primeiro item do array `dadosDosBens`) para intimar os devedores, fiduciantes (e seus respectivos cônjuges anuentes ou representantes legais) a purgarem a mora, sob pena de consolidação da propriedade do imóvel em nome do banco.

### Exemplo de placeholders e dicas de modelagem

- Dica: no array `dadosFiducianteGarantidor` inclua um campo discriminador `tipoPessoa` com valores `PF` ou `PJ`.
- Se `tipoPessoa == "PJ"`, envie os campos da empresa e do representante; se `PF`, envie os campos pessoais.

---

*Arquivo gerado a partir do texto original — formatado para uso como guia de template/README ou para conversão em Handlebars/templating.*
