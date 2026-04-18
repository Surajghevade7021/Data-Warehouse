flowchart LR

%% ========================
%% DIMENSIONS
%% ========================
subgraph Dimensions
    D1[dim_lead]
    D2[dim_user]
    D3[dim_subproduct]
    D4[dim_lead_substatus]
    D5[dim_activity_type]
    D6[dim_comment]
    D7[dim_location]
    D8[dim_pool]
    D9[dim_question]
    D10[dim_common_object]
end

%% ========================
%% FACTS
%% ========================
subgraph Facts
    F1[fact_lead_profiling]
    F2[fact_lead_events]
    F3[fact_activity]
    F4[fact_call_activity]
    F5[fact_follow_up]
    F6[fact_onboarding]
    F7[fact_payment]
    F8[fact_installment]
    F9[fact_refund]
    F10[fact_status_events]
    F11[fact_pool_lead]
    F12[fact_lead_response]
end

%% ========================
%% BRIDGES
%% ========================
subgraph Bridges
    B1[bridge_lead_subproduct]
    B2[bridge_user_subproduct]
    B3[bridge_payment_installment]
    B4[bridge_ticket_recipient]
    B5[fact_contact_mapping]
end

%% ========================
%% AGGREGATES
%% ========================
subgraph Aggregates
    A1[agg_sales_summary]
    A2[fact_marketing_cost]
    A3[fact_financial_txns]
    A4[fact_call_analysis]
end

%% ========================
%% RELATIONSHIPS
%% ========================

D1 --> F1
D2 --> F1
D3 --> F6
D4 --> F10
D5 --> F3
D7 --> F4
D8 --> F11
D9 --> F12

F6 --> F7
F7 --> F8
F7 --> F9

F1 --> B1
F2 --> B5
F6 --> B3

F1 --> A1
F7 --> A3
F4 --> A4
F3 --> A2
