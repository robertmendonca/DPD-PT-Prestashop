# Módulo DPD Portugal para PrestaShop

Módulo de integração **DPD Portugal** para lojas **PrestaShop 8.x**.

Este módulo permite disponibilizar métodos de envio DPD no checkout da loja, incluindo entrega ao domicílio e entrega em pontos Pickup/Shop, e permite criar expedições DPD a partir da encomenda no backoffice do PrestaShop.

> **Versão atual:** 0.7.7  
> **Nome do módulo:** RGC DPD PT  
> **Compatibilidade:** PrestaShop 8.x  
> **Âmbito:** Portugal Continental, Portugal Ilhas, Espanha e Internacional, conforme os serviços contratados com a DPD.

> **PrestaShop 9.x:** em validação. O módulo pode funcionar, mas ainda requer teste funcional completo antes de ser considerado oficialmente compatível.
---

## Download do módulo

Neste repositório, descarregue o ficheiro `.zip` do módulo e instale-o diretamente no backoffice do PrestaShop.

Não é necessário descarregar código-fonte, executar comandos técnicos ou alterar ficheiros do módulo manualmente.

---

## Testar antes de instalar

Pode visualizar o comportamento do módulo numa loja demo:

**Loja demo:**

https://demo-dpd.rgcconsulting.pt/

**Backoffice demo:**
https://demo-dpd.rgcconsulting.pt/admin347jaziuaw72gky9cvo/

Dados de acesso ao backoffice demo:

```text
Email: demo@exemplo.com
Password: Demo@Demo
```

A loja demo serve para conhecer o fluxo de checkout, a seleção de pontos Pickup e o comportamento geral do módulo.

---

## Para quem é este módulo

Este módulo destina-se a clientes DPD que utilizam PrestaShop e pretendem integrar os serviços DPD na sua loja online.

Para criar expedições reais, é obrigatório ter uma conta DPD válida, credenciais API e contas DPD de serviço fornecidas pela DPD.

---

## Principais funcionalidades

### No checkout da loja

- Apresenta métodos de envio DPD conforme a morada do cliente.
- Suporta entrega ao domicílio através de serviços Home.
- Suporta entrega em pontos Pickup/Shop.
- Mostra lista e mapa de pontos Pickup quando o cliente escolhe um serviço Pickup/Shop.
- Exige a seleção de um ponto Pickup antes da finalização da encomenda.
- Usa ícones DPD nos métodos de envio e no mapa.

### No backoffice do PrestaShop

- Permite configurar credenciais e endpoints da API DPD.
- Permite configurar contas DPD por tipologia de serviço.
- Cria e repara automaticamente os transportadores DPD no PrestaShop.
- Permite criar uma expedição DPD a partir da encomenda.
- Guarda a guia DPD e a etiqueta PDF.
- Atualiza o tracking da encomenda no PrestaShop.
- Disponibiliza área de diagnóstico com logs e informação útil para suporte.

---

## Serviços DPD suportados

O módulo trabalha por tipologia de serviço. Cada serviço deve ser ativado apenas se estiver contratado e validado pela DPD.

| Serviço | Tipo de entrega | Destino |
|---|---:|---|
| DPD Portugal Home | Home | Portugal Continental |
| DPD Portugal Shop | Pickup/Shop | Portugal Continental |
| DPD Portugal Ilhas | Home | Madeira e Açores |
| DPD Espanha Home | Home | Espanha |
| DPD Espanha Shop | Pickup/Shop | Espanha |
| DPD Internacional Home | Home | Países diferentes de Portugal e Espanha |
| DPD Internacional Shop | Pickup/Shop | Países diferentes de Portugal e Espanha |

Cada serviço utiliza uma **conta DPD de 8 dígitos**. As contas devem ser fornecidas pela DPD.

---

## Requisitos

### Loja

- PrestaShop 8.x.
- Produtos físicos.
- Backoffice com permissão para instalar módulos.
- Países, zonas, moradas e transportadoras corretamente configurados.
- Checkout compatível com o fluxo padrão do PrestaShop.

