---
theme: apple-basic
# background: path-to-your-image
title: Ligações via WhatsApp
info: com gravações, IA etc
class: text-center
transition: slide-left
mdc: true
duration: 20min
layout: intro
background: 'white'
---

# Ligações via WhatsApp

com gravações, IA etc

<div class="absolute bottom-10">
  <span class="font-700">
    Gabriel Ochsenhofer -
    2025
  </span>
</div>

---
transition: fade-out
---

# Uma breve Introdução

Módulo de mensageria da Pedido Pago

- Lançado em Novembro de 2022
- Desde o início com a API oficial
- ⚡️Objetivo: Agilizar o atendimento via WhatsApp

<!--
Desde o início com a API oficial do WhatsApp Business;
Com o objetivo inicial de agilizar o atendimento via WhatsApp trazendo funcionalidades básicas de chatbot
e atendimento com múltiplos atendentes;
 -->

---

<style>
.slidev-vclick-target {
  transition: all 500ms ease;
}

.slidev-vclick-hidden {
  transform: scale(0);
}
</style>

# Melhorias ao logo dos anos

<v-clicks depth="2">

- Drivers alternativos ao WhatsApp
  - Maniback
  - E-Mail
  - Telegram
- Conversões automáticas de mensagem
  - De marketing para mensagem interativa
  - Redução de custos
- ⏲ Ajustes de Escalabilidade
  - 10x volume de 2024
  - 10k updates/minuto de contatos
  - Filtro/busca de contatos responder em menos de 100ms

</v-clicks>

<!--
Desde 2022 até o momento, trabalhamos em diversas melhorias para o nosso módulo de
mensageria para a Pedido Pago; Sendo assim, listamos aqui os principais tópicos;

-

drivers alternativos ao whatsapp

Apesar do WhatsApp ser o canal de atendimento com o maior volume de pessoas, ele não é o único canal que os clientes utilizam;

e por este motivo e outros fatores, como custo por mensagem, clientes de diferentes localidades tendo um nicho diferente de mensageria, fizemos
uma grande mudança na mensageria para ser um centralizador de canais de atendimento, e o primeiro canal ficou com o WhatsApp Business;
antes a mensageria era uma coisa só do WhatsApp, foi refatorada para que o WhatsApp fosse apenas um módulo (ou canal), dentre outros como:

Driver Maniback

O maniback, sendo um app desenvolvido pela Pedido Pago, o nosso app de cashback, foi o primeiro beneficiário desta mudança; Se o cliente já tem o 
maniback instalado no celular, damos preferência a enviar mensagens via este app maniback, pois o custo muito menor que o do WhatsApp;

Driver email
Integramos Google, Microsoft e outros via SMTP e IMAP

Driver telegram
(por enquanto)

--

Uma melhoria importante também foi a conversão automática de mensagens,
principalmente mensagens de marketing, que viram mensagens interativas quando existe
uma janela aberta com o cliente, aquela janela de serviço que começa quando o cliente
envia uma mensagem para a empresa.

Isto ajuda bastante na redução de custos, já que uma mensagem de marketing
custa em média 35 centavos para a empresa.

--

O volume de mensagens, usuários ativos (colaboradores) aumentou mais que 10x desde o último ano; Sendo assim, passamos por várias iterações de performance ao longo desses 3 anos;

Curiosidade: no horário entre 9 - 12h, cerca de 10 mil atualizações de contato são feitas por minuto;

Por que isso é um desafio? Pois as atualizações, sejam em dados de orçamento - status - numero de pedido, vendedor atribuído, data de sincronização com o ERP; Boa parte dessas atualizações precisam ser buscáveis, em tempo real, o tempo todo;

Sendo assim, essas 10k atualizações por minuto precisam ser consumidas e enviadas p/ o banco de dados responsável pela busca desses dados, para que ele consiga responder a uma busca (com diversos filtros) em menos de 100ms;

Update de contato -> fila de contatos a serem indexados -> deduplicar eventos com o mesmo contato -> atualizações em massa (100 a 200 por update);
Escalabilidade automática -> se o backlog dessa fila de atualizações cresce mais rapido do que está sendo consumida, novos workers são criados para consumir ainda mais contatos em paralelo; (e com isso tem o desafio dos workers não trabalhar com os mesmos contatos ((lock)))
-->

---
layout: section
---

# Ligações

<!--
Apesar da maior parte dos clientes, gerações mais novas, terem a preferência de comunicação assíncrona via texto; Ainda sim a comunicação direta via áudio tem o seu valor (que inclusive no fator de negociação com o cliente pode ser mais eficaz); E ligações, parte dos clientes, colaboradores e farmácias tem preferência em comunicação via telefone, principalmente a área de vendas;
-->

