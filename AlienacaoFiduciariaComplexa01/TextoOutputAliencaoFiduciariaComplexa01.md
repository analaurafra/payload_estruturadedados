# Instrumento Particular de Constituição de Garantia Fiduciária

**Proposta de referência:** `{{idProposta}}`  
**Emissão:** `{{dataEmissao}}`

**Valor total do crédito:** R$ `{{valorEmprestimo}}`

---

## Devedor Principal

- **Razão social / Nome:** `{{devedorPrincipal.razaoSocial}}`  
- **CNPJ:** `{{devedorPrincipal.cnpj}}`  
- **Endereço:** `{{devedorPrincipal.endereco.logradouro}}`, nº `{{devedorPrincipal.endereco.numero}}`, `{{devedorPrincipal.endereco.complemento}}`  
	Bairro: `{{devedorPrincipal.endereco.bairro}}` — `{{devedorPrincipal.endereco.cidade}}/{{devedorPrincipal.endereco.estado}}`, CEP: `{{devedorPrincipal.endereco.cep}}`

---

## Fiduciantes Garantidores

*(O bloco abaixo repete para cada fiduciante do array `fiduciantesGarantidores`)*

- **Nome:** `{{nome}}`  
- **Nacionalidade / Profissão:** `{{nacionalidade}}` / `{{profissao}}`  
- **Documentos:** RG `{{rg}}` `{{orgaoEmissor}}` — CPF `{{cpf}}`  
- **Endereço residencial:** `{{enderecoResidencial.logradouro}}`, nº `{{enderecoResidencial.numero}}`, Bairro `{{enderecoResidencial.bairro}}`, `{{enderecoResidencial.cidade}}/{{enderecoResidencial.estado}}`  
- **Estado Civil / Regime de Bens:** `{{estadoCivil}}` — `{{regimeBens}}`

### Condicional: Anuência do Cônjuge

> **Regra condicional 1:** somente incluir se `{{#if regrasGatilho.exigirAssinaturaConjuge}}` for verdadeiro.

> **Bloco (apenas quando aplicável):**  
> DA ANUÊNCIA OBRIGATÓRIA DO CÔNJUGE:  
> Neste ato, comparece também como anuente o cônjuge: `{{dadosConjuge.nomeConjuge}}`, RG `{{dadosConjuge.rgConjuge}}` (`{{dadosConjuge.orgaoEmissorConjuge}}`), CPF `{{dadosConjuge.cpfConjuge}}`.

---

## Cláusula Primeira — Da Garantia Fiduciária dos Bens

Em garantia ao cumprimento de todas as obrigações contratuais, os Fiduciantes alienam ao `{{credorFiduciario.nomeCredor}}` os seguintes bens de sua propriedade:

*(Repetir para cada item do array `bensImoveis`)*

- **Tipo do bem:** `{{tipo}}`  
- **Descrição legal:** `{{descricao}}`  
- **Localização:** `{{enderecoImovel.logradouro}}`, nº `{{enderecoImovel.numero}}`, `{{enderecoImovel.bairro}}` — `{{enderecoImovel.cidade}}/{{enderecoImovel.estado}}`, CEP: `{{enderecoImovel.cep}}`  
- **Registro / Matrícula:** Matrícula nº `{{matricula}}` perante o `{{cartorio}}`.

### Condicional: Notificação em Cartório

> **Regra condicional 2:** incluir o bloco abaixo se `{{#if regrasGatilho.notificacaoCartorio}}` for verdadeiro.

> **Cláusula Segunda — Da Consolidação da Propriedade:**  
> Fica o Credor Fiduciário autorizado a acionar o cartório `{{bensImoveis.0.cartorio}}` (do 1º bem) para intimar o fiduciante `{{fiduciantesGarantidores.0.nome}}` (1º fiduciante) a purgar a mora, caso ocorra impontualidade no pagamento das obrigações.

---

## Resumo prático

- Campos entre `{{ }}` são placeholders do template (variáveis).  
- Blocos marcados como condicionais dependem das flags booleanas (`regrasGatilho.*`) para serem incluídos no documento final.

---

*Arquivo convertido e formatado como Markdown para uso como guia de template/README ou para conversão em Handlebars.*