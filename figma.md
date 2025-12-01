# Ligações via WhatsApp

---

# Uma breve Introdução

Módulo de mensageria da Pedido Pago

- Lançado em Novembro de 2022
- Desde o início com a API oficial do WhatsApp Business
- ⚡️Objetivo: Agilizar o atendimento via WhatsApp

Trazendo funcionalidades básicas de chatbot e atendimento com múltiplos atendentes

---

# Melhorias ao logo dos anos

Desde 2022 até agora, trabalhamos em diversas melhorias para o nosso módulo de mensageria para a Pedido Pago; Sendo assim, listamos aqui os principais tópicos;

- Drivers alternativos ao WhatsApp

Apesar do WhatsApp ser o canal de atendimento com o maior volume de pessoas, ele não é o único canal que os clientes utilizam;

e por este motivo e outros fatores, como custo por mensagem, clientes de diferentes localidades tendo um nicho diferente de mensageria, fizemos
uma grande mudança na mensageria para ser um centralizador de canais de atendimento, e o primeiro canal ficou com o WhatsApp Business;

antes a mensageria era uma coisa só do WhatsApp, foi refatorada para que o WhatsApp fosse apenas um módulo (ou canal), dentre outros como:

### Driver Maniback

O maniback, sendo um app desenvolvido pela Pedido Pago, o nosso app de cashback, foi o primeiro beneficiário desta mudança; Se o cliente já tem o 
maniback instalado no celular, damos preferência a enviar mensagens via este app maniback, pois o custo muito menor que o do WhatsApp;

### Driver email

Integramos Google, Microsoft e outros via SMTP e IMAP

### Driver telegram

(por enquanto)

- Conversões automáticas de mensagem

Que foi uma melhoria muito importante pra redução de custos, já que uma mensagem de marketing custa em média 35 centavos para a empresa.

neste caso, mensagens de marketing, que viram mensagens interativas quando existe uma janela aberta com o cliente;

aquela janela de serviço que começa quando o cliente
envia uma mensagem para a empresa.

- Ajustes de Escalabilidade

O volume de mensagens, usuários ativos (colaboradores) aumentou mais que 10x desde o último ano; Sendo assim, passamos por várias iterações de performance ao longo desses 3 anos;

no horário entre 9 - 12h, cerca de 10 mil atualizações de contato são feitas por minuto;

Por que isso é um desafio? Pois as atualizações, sejam em dados de orçamento - status - numero de pedido, vendedor atribuído, data de sincronização com o ERP; Boa parte dessas atualizações precisam ser buscáveis, em tempo real, o tempo todo;

Sendo assim, essas 10k atualizações por minuto precisam ser consumidas e enviadas p/ o banco de dados responsável pela busca desses dados, para que ele consiga responder a uma busca (com diversos filtros) em menos de 100ms;

---

# Ligações

Apesar da maior parte dos clientes, gerações mais novas, terem a preferência de comunicação via texto; Ainda sim a comunicação direta via áudio tem o seu valor (que inclusive no fator de negociação com o cliente pode ser mais eficaz); E ligações, parte dos clientes, colaboradores e farmácias tem preferência em comunicação via telefone, principalmente a área de vendas;

## Temos dois fluxos principais:

- Empresa Liga para o Cliente
- Cliente Liga para a Empresa

---

# No Fluxo Empresa Liga para o Cliente

Na primera etapa, um modelo de mensagem é enviado para o cliente, que pede uma autorização pro cliente, para poder receber ligações, e o cliente tem a opção de aceitar ou recusar receber ligações (ou ele pode simplesmente ignorar, acontece);

O Meta impõe esse pré-requisito com intuito de previnir spam e ligações indesejadas. Isto não é algo que é imposto pela Pedido Pago, mas mesmo assim, eu no ponto de vista do cliente, acho uma boa medida para evitar o que acontece na telefonia tradicional, que mesmo estando na lista de não perturbe da Anatel etc, ainda sim recebemos diversas ligações robôs (tem também essa questão de ter muitos golpes)

Após a confirmação do cliente, o atendente é notificado;

E após a ligação ser iniciada, o atendente tem opção de convidar outros colaboradores pra essa mesma ligação;

