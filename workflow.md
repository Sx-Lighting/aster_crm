```mermaid
flowchart TD
    %% Fontes de Entrada
    A1([Preenche formulário no Site])
    A2([Prospecção Ativa])
    A3([Prospecção Passiva])
    A4([Nova OPP - Cliente existente])

    %% Cadastro e Qualificação
    B1[Cadastra PN como Lead - Suspect]
    B2[Cadastra Opp na Etapa Prospect]
    B3[Prospecção avalia o lead<br>e preenche o formulário de qualificação]
    B4{Lead Qualificado?}
    B5[Descarta Lead]
    B6[Cria Oportunidade - Cotação<br>com status Posicionado]
    B7[Cria Tarefa ou Agendamento<br>para equipe de vendas]
    B8[Preenchimento dos dados da cotação<br>e tratativas com o cliente]

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B1 --> B2
    B2 --> B3
    B3 --> B4
    B4 -- Não --> B5
    B4 -- Sim --> B6
    B6 --> B7
    B7 --> B8
    A4 --> B8

    %% Processo Comercial
    C1[Processo de Precificação]
    C2[Emissão da Proposta<br>Status Pendente]
    C3[Follow-up e negociação<br>com o cliente]
    C4{Aceite comercial pelo cliente?}
    C5[Perda]
    C6[Aprovação Financeira]
    C7[Aprovação PCP e Sales Opps]

    B8 --> C1
    C1 --> C2
    C2 --> C3
    C3 --> C4
    C4 -- Não --> C5
    C4 -- Sim --> C6
    C6 --> C7

    %% Pedido e Pós-venda
    D1[Split por IE - filial]
    D2[Criação de Pedido como rascunho<br>Status Prometido]
    D3[Confirmação de Pedido oficial<br>Status Prometido]
    D4[Processo de Produção]
    D5[Gerente de Picking]
    D6[Emissão da Nota Fiscal<br>Status Ganho]
    D7([Fim])

    C7 --> D1
    D1 --> D2
    D2 --> D3
    D3 --> D4
    D4 --> D5
    D5 --> D6
    D6 --> D7