### Servidor

Recomendado:

- PHP 8.1 ou superior.
- Extensão PHP `curl` ativa.
- Extensão PHP `json` ativa.
- Extensão PHP `openssl` ativa.
- Extensão PHP `soap` recomendada para pesquisa Pickup.

Para o mapa Pickup, o front office precisa conseguir carregar recursos externos usados pelo Leaflet/OpenStreetMap.

---

## Antes de instalar: dados necessários da DPD

Antes de configurar o módulo, solicite à DPD os dados da sua conta.

Peça especificamente:

- API username / utilizador API;
- API password / password API;
- client ID;
- client secret;
- URL OAuth/token;
- URL de criação de expedição;
- URL de pedido de recolha, se aplicável;
- URL de fecho do dia/manifesto, se aplicável;
- chave Pickup/MyPudo, se usar pontos Pickup/Shop;
- contas DPD de 8 dígitos para cada serviço contratado.

Sem estes dados, o módulo pode ser instalado, mas não conseguirá criar expedições reais.

### Modelo de pedido à DPD

```text
Boa tarde,

Preciso configurar o módulo DPD para PrestaShop.

Podem enviar, por favor, os dados de API e as contas DPD de 8 dígitos para os serviços contratados?

Serviços pretendidos:
- Portugal Home
- Portugal Shop/Pickup
- Portugal Ilhas
- Espanha Home
- Espanha Shop/Pickup
- Internacional Home
- Internacional Shop/Pickup

Obrigado.
```

---

## Instalação pelo backoffice

1. Descarregue o ficheiro ZIP do módulo.
2. Entre no backoffice do PrestaShop.
3. Vá a **Módulos > Gestor de módulos**.
4. Clique em **Carregar um módulo**.
5. Selecione o ficheiro ZIP.
6. Aguarde o upload terminar.
7. Clique em **Instalar**.
8. Abra a configuração do módulo **RGC DPD PT**.

---

## Configuração inicial

Depois de instalar, aceda à configuração do módulo e preencha as abas principais.

### 1. Aba DPD

Preencha os dados técnicos fornecidos pela DPD:

- modo de operação: QA/teste ou produção;
- OAuth URL;
- URL de criação de expedição;
- URL de recolha, se aplicável;
- URL de fecho do dia/manifesto, se aplicável;
- API username;
- API password;
- client ID;
- client secret.

Depois de guardar, use o botão **Testar OAuth DPD**, se disponível, para validar a autenticação.

### 2. Aba Tipologia de serviços / Contas DPD

Configure os serviços contratados:

- ativo/inativo;
- conta DPD de 8 dígitos;
- nome visível do transportador no checkout;
- tipo de entrega: Home ou Pickup/Shop.

Ative apenas os serviços que foram contratados e validados pela DPD.

### 3. Aba Expedidor / Shipper

Preencha os dados da empresa que envia a encomenda:

- nome;
- email;
- telefone;
- telemóvel;
- morada;
- código postal;
- cidade;
- país.

Estes dados são enviados à DPD no pedido de criação da expedição.

### 4. Aba Operação

Configure:

- peso máximo permitido;
- Predict, se aplicável;
- número de volumes por defeito;
- formato da etiqueta;
- ativação de logs.

### 5. Aba Pesquisa de pontos Pickup

Se usar serviços Pickup/Shop, configure:

- Pickup WSDL;
- Pickup carrier code;
- Pickup key;
- quantidade máxima de pontos;
- distância máxima.

A chave Pickup/MyPudo deve ser fornecida pela DPD.

### 6. Aba Portes

Defina o preço base de cada serviço DPD.

O módulo usa estes valores para apresentar o custo de envio no checkout.

### 7. Aba Diagnóstico

Use esta área para:

- testar autenticação;
- verificar serviços ativos;
- consultar carriers configurados;
- analisar mensagens de erro;
- recolher informação para suporte.

---

## Depois de configurar

Após qualquer alteração importante:

