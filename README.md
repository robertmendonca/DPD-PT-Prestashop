# Módulo DPD Portugal para PrestaShop

Módulo gratuito para integrar a DPD Portugal no PrestaShop.

Este módulo permite criar métodos de envio DPD, incluindo entregas ao domicílio e entregas em pontos Pickup, de acordo com os dados fornecidos pela DPD ao cliente.

## Loja demo

Pode testar o módulo numa loja de demonstração:

**Loja demo:**

https://demo-dpd.rgcconsulting.pt/

**Backoffice demo:**

https://demo-dpd.rgcconsulting.pt/admin340be9ii62vxyzfnd9y/

Dados de acesso ao backoffice demo:

```text
Email: demo@exemplo.com
Password: Demo@Demo
```

Esta conta serve apenas para demonstração e testes básicos do módulo.

## Antes de instalar

Antes de configurar o módulo, o cliente deve solicitar à DPD os dados de acesso à API.

Sem estes dados, o módulo pode ser instalado, mas não conseguirá criar expedições.

## Dados necessários da DPD

Solicite à DPD os seguintes dados:

- Utilizador da API
- Palavra-passe da API
- Conta DPD de 8 dígitos para cada serviço contratado
- Confirmação dos serviços ativos na sua conta
- Dados do expedidor/remetente

## Serviços DPD suportados

O módulo está preparado para os seguintes serviços:

| Conta exemplo | Serviço |
|---|---|
| 09999001 | DPD Portugal Home |
| 09999002 | DPD Portugal Shop / Pickup |
| 09999003 | DPD Portugal Ilhas |
| 09999004 | DPD Espanha Home |
| 09999005 | DPD Espanha Shop / Pickup |
| 09999006 | DPD Internacional Home |
| 09999007 | DPD Internacional Shop / Pickup |

Os números acima são apenas exemplos. Cada cliente deve preencher as contas reais fornecidas pela DPD.

## Requisitos

- PrestaShop 8.x
- PHP compatível com a versão do PrestaShop utilizada
- cURL ativo no servidor
- Conta ativa na DPD Portugal
- Dados de acesso à API DPD

## Instalação

1. Faça download do ficheiro `rgcdpdpt-0.x.x.zip` do módulo.
2. Aceda ao backoffice do PrestaShop.
3. Vá a **Módulos > Gestor de módulos**.
4. Clique em **Carregar um módulo**.
5. Envie o ficheiro `.zip`.
6. Após a instalação, clique em **Configurar**.

## Configuração básica

Depois de instalar o módulo, preencha as abas de configuração.

### DPD

Nesta aba deve preencher:

- Modo de operação
- URL de autenticação/token
- URL de criação de expedição
- URL de recolha
- URL de fecho do dia
- Utilizador da API
- Palavra-passe da API

### Expedidor / Shipper

Nesta aba deve preencher os dados da empresa que envia as encomendas:

- Nome
- Morada
- Código postal
- Localidade
- País
- Telefone
- Email

### Tipologia de serviços / Contas DPD

Nesta aba deve preencher as contas DPD de acordo com os serviços contratados.

Ative apenas os serviços que a sua conta DPD tem contratados.

### Portes

Nesta aba pode configurar os valores dos portes para cada serviço.

### Pesquisa de pontos Pickup

Nesta aba pode configurar os dados necessários para pesquisa de pontos Pickup.

### Diagnóstico

Use esta aba para validar a configuração e testar a ligação à DPD.

## Utilização

Após a configuração:

1. O cliente escolhe o método de envio no checkout.
2. Se escolher uma opção Pickup, deverá selecionar um ponto DPD Pickup.
3. Após a encomenda ser criada, o lojista poderá criar a expedição DPD no backoffice.
4. O módulo gera a informação necessária para o envio.

## Suporte

Este módulo é disponibilizado gratuitamente para clientes DPD.

A instalação e configuração básica podem estar incluídas num apoio inicial de até **15 minutos**, conforme acordo com a DPD.

Caso seja necessário apoio adicional, será cobrado um pack de suporte de:

**20€ + IVA por cada pack adicional de 30 minutos**

O suporte pode incluir:

- Instalação do módulo
- Configuração inicial
- Validação dos dados DPD
- Apoio em erros de ligação à API
- Apoio em configuração de métodos de envio

O suporte não inclui, salvo acordo específico:

- Correções em temas personalizados
- Problemas gerais do PrestaShop
- Desenvolvimento à medida
- Alterações específicas fora do funcionamento padrão do módulo
- Correção de problemas causados por outros módulos

## Recomendações

- Não partilhe publicamente o utilizador ou palavra-passe da API DPD.
- Não publique dados reais de clientes em issues públicas.
- Antes de pedir suporte, confirme se os dados fornecidos pela DPD estão corretos.
- Após configurar o módulo, faça sempre um teste com uma encomenda real ou de teste.

## Problemas frequentes

### O módulo instala, mas não cria expedições

Verifique se:

- O utilizador da API está correto
- A palavra-passe está correta
- As contas DPD estão preenchidas
- O serviço está ativo na DPD
- O servidor tem cURL ativo
- A loja consegue comunicar com a API da DPD

### O Pickup não aparece no checkout

Verifique se:

- O serviço Pickup está ativo
- A conta DPD Pickup foi preenchida
- O carrier foi criado corretamente
- O cliente tem uma morada válida
- O código postal está correto

### O mapa Pickup não carrega

Verifique se:

- A configuração de Pickup está preenchida
- O código postal do cliente está correto
- O navegador não está a bloquear scripts
- Não existe conflito com o tema ou outros módulos

## Licença

Este módulo é disponibilizado gratuitamente para utilização por clientes DPD.

A redistribuição, alteração ou utilização comercial fora deste contexto deve respeitar os termos definidos pelo proprietário do módulo.