---

# Visualizar Fluxo

(clicar em solicitar permissão)

como esse processo é assíncrono; pode ser que o cliente demore a clicar no botão de aceitar (ou recusar), e o atendente pode estar em outra tela, com outro cliente;

neste exemplo de agora, estamos presumindo que o cliente aceitou receber ligações segundos após receber o modelo de mensagem;

(clicar em aceitar)

após o aceite do cliente, a Empresa
tem até 7 dias para fazer ligações para ele, sendo que tem um limite máximo de 5 ligações por um período de 24h (iniciadas pela empresa)

(clicar em ligar)

Já neste slide podemos ver a ligação sendo iniciada pelo Luis

E neste cenário o cliente tem até 30 segundos para aceitar ou recusar a ligação

Podemos ver que o cliente atendeu a ligação, e também no filtro de ligações em adamento, podemos ver na coluna da esquerda a ligação iniciada pelo Luis

### Opção de convidar outros colaboradores

Existe também a opção de convidar outros colaboradores, e para faciliar o processo, os colaboradores já envolvidos neste atendimento são listados em primeiro lugar;

Neste exemplo vou convidar o Fernando;

O Fernando recebe um modal na tela dele perguntando se quer aceitar a ligação;

Neste exemplo ele aceitou e já está fazendo parte desta chamada;

(clicar na foto do Fernando novamente)

Temos também a opcão de reduzir o volume de cada participante (e também silenciar);

---

# Ligações de Clientes

# 100% 
Configurável 🛠️

Assim como fazer ligações, para receber ligações podemos configurar:

* Se recebemos ligações (ou não)
* Se recebemos ligações 24h/dia ou se seguimos os horários de atendimento
* Se adicionamos os próximos feriados para não ter disponibilidade nestes dias;
* Se desejamos habilitar um botão para o cliente notificar a farmácia para ligar de volta assim que voltar a estar disponível;


Nestas imagens, podemos observar:

(TL)
Empresa ativou o botão para o cliente ligar livremente para a empresa;

(TR)
Empresa desativou o botão para o cliente ligar livremente para a empresa;

Isso não impede que o cliente ligue em todas as situações; Por exemplo: a farmácia pode optar por não mostrar esse botão, mas pode enviar um template de atendimento com um dos botões com uma call to action de ligar para a farmácia; Que é esse exemplo de mensagem que o cliente recebeu;

(BL)
Este aqui é um exemplo de um cliente ligando p/ a empresa;

(BR)
Este exemplo aqui é do cliente visualizando o período que a empresa pode ligar p/ ele (ou seja, é um exemplo que ocorreu após o cliente aceitar receber ligações)

O cliente pode revogar esta permissão a qualquer momento (e somos notificados quando isso acontece);

---

# Cliente realiza ligação para a empresa

Neste exemplo de ligações, os colaboradores diretamente envolvidos com esse cliente, seja de pedidos anteriores ou de uma atribuição recente, serão os primeiros que receberão essa chamada vinda do cliente. Caso nenhum colaborador envolvido esteja online, a chamada será oferecida para os demais atendentes.

---

Fluxo de cliente ligando

---

# Histórico de ligações

---

# 100%
BSP Disparalha

<!--
Estes dois requerimentos são cobertos para quem tem o a integração via o nosso BSP Disparalha
-->

---

# Pré-requisitos

* Ter a assinatura de webhooks do módulo de ligações (`calls`)
É com isso que o Meta informa a gente que tem novas ligações para receber (e as atualizações de permissão dos clientes)

---

# Integrações Futuras

Já estamos em conversas para integrar a telefonia via WhatsApp
com sistemas tradicionais de telefonia (SIP, VoIP, etc)

Qual o motivo? O motivo é que, no sistema de telefonia geralmente é feito uma distribuição
automática de chamadas, e com a integração será possível aproveitar essa funcionalidade
já existente.

A URA pode ser desde uma mensagem automática (para clientes que ligam fora do horário de atendimento)
até funcionalidades básicas de atendimento.

E por último, temos o objetivo de, assim como fizemos para os ERPs, ter uma API pública
que permita que outros parceiros façam uma integração específica já com essa API que estará disponível.