1. Clique em **Guardar configurações**.
2. Clique em **Reparar carriers**.
3. Limpe a cache do PrestaShop.
4. Faça uma encomenda de teste.
5. Confirme que o método DPD correto aparece no checkout.
6. Confirme que a criação da expedição funciona no backoffice.

---

## Utilização no checkout

### Entrega Home

O cliente escolhe o método DPD Home disponível para a sua morada e finaliza a compra normalmente.

### Entrega Pickup/Shop

Quando o cliente escolhe um serviço Pickup/Shop:

1. O módulo carrega os pontos próximos com base no código postal da morada de entrega.
2. O cliente pode escolher o ponto numa lista ou diretamente no mapa.
3. A seleção do ponto Pickup é obrigatória.
4. O ponto escolhido fica associado ao carrinho e à encomenda.

O botão **Procurar pontos Pickup** serve para atualizar a pesquisa, por exemplo quando o cliente altera o código postal.

---

## Criação da expedição DPD

A expedição não é criada automaticamente no momento da compra.

Esta decisão evita criar expedições para encomendas ainda não pagas, canceladas, pendentes de validação ou ainda em preparação.

Para criar a expedição:

1. Entre no backoffice do PrestaShop.
2. Vá a **Encomendas**.
3. Abra a encomenda pretendida.
4. Confirme que a encomenda está pronta para expedir.
5. No bloco **DPD Portugal**, clique em **Criar expedição DPD**.
6. Aguarde a resposta da DPD.
7. Abra ou descarregue a etiqueta PDF.
8. Imprima a etiqueta e prepare a encomenda.

Depois da criação da expedição, o módulo guarda:

- número da guia DPD;
- etiqueta PDF;
- tracking no PrestaShop;
- resposta da DPD para diagnóstico.

---

## Atualização do módulo

Para atualizar para uma nova versão:

1. Faça backup da loja e da base de dados.
2. Descarregue o novo ZIP do módulo.
3. Instale ou atualize pelo backoffice do PrestaShop.
4. Confirme que a versão foi atualizada.
5. Abra a configuração do módulo.
6. Clique em **Guardar configurações**.
7. Clique em **Reparar carriers**.
8. Limpe a cache do PrestaShop.
9. Teste o checkout e a criação de expedição.

---

## Resolução rápida de problemas

### Os métodos DPD não aparecem no checkout

Verifique:

- se o módulo está instalado e ativo;
- se os serviços DPD estão ativos na configuração;
- se as contas DPD de 8 dígitos estão preenchidas;
- se clicou em **Reparar carriers**;
- se a morada do cliente está completa;
- se o país/região é abrangido pelo serviço ativo;
- se o peso do carrinho não ultrapassa o limite configurado;
- se os produtos são físicos;
- se a cache do PrestaShop foi limpa.

### O mapa Pickup não aparece

Verifique:

- se o cliente selecionou um método Pickup/Shop;
- se a morada tem código postal válido;
- se a chave Pickup/MyPudo foi preenchida;
- se o servidor consegue comunicar com o webservice Pickup;
- se o tema da loja não bloqueia JavaScript;
- se o front office consegue carregar recursos externos do mapa.

### A expedição DPD falha

Verifique:

- API username e API password;
- client ID e client secret;
- endpoint usado: QA/teste ou produção;
- conta DPD associada ao serviço escolhido;
- permissões da conta na DPD;
- IP autorizado, se aplicável;
- morada do destinatário;
- telefone/telemóvel do destinatário;
- ponto Pickup selecionado, no caso de Pickup/Shop;
- mensagem apresentada na aba **Diagnóstico**.

### A guia não aparece, mas a etiqueta foi criada

Se a API devolver a etiqueta mas não devolver a guia num campo reconhecido, o bloco DPD da encomenda pode permitir:

- recuperar a guia a partir da resposta guardada;
- recuperar a guia a partir da etiqueta;
- inserir a guia manualmente.

---

## Perguntas frequentes

### O módulo é gratuito?

Sim. O módulo é disponibilizado gratuitamente para clientes DPD.

### Posso usar o módulo sem contrato com a DPD?

