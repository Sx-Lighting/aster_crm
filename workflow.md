```mermaid
flowchart TD
    %% Início da Prospecção
    A1([Preenche formulário no Site])
    A2([Prospecção Ativa])
    A3([Prospecção Passiva])
    B1[Cadastra PN como Lead]
    B2[Cadastra uma Opp de Vendas na Etapa de Prospect]

    A1 --> B1
    A2 --> B1
    A3 --> B1
    B1 --> B2

    %% Decisão: Lead Qualificado
    C1{Lead Qualificado?}
    B2 --> C1

    C1 -- Não --> C2[Descarta OPP]

    C1 -- Sim --> D1[Alteração da Responsabilidade para Time de Vendas]
    D1 --> D2[Preenchimento dos dados da cotação]
    D2 --> D3[Altera o status para "Posicionado"]

    %% Entrada alternativa: Nova OPP
    A4([Nova OPP<br/>(Cliente existente etc)])
    A4 --> D2

    %% Processo de Proposta
    E1[Processo de Precificação]
    E2[Emissão da Proposta<br/>(Documento)]
    E3[Follow-up e<br/>Negociação com o cliente]
    E4{Aceite comercial<br/>pelo cliente?}
    E5[Altera o status<br/>para "Pendente"]

    D3 --> E1
    E1 --> E2
    E2 --> E3
    E3 --> E5
    E5 --> E4

    E4 -- Não --> E1
    E4 -- Sim --> F1[Aprovação Sales Ops]
    F1 --> F2[Aprovação Financeira]
    F2 --> F3[Aprovação PCP]

    %% Processo de Pedido
    G1[Split por I.E<br/>(filial)]
    G2[Geração de Pedido de Vendas]
    G3[Altera o status<br/>para "Prometido"]
    G4[Processo de Produção]
    G5[Gerente de Picking]
    G6[Emissão de Nota Fiscal]
    G7[Altera o status no funil<br/>para "Ganho"]
    G8([Fim])

    F3 --> G1
    G1 --> G2
    G2 --> G3
    G3 --> G4
    G4 --> G5
    G5 --> G6
    G6 --> G7
    G7 --> G8
