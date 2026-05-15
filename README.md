# RGC DPD PT - Módulo DPD Portugal para PrestaShop

Módulo gratuito para integrar serviços da **DPD Portugal** em lojas **PrestaShop 8.x**.

O módulo permite disponibilizar métodos de envio DPD no checkout, incluindo entrega ao domicílio e entrega em pontos **DPD Pickup / Shop**, e permite ao lojista criar expedições DPD diretamente a partir da encomenda no backoffice do PrestaShop.

> Este repositório é destinado a clientes DPD. Para instalar o módulo, utilize apenas o ficheiro ZIP disponibilizado neste repositório.

---

## Conteúdo do repositório

```text
README.md
rgcdpdpt-0.7.7.zip
```

- `README.md`: guia de instalação, configuração e utilização.
- `rgcdpdpt-0.7.7.zip`: ficheiro do módulo a instalar no PrestaShop.

Não é necessário descompactar o ZIP manualmente. A instalação deve ser feita pelo gestor de módulos do PrestaShop.

---

## Funcionalidades principais

- Criação automática dos métodos de envio DPD no PrestaShop.
- Suporte a entrega ao domicílio e entrega em pontos DPD Pickup / Shop.
- Pesquisa de pontos Pickup no checkout com base no código postal da morada de entrega.
- Seleção de ponto Pickup pelo cliente antes de concluir a encomenda.
- Mapa de pontos Pickup quando existirem coordenadas disponíveis.
- Configuração de contas DPD por tipologia de serviço.
- Configuração de portes por serviço.
- Criação de expedição DPD no backoffice da encomenda.
- Geração e abertura da etiqueta PDF da expedição.
- Gravação do número de guia / tracking na encomenda.
- Área de diagnóstico para validação da configuração e consulta de erros recentes.

---

## Requisitos

Antes de instalar, confirme que a loja cumpre os seguintes requisitos:

- PrestaShop 8.x.
- PHP compatível com a versão do PrestaShop em utilização.
- Extensão PHP cURL ativa.
- Comunicação externa permitida entre o servidor da loja e os serviços da DPD.
- Conta ativa na DPD Portugal.
- Dados de acesso à API fornecidos pela DPD.

Para a pesquisa de pontos Pickup, recomenda-se também que a extensão PHP SOAP esteja ativa. Quando SOAP não está disponível, o módulo tenta utilizar cURL como alternativa.

Para o mapa dos pontos Pickup, o browser do cliente precisa de conseguir carregar recursos externos de mapa, nomeadamente Leaflet e OpenStreetMap. Caso o mapa não carregue, a seleção pela lista de pontos pode continuar disponível.

---

## Antes de instalar

O módulo pode ser instalado sem credenciais, mas não conseguirá criar expedições enquanto os dados da DPD não forem configurados.

Antes de iniciar a configuração, solicite à DPD os dados necessários para a sua conta.

### Dados necessários da DPD

Solicite à DPD:

- Utilizador da API.
- Palavra-passe da API.
- Client ID, se aplicável.
- Client Secret, se aplicável.
- Conta DPD de 8 dígitos para cada serviço contratado.
- Confirmação dos serviços ativos na sua conta.
- Dados do expedidor / remetente.
- Dados necessários para pesquisa de pontos Pickup, quando aplicável.
- Confirmação de que o IP do servidor da loja está autorizado, caso a DPD utilize whitelist de IP.

Sem estes dados, a ligação à API poderá falhar mesmo que o módulo esteja instalado corretamente.

---

## Serviços DPD suportados

O módulo está preparado para os seguintes serviços:

| Serviço | Tipo de entrega | Destino previsto |
|---|---:|---|
| DPD Portugal Home | Domicílio | Portugal continental |
| DPD Portugal Shop / Pickup | Pickup | Portugal continental |
| DPD Portugal Ilhas | Domicílio | Madeira e Açores |
| DPD Espanha Home | Domicílio | Espanha |
| DPD Espanha Shop / Pickup | Pickup | Espanha |
| DPD Internacional Home | Domicílio | Outros países |
| DPD Internacional Shop / Pickup | Pickup | Outros países |

Cada serviço deve ser ativado apenas se estiver contratado na conta DPD do cliente.

As contas apresentadas por defeito no módulo são apenas exemplos. O cliente deve substituir esses valores pelas contas reais fornecidas pela DPD.

---

## Instalação

1. Faça download do ficheiro `rgcdpdpt-0.7.7.zip`.
2. Aceda ao backoffice do PrestaShop.
3. Vá a **Módulos > Gestor de módulos**.
4. Clique em **Carregar um módulo**.
5. Envie o ficheiro ZIP do módulo.
6. Aguarde a instalação.
7. Após instalar, clique em **Configurar**.

Depois da instalação, o módulo cria os métodos de envio DPD correspondentes aos serviços ativos na configuração.

---

## Atualização do módulo

Antes de atualizar, recomenda-se fazer backup da loja e da base de dados.

Para atualizar:

