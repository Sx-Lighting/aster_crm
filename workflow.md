```mermaid
flowchart TD
    %% Fontes de Entrada
    A1([Preenche formulário<br>no Site])
    A2([Prospecção Ativa])
    A3([Prospecção Passiva])
    A4([Nova OPP - Cliente existente])

    %% Cadastro de Lead
    B1[Cadastra PN como<br>Lead - Suspect]
    B2[Cadastra uma Opp<br>na Etapa de Prospect]
    B3[Prospecção avalia o lead<br>e preenche formulário de qualificação]

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B1 --> B2
    B2 --> B3

    %% Decisão Qualificação
    C1{Lead Qualificado?}
    B3 --> C1

    C1 -- Não --> C2([Descarta Lead])
    C1 -- Sim --> D1[Cria oportunidade - Cotação<br>com status Posicionado]

    D1 --> D2[Cria tarefa / agendamento<br>para equipe de vendas]
    D2 --> D3[Preenchimento da cotação<br>e tratativas com cliente]

    A4 --> D3

    %% Processo Comercial
    E1[Split por IE - filial]
    E2[Geração de pedido - status Prometido]
    E3[Gerente de Picking]
    E4[Emissão de nota fiscal<br>status Ganho]
    E5([Fim])
    E6[Processo de Produção]

    D3 --> F1[Processo de Precificação]
    F1 --> F2[Emissão da proposta<br>status Pendente]
    F2 --> F3[Follow-up e negociação<br>com cliente]

    F3 --> F4{Aceite comercial pelo cliente?}
    F4 -- Não --> F1
    F4 -- Sim --> F5[Aprovação Financeira]
    F5 --> F6[Aprovação PCP e Sales Ops]
    F6 --> E1

    %% Continuação do Pedido
    E1 --> E2
    E2 --> E6
    E6 --> E3
    E3 --> E4
    E4 --> E5

    %% Perda
    F4 -- Rejeitado --> P1([Perda])