---

# Ligações

Dois fluxos principais:

<v-clicks>

- Empresa Liga para o Cliente
- Cliente Liga para a Empresa

</v-clicks>

<!--
E é por isso que, com o ingresso do suporte a ligações na API oficial do Whatsapp Business, nós desenvolvemos a nossa feature de ligações;

Ligações iniciadas pela Empresa/Farmácia
Requer uma pré-autorização do Cliente
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_1.png'
---

<style lang="postcss">
.slidev-layout, .my-14, .mr-14, .ml-14, .mt-14, .mb-14 {
  background-size: contain !important;
}
</style>

<!--
O Meta impõe esse pré-requisito com intuito de previnir spam e ligações indesejadas. Isto não é algo que é imposto pela Pedido Pago, mas mesmo assim, eu no ponto de vista do cliente, acho uma boa medida para evitar o que acontece na telefonia tradicional, que mesmo estando na lista de não perturbe da Anatel etc, ainda sim recebemos diversas ligações robôs (tem também essa questão de ter muitos golpes)
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_2.png'
---

<!--
Neste slide temos aí no topo o botão de pedir autorização para o cliente.

Este aqui é um exemplo deste fluxo de interação com o cliente via ligação;
* clicar em botão "solicitar permissão";
-->

---
layout: image-right
image: '/temp_fullimg_calls_business_initiated_popup.png'
---

# Empresa -> Cliente
## Pré-autorização via template

<v-clicks>

* Modelo é enviado para o cliente;
* Ele tem a opção de aceitar ou recusar;
* O atendente é notificado após a confirmação;

</v-clicks>

<!--
* template é enviado p/ o cliente (dois botões - aceitar e recusar);
* o cliente irá responder a esta mensagem (ou não, acontece)
* ao receber a confirmação positiva do meta, já iniciamos uma ligação;

como esse processo é async; pode ser que o cliente demore a clicar no botão de aceitar, e o atendente pode estar em outra tela, com outro cliente; 

() neste caso recomendo mostrar um aviso pro atendente resumir esta operação, pra voltar pro contato anterior
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_4.png'
---

<!--
Este é um exemplo; demonstra que após o aceite do cliente, a Empresa
tem até 7 dias para fazer ligações para este cliente, sendo que tem um limite máximo
de 5 ligações por um período de 24h (iniciadas pela empresa)
Ex: a sexta ligação pode ser feita após 24h após a primeira ligação
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_5.png'
---

<!--
Já neste slide podemos ver a ligação sendo iniciada pelo Luis
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_6.png'
---

<!--
E neste cenário o cliente tem até 30 segundos para aceitar ou recusar a ligação
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_7.png'
---

<!--
E neste slide podemos ver que o cliente atendeu a ligação, e também no filtro de ligações em adamento, podemos ver na coluna da esquerda a ligação iniciada pelo Luis
-->

---
layout: image-right
image: '/temp_calls_business_initiated_invite_others.png'
---

# Empresa -> Cliente
## Convidar Atendentes

* Opção de convidar outros colaboradores;

<!--
Existe também a opção de convidar outros colaboradores, e para faciliar o processo,
os especialistas (outros colaboradores já envolvidos neste atendimento)
são listados em primeiro lugar;
-->

---
layout: image-right
image: '/temp_calls_business_initiated_invite_request_modal.png'
---

# Empresa -> Cliente
## Convidar Atendentes

* Colaborador convidado recebe o convite;

<!--
Este é o modal que o colaborador recebe após o atendente clicar no botão de convidar;

Isto é bastante útil no caso de precisar envolver algum especialista neste atendimento e isto traz uma transparência p/ o cliente já que estão todos na mesma linha;
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_8_call_joined_3_ppl.png'
---

<!--
Neste slide podemos ver que nesta ligação de exemplo, o Fernando se juntou ao Luis
e ao cliente
-->

---
layout: image-right
image: '/temp_calls_business_initiated_volume_settings.png'
---

# Empresa -> Cliente
## Opções de Volume

* Opção de ajustar volume de cada ligação;
* Opção de silenciar ligação;

<!--
Não está exemplificado neste slide, mas também será possível bloquear
ligações de clientes específicos no caso de spam;
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_9_calls_history.png'
---

<!--
Este slide mostra o histórico de ligações, e como podemos ver que uma ligação
ainda está em andamento, que é esse item flutuante;

Exemplo de histórico de chamadas, onde será possível escutar, ver transcrição e até o resumo da ligação
-->

---
layout: image-right
image: '/temp_calls_business_initiated_history_actions.png'
---

