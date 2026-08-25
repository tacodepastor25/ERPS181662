graph LR
    %% -- PALETA DE COLORES FRÍOS --
    classDef master fill:#475569,stroke:#1e293b,color:#fff,rx:8,ry:8
    classDef presales fill:#06b6d4,stroke:#0891b2,color:#fff,rx:8,ry:8
    classDef order fill:#3b82f6,stroke:#1d4ed8,color:#fff,rx:8,ry:8
    classDef logistics fill:#6366f1,stroke:#4338ca,color:#fff,rx:8,ry:8
    classDef inventory fill:#14b8a6,stroke:#0f766e,color:#fff,rx:8,ry:8
    classDef finance fill:#8b5cf6,stroke:#6d28d9,color:#fff,rx:8,ry:8
    classDef payment fill:#0ea5e9,stroke:#0369a1,color:#fff,rx:8,ry:8

    %% -- NODOS DE DATOS MAESTROS --
    CUST([Customer Master Data])
    ITEM([Item Master Data])

    %% -- PROCESO DE VENTAS --
    SQ["Sales Quotation<br>(Cotización)"]
    SO["Sales Order<br>(Pedido Original - Qty: 10)"]
    
    CUST --> SQ
    ITEM --> SQ
    SQ -->|Accepted| SO

    %% -- DIVISIÓN POR ENTREGA PARCIAL --
    DEL1["Delivery 1<br>(1ra Entrega - Qty: 6)"]
    SO_OPEN{"Sales Order<br>(Status: Open / Backorder)"}
    DEL2["Delivery 2<br>(2da Entrega - Qty: 4)"]

    SO -->|Copy To - Partial Qty| DEL1
    SO -.->|Leaves remaining Qty: 4| SO_OPEN
    SO_OPEN -->|Copy To - Final Qty| DEL2

    %% -- ACTUALIZACIONES DE INVENTARIO --
    INV1[("Stock Decreases<br>(Minus 6)")]
    INV2[("Stock Decreases<br>(Minus 4)")]

    DEL1 -->|Updates| INV1
    DEL2 -->|Updates| INV2

    %% -- FACTURACIÓN --
    ARI1["A/R Invoice 1<br>(Factura 1)"]
    ARI2["A/R Invoice 2<br>(Factura 2)"]

    DEL1 -->|Copy To| ARI1
    DEL2 -->|Copy To| ARI2

    %% -- PAGOS Y CONTABILIDAD --
    IP1["Incoming Payment 1<br>(Pago Recibido)"]
    IP2["Incoming Payment 2<br>(Pago Recibido)"]
    JE[("Journal Entries<br>(Asientos Contables)")]

    ARI1 -->|Paid| IP1
    ARI2 -->|Paid| IP2
    
    IP1 -->|Reconciliation| JE
    IP2 -->|Reconciliation| JE

    %% -- ASIGNACIÓN DE CLASES --
    class CUST,ITEM master
    class SQ presales
    class SO,SO_OPEN order
    class DEL1,DEL2 logistics
    class INV1,INV2 inventory
    class ARI1,ARI2 finance
    class IP1,IP2,JE payment
    %% -- PALETA DE COLORES FRÍOS --
    classDef master fill:#475569,stroke:#1e293b,color:#fff,rx:8,ry:8
    classDef presales fill:#06b6d4,stroke:#0891b2,color:#fff,rx:8,ry:8
    classDef order fill:#3b82f6,stroke:#1d4ed8,color:#fff,rx:8,ry:8
    classDef logistics fill:#6366f1,stroke:#4338ca,color:#fff,rx:8,ry:8
    classDef inventory fill:#14b8a6,stroke:#0f766e,color:#fff,rx:8,ry:8
    classDef finance fill:#8b5cf6,stroke:#6d28d9,color:#fff,rx:8,ry:8
    classDef payment fill:#0ea5e9,stroke:#0369a1,color:#fff,rx:8,ry:8

    %% -- NODOS DE DATOS MAESTROS --
    CUST([Customer Master Data])
    ITEM([Item Master Data])

    %% -- PROCESO DE VENTAS --
    SQ["Sales Quotation<br>(Cotización)"]
    SO["Sales Order<br>(Pedido Original - Qty: 10)"]
    
    CUST --> SQ
    ITEM --> SQ
    SQ -->|Accepted| SO

    %% -- DIVISIÓN POR ENTREGA PARCIAL --
    DEL1["Delivery 1<br>(1ra Entrega - Qty: 6)"]
    SO_OPEN{"Sales Order<br>(Status: Open / Backorder)"}
    DEL2["Delivery 2<br>(2da Entrega - Qty: 4)"]

    SO -->|Copy To - Partial Qty| DEL1
    SO -.->|Leaves remaining Qty: 4| SO_OPEN
    SO_OPEN -->|Copy To - Final Qty| DEL2

    %% -- ACTUALIZACIONES DE INVENTARIO --
    INV1[("Stock Decreases<br>(Minus 6)")]
    INV2[("Stock Decreases<br>(Minus 4)")]

    DEL1 -->|Updates| INV1
    DEL2 -->|Updates| INV2

    %% -- FACTURACIÓN --
    ARI1["A/R Invoice 1<br>(Factura 1)"]
    ARI2["A/R Invoice 2<br>(Factura 2)"]

    DEL1 -->|Copy To| ARI1
    DEL2 -->|Copy To| ARI2

    %% -- PAGOS Y CONTABILIDAD --
    IP1["Incoming Payment 1<br>(Pago Recibido)"]
    IP2["Incoming Payment 2<br>(Pago Recibido)"]
    JE[("Journal Entries<br>(Asientos Contables)")]

    ARI1 -->|Paid| IP1
    ARI2 -->|Paid| IP2
    
    IP1 -->|Reconciliation| JE
    IP2 -->|Reconciliation| JE

    %% -- ASIGNACIÓN DE CLASES --
    class CUST,ITEM master
    class SQ presales
    class SO,SO_OPEN order
    class DEL1,DEL2 logistics
    class INV1,INV2 inventory
    class ARI1,ARI2 finance
    class IP1,IP2,JE payment
