```mermaid
flowchart TD
    %% Fontes de Entrada
    A1([Preenche formulário<br/>no Site])
    A2([Prospecção Ativa])
    A3([Prospecção Passiva])
    A4([Nova OPP<br/>Cliente existente etc])

    %% Cadastro de Lead
    B1[Cadastra PN como<br/>Lead (Suspect)]
    B2[Cadastra uma Opp<br/>na Etapa de Prospect]
    B3[Prospecção avalia o lead<br/>e preenche o formulário de qualificação]

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B1 --> B2
    B2 --> B3

    %% Decisão Qualificação
    C1{Lead<br/>Qualificado?}
    B3 --> C1

    C1 -- Não --> C2([Descarta Lead])
    C1 -- Sim --> D1[Cria uma Oportunidade<br/>(Cotação) com Status = Posicionado]

    D1 --> D2[Cria uma Tarefa / Agendamento<br/>para equipe de vendas]
    D2 --> D3[Preenchimento dos dados da cotação<br/>/ tratativas com o cliente]

    A4 --> D3

    %% Processo Comercial
    E1[Split por I.E<br/>(filial)]
    E2[Geração do(s) Pedido(s)<br/>Status = "Prometido"]
    E3[Gerente de Picking]
    E4[Emissão de Nota Fiscal<br/>(Status = Ganho)]
    E5([Fim])
    E6[Processo de Produção]

    D3 --> F1[Processo de Precificação]
    F1 --> F2[Emissão da Proposta (Documento)<br/>Status = "Pendente"]
    F2 --> F3[Follow-up e Negociação<br/>com o cliente]

    F3 --> F4{Aceite comercial<br/>pelo cliente?}
    F4 -- Não --> F1
    F4 -- Sim --> F5[Aprovação Financeira]
    F5 --> F6[Aprovação PCP / Sales Ops]
    F6 --> E1

    %% Continuação do Pedido
    E1 --> E2
    E2 --> E6
    E6 --> E3
    E3 --> E4
    E4 --> E5

    %% Perda
    F4 -- Rejeitado --> P1([Perda])