Pode instalar, mas não conseguirá criar expedições reais sem credenciais e contas DPD válidas.

### A DPD fornece os dados que devo preencher?

Sim. As credenciais API, endpoints, chave Pickup e contas DPD devem ser solicitadas à DPD.

### Posso ativar apenas alguns serviços?

Sim. Deve ativar apenas os serviços contratados e validados pela DPD.

### O módulo suporta Portugal Ilhas?

Sim. Existe serviço específico para Madeira e Açores, desde que a respetiva conta DPD esteja configurada.

### O módulo suporta Espanha e Internacional?

Sim, desde que os serviços estejam contratados e as contas DPD correspondentes estejam configuradas.

### O mapa Pickup aparece automaticamente?

Sim. Quando o cliente seleciona um serviço Pickup/Shop, o módulo carrega os pontos automaticamente com base no código postal da morada de entrega.

### A expedição é criada automaticamente?

Não. Nesta versão, a criação da expedição é manual no backoffice da encomenda.

### O módulo calcula portes avançados por peso, valor ou categoria?

Nesta versão, o módulo trabalha com preço base por serviço. Regras avançadas de portes por peso, valor, categoria ou país/região não estão incluídas.

---

## Limitações atuais

Nesta versão, o módulo ainda não inclui:

- criação automática de expedição por mudança de estado da encomenda;
- pedido de recolha diretamente pelo backoffice;
- fecho do dia/manifesto pelo backoffice;
- cancelamento de expedição;
- tracking detalhado por API;
- regras avançadas de portes por peso, valor, categoria ou país/região.

---

## Suporte

O módulo é disponibilizado gratuitamente.

Cada cliente tem direito a **15 minutos gratuitos de apoio inicial pela DPD** para instalação ou primeira configuração.

Após esse período, o suporte técnico adicional é cobrado em packs de:

```text
20 EUR + IVA por pack adicional de 30 minutos
```

O suporte pode incluir:

- instalação assistida;
- configuração das contas DPD;
- validação dos carriers;
- análise de erros no checkout;
- análise de erros da API;
- validação do fluxo Pickup;
- testes de criação de expedição.

### Dados úteis para pedir suporte

Ao pedir suporte, envie:

```text
Loja: https://exemplo.pt
PrestaShop: 8.x
PHP: 8.x
Módulo: 0.7.7
Ambiente: QA/teste ou produção
Serviço DPD usado: Portugal Home / Portugal Shop / Ilhas / Espanha / Internacional
Erro apresentado:
Passos para reproduzir:
```

Também pode ser útil enviar prints da configuração, da encomenda e da mensagem de erro, desde que não contenham credenciais nem dados pessoais sensíveis.

---

## Segurança

Nunca publique em issues, screenshots, fóruns ou repositórios públicos:

- API password;
- client secret;
- chave Pickup/MyPudo;
- tokens OAuth;
- etiquetas PDF reais;
- dados pessoais de clientes;
- moradas completas de clientes;
- payloads completos de expedições reais;
- logs com dados pessoais.

Se uma credencial for exposta por engano, contacte a DPD e solicite a substituição/rotação da credencial.

---

## Responsabilidade de configuração

O correto funcionamento do módulo depende de:

- credenciais DPD válidas;
- serviços contratados e ativos na DPD;
- contas DPD corretas por serviço;
- endpoints corretos para QA/teste ou produção;
- configuração correta da loja PrestaShop;
- servidor com extensões PHP necessárias.

Alguns erros podem depender da validação da própria DPD, por exemplo credenciais inválidas, IP não autorizado, conta sem permissão para Pickup ou serviço contratado diferente do serviço configurado.

---

## Créditos

Desenvolvido por **RGC Consulting** para integração DPD Portugal em PrestaShop.

## Apoie o meu trabalho ☕  
Se este projeto te ajudou, considera comprar-me um café:  

[![Buy Me a Coffee](https://github.com/user-attachments/assets/e5e0b7a8-4ec3-4a20-b5c8-07301078a283)](https://www.buymeacoffee.com/robertmendonca)