1. Faça download da nova versão do ZIP.
2. Aceda ao backoffice do PrestaShop.
3. Vá a **Módulos > Gestor de módulos**.
4. Carregue o novo ZIP do módulo.
5. Confirme que a versão foi atualizada.
6. Entre na configuração do módulo e clique em **Guardar configurações** ou **Reparar carriers**, se necessário.
7. Faça uma encomenda de teste para validar checkout, portes, Pickup e criação de expedição.

---

## Configuração

A configuração do módulo é feita em abas no backoffice.

### 1. DPD

Nesta aba são configurados os dados principais de ligação à API DPD.

Campos principais:

- Modo de operação.
- URL de autenticação / token.
- URL de criação de expedição.
- URL de recolha.
- URL de fecho do dia.
- API username.
- API password.
- Client ID.
- Client Secret.

Use os valores fornecidos ou confirmados pela DPD. Em produção, utilize os endpoints e credenciais de produção.

### 2. Tipologia de serviços / Contas DPD

Nesta aba são configurados os serviços DPD que a loja pode disponibilizar.

Para cada serviço, configure:

- Estado ativo/inativo.
- Conta DPD de 8 dígitos.
- Nome visível no checkout.
- Tipo de entrega: Home ou Pickup.

Ative apenas os serviços realmente contratados com a DPD. Se um serviço estiver ativo mas sem conta válida, o método de envio poderá não aparecer corretamente ou a expedição poderá falhar.

### 3. Expedidor / Shipper

Nesta aba são configurados os dados da empresa que envia as encomendas.

Preencha:

- Nome do remetente.
- Email.
- Telefone.
- Telemóvel, se aplicável.
- Nome da empresa expedidora.
- Morada.
- Código postal.
- Localidade.
- País.

Estes dados são utilizados na criação da expedição DPD.

### 4. Operação

Nesta aba são configurados parâmetros operacionais.

Campos principais:

- Peso máximo permitido.
- Predict ativo/inativo.
- Número de volumes por defeito.
- Formato da etiqueta.
- Logs ativos/inativos.

Se a encomenda ultrapassar o peso máximo configurado, os métodos DPD podem não ficar disponíveis para essa encomenda.

### 5. Pesquisa de pontos Pickup

Nesta aba são configurados os dados necessários para a pesquisa de pontos Pickup / Shop.

Campos principais:

- Pickup WSDL.
- Código do carrier Pickup.
- Chave Pickup.
- Número máximo de pontos a apresentar.
- Distância máxima de pesquisa.

Estes dados devem ser fornecidos ou confirmados pela DPD.

### 6. Portes

Nesta aba pode definir o preço base de cada serviço DPD.

O preço configurado será utilizado pelo PrestaShop para apresentar o custo do método de envio no checkout.

Depois de alterar valores de portes, guarde a configuração para sincronizar os métodos de envio.

### 7. Diagnóstico

Nesta aba pode:

- Confirmar quais os serviços ativos.
- Verificar as contas DPD configuradas.
- Consultar os carriers criados no PrestaShop.
- Consultar logs recentes.
- Testar a autenticação OAuth com a DPD.

Use esta aba sempre que ocorrer erro de ligação, erro de credenciais ou falha na criação da expedição.

---

## Utilização no checkout

Depois de configurado, o módulo disponibiliza os métodos DPD elegíveis no checkout, de acordo com:

- País da morada de entrega.
- Código postal.
- Peso da encomenda.
- Serviços ativos no módulo.
- Contas DPD preenchidas.
- Portes configurados.

Quando o cliente escolhe um método Pickup, o módulo apresenta a pesquisa de pontos Pickup. O cliente deve selecionar um ponto antes de finalizar a encomenda.

Se nenhum ponto Pickup for selecionado, a encomenda não deve avançar com esse método de envio.

---

## Criação de expedição no backoffice

Após a encomenda ser criada:

1. Aceda ao backoffice do PrestaShop.
2. Abra a encomenda.
3. Procure a área **DPD Portugal** na página da encomenda.
4. Clique em **Criar expedição DPD**.
5. Aguarde a resposta da DPD.

Quando a expedição é criada com sucesso, o módulo guarda a informação da expedição e disponibiliza a etiqueta PDF.

Se a DPD devolver o número de guia / tracking, o módulo grava essa informação na encomenda.

---

## Etiqueta PDF e tracking

Na área **DPD Portugal** da encomenda, poderá ver:

- Estado da expedição.
- Número da guia / tracking, quando disponível.
- Botão para abrir a etiqueta PDF.
- Informação do ponto Pickup, quando aplicável.
- Mensagens de erro, caso a expedição não tenha sido criada.

Se a expedição for criada mas o número de guia não for identificado automaticamente, o módulo pode apresentar opções para tentar recuperar a guia ou inseri-la manualmente.

---

## Testes recomendados após configuração

Antes de colocar o módulo em uso real, recomenda-se testar:

1. Checkout com entrega DPD Home para Portugal continental.
2. Checkout com entrega DPD Pickup, selecionando um ponto Pickup.
3. Checkout para ilhas, se esse serviço estiver contratado.
4. Checkout para Espanha, se esse serviço estiver contratado.
5. Criação de expedição numa encomenda de teste.
6. Abertura da etiqueta PDF.
7. Gravação do tracking na encomenda.
8. Cálculo dos portes configurados.