# Ações no histórico de ligações

* Transcrição completa;
* Deep link para a ligação na thread do contato;

<!--
Em uma ligação com o cliente, já que a Pedido Pago faz a ponte entre o atendente e o cliente (tecnicamente o cliente FB está com uma conexão com a PP, e a PP está com uma conexão com o atendente) existe essa ilusão de estarem compartilhando a mesma conexão, mas o que acontece é que o servidor (no caso a Pedido Pago) retransmite (e mixa) os audios do cliente p/ atendente (e vice versa)

Sendo assim, nada impede que possamos adicionar mais conexões na mesma “sessão”, podemos adicionar mais colaboradores que estão na tela da mensageria, podemos adicionar até terceiros (como sistemas de telefonia (SIP ou webrtc)
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_10_call_completed.png'
---

<!--
Exemplo de como a ligação fica na thread de conversa com o cliente (obs: o cliente não tem essa visualização);
O cliente ve só o que o WhatsApp mostra mesmo;
Neste caso, como foi a última ligação (a que acabou de acontecer, ela fica com a transcrição aparente para dar o contexto da conversa);
-->

---
layout: image
image: '/temp_fullimg_calls_business_initiated_11_new_call_old_call_minimized.png'
---

<!--
E neste slide podemos ver que uma outra ligação foi iniciada, e a última ligação concluída fica minimizada na thread de conversa deste cliente;
-->

---
layout: statement
---

# Ligações de Clientes

---
layout: fact
---

# 100% 
Configurável 🛠️

<!--
Assim como fazer ligações, para receber ligações podemos configurar:

* Se recebemos ligações (ou não)
* Se recebemos ligações 24h/dia ou se seguimos os horários de atendimento
* Se adicionamos os próximos feriados para não ter disponibilidade nestes dias;
* Se desejamos habilitar um botão para o cliente notificar a farmácia para ligar de volta assim que voltar a estar disponível;
-->

---
layout: 3-images
imageLeft: '/temp_calls_client_initiated_whatsapp_details.png'
imageTopRight: '/temp_calls_client_initiated_enable_calls_button.png'
imageBottomRight: '/temp_calls_client_initiated_call_hours.png'
---

<!--
Imagem da esquerda: cliente efetuando uma ligação e as duas últimas são do cliente após permitir que a empresa faça ligações (mostra o período
padrão de 7 dias, mas o cliente tem a possibilidade de editar);

Top right: O que aparece para o cliente quando a empresa habilita o botão de
ligação;

Detalhe: se a empresa optar por não mostrar este botão, a empresa ainda pode
eventualmente aceitar ligações de clientes caso envie templates com o call
to action de ligar para o estabelecimento;

Bottom right: O que aparece para o cliente quando está em um período
que a empresa não pode receber ligações no momento;
-->

---
layout: image
image: '/temp_fullimg_calls_client_initiated_1.png'
---

<!--
Neste exemplo de ligações, os colaboradores diretamente envolvidos com esse cliente, seja de pedidos anteriores ou de uma atribuição recente, serão os primeiros que receberão essa chamada vinda do cliente. Caso nenhum colaborador envolvido esteja online, a chamada será oferecida para os demais atendentes.
-->

---
layout: image
image: '/temp_fullimg_calls_client_initiated_3.png'
---

<!--
E por 'ultimo um slide da ligação que acabou de ser atendida pelo atendente;
-->

---
layout: section
---

# Pré-requisitos

---
layout: bullets
---

* Ter a assinatura de webhooks do módulo de ligações (`calls`)
* Estar no `tier` de 1000 conversas/dia (ou superior)

---
layout: fact
---

# 100%
BSP Disparalha

<!--
Estes dois requerimentos são cobertos para quem tem o a integração via o nosso BSP Disparalha
-->

---

# Integrações Futuras

* Sistemas Tradicionais de Telefonia
* "URA" ou Pré-atendimento
* API para integração via WebRTC

<!--
Já estamos em conversas para integrar a telefonia via WhatsApp
com sistemas tradicionais de telefonia (SIP, VoIP, etc)

Qual o motivo? O motivo é que, no sistema de telefonia geralmente é feito uma distribuição
automática de chamadas, e com a integração será possível aproveitar essa funcionalidade
já existente.

A URA pode ser desde uma mensagem automática (para clientes que ligam fora do horário de atendimento)
até funcionalidades básicas de atendimento.

E por último, temos o objetivo de, assim como fizemos para os ERPs, ter uma API pública
que permita que outros parceiros façam uma integração específica já com essa API que estará disponível.
-->

---
layout: statement
---

# Fim