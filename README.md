*----------------------------------------------------------------------*
* Report.....: ZMMR_ESTUPE_INFARMED
* Descrição..: Listagem Obrigatória para artigos Estupefacientes (INFARMED)
* Objetivo...: Gerar listagem anual (ano civil) dos movimentos de entrada/saída
*              de substâncias controladas (mov. 101/201/301), desde a compra
*              ao débito ao utente, para envio ao INFARMED (homologação),
*              com geração de PDF via Adobe Form e envio por e-mail.
*
* Módulos.....: MM / LOG
* Ambiente....: SAP S/4HANA
*
* Entrada.....: P_ANO  - Ano civil (obrigatório)
*
* Saída.......: ALV GRID OO (visualização/filtragem/ordenação)
*              PDF oficial via Adobe Form (SFP) anexado no e-mail.
*
* Regras......: - Considerar movimentos 101 (Entrada), 201 e 301 (Saída) *
*              - "Registo": Req (BANFN) / PO (EBELN) / Doc Material (MBLNR)
*              - "Documento": "Consumo ao doente - <texto>" via MSEG-SGTXT
*              - "Serv./Forn.": Entrada = Fornecedor (EKKO/LFA1);
*                               Saída   = Serviço (centro de custo CSKT)
*              - "Stock": saldo calculado (running balance) por
*                         Material/Centro/Depósito após cada movimento.
*              - Ordenação final: Data (BUDAT), Doc Material, Item.
*
* Adobe Form..: ZAF_ESTUPE_LISTAGEM
* Interface...: ZIF_ESTUPE_LISTAGEM (IS_HEADER / IT_ITEMS)
*