Faça estes testes com dados reais ou dados de teste autorizados pela DPD.

---

## Problemas frequentes

### O módulo instala, mas não cria expedições

Verifique:

- Se o utilizador da API está correto.
- Se a palavra-passe da API está correta.
- Se o Client ID e Client Secret estão corretos.
- Se os endpoints configurados correspondem ao ambiente correto.
- Se as contas DPD de 8 dígitos estão preenchidas.
- Se o serviço está ativo na DPD.
- Se o servidor tem cURL ativo.
- Se o servidor consegue comunicar com a API da DPD.
- Se o IP do servidor precisa de estar autorizado pela DPD.

### O método de envio DPD não aparece no checkout

Verifique:

- Se o serviço está ativo no módulo.
- Se a conta DPD do serviço foi preenchida.
- Se o país e o código postal da morada correspondem ao serviço selecionado.
- Se o peso da encomenda não ultrapassa o limite configurado.
- Se o preço do porte foi configurado.
- Se o carrier foi criado corretamente.
- Se os grupos de clientes e zonas do PrestaShop permitem esse transportador.

### O Pickup não aparece no checkout

Verifique:

- Se o serviço Pickup está ativo.
- Se a conta DPD Pickup foi preenchida.
- Se os dados da pesquisa Pickup estão preenchidos.
- Se o cliente tem uma morada de entrega válida.
- Se o código postal está correto.
- Se o país da morada é suportado pelo serviço Pickup ativo.

### O mapa Pickup não carrega

Verifique:

- Se o browser consegue carregar recursos externos.
- Se existe algum bloqueador de scripts no browser.
- Se o tema ou outro módulo está a bloquear JavaScript no checkout.
- Se a DPD devolveu coordenadas para os pontos encontrados.

Mesmo que o mapa não carregue, a seleção por lista pode continuar disponível.

### A autenticação OAuth falha

Verifique:

- API username.
- API password.
- Client ID.
- Client Secret.
- URL de autenticação.
- Ambiente configurado: teste/QA ou produção.
- Whitelist de IP junto da DPD.

Use o botão **Testar OAuth DPD** na aba Diagnóstico para validar a ligação.

### A expedição falha para uma encomenda específica

Verifique:

- Dados da morada de entrega.
- Código postal.
- País.
- Nome do cliente.
- Telefone ou telemóvel.
- Peso da encomenda.
- Serviço DPD escolhido.
- Conta DPD associada ao serviço.
- Mensagem de erro apresentada pela DPD na área da encomenda ou no Diagnóstico.

---

## Segurança e privacidade

- Não publique credenciais DPD em issues públicas, fóruns ou capturas de ecrã.
- Não partilhe API username, API password, Client Secret ou Pickup Key.
- Ao pedir suporte, oculte dados pessoais de clientes sempre que possível.
- Evite publicar moradas, telefones, emails, números de guia ou payloads completos em locais públicos.
- Mantenha o PrestaShop, PHP e servidor atualizados.
- Faça backup antes de instalar ou atualizar módulos.

---

## Desinstalação

A desinstalação do módulo pode remover configurações, registos internos de Pickup, expedições e logs associados ao módulo.

Antes de desinstalar em ambiente de produção, faça backup da base de dados e confirme se ainda precisa de consultar informações antigas de expedições ou etiquetas.

---

## Suporte

Este módulo é disponibilizado gratuitamente para clientes DPD.

A instalação e configuração básica podem estar incluídas num apoio inicial de até **15 minutos**, conforme acordo com a DPD.

Caso seja necessário apoio adicional, poderá ser cobrado um pack de suporte de:

**20€ + IVA por cada pack adicional de 30 minutos**

O suporte pode incluir:

- Instalação do módulo.
- Configuração inicial.
- Validação dos dados DPD.
- Apoio em erros de ligação à API.
- Apoio na configuração de métodos de envio.
- Apoio na validação de Pickup, etiquetas e tracking.

O suporte não inclui, salvo acordo específico:

- Correções em temas personalizados.
- Problemas gerais do PrestaShop.
- Desenvolvimento à medida.
- Alterações específicas fora do funcionamento padrão do módulo.
- Correção de problemas causados por outros módulos.
- Configuração avançada do servidor ou da loja não relacionada diretamente com a DPD.

Antes de pedir suporte, tenha disponível:

- Versão do PrestaShop.
- Versão do PHP.
- Versão do módulo.
- Serviço DPD afetado.
- Mensagem de erro apresentada.
- Confirmação dos dados fornecidos pela DPD.
- Exemplo de encomenda afetada, sem expor dados sensíveis publicamente.

---

## Utilização autorizada

Este módulo é disponibilizado gratuitamente para utilização por clientes DPD.

A redistribuição, alteração, revenda ou utilização comercial fora deste contexto deve respeitar os termos definidos pelo proprietário do módulo.

---

## Versão

Versão documentada: **0.7.7**

Autor: **RGC Consulting**
