```mermaid
erDiagram
    Customer ||--o{ Order : "places"
    Customer {
        int ID PK
        string Name
        string PhoneNumber
        string Email
        string Address
    }
    Order ||--o{ OrderItem : "contains"
    Order {
        int ID PK
        int CustomerID FK
        date Date
        time Time
        float TotalPrice
        string Status
    }
    Pizza ||--o{ OrderItem : "included_in"
    Pizza {
        int ID PK
        string Name
        string Description
        float Price
    }
    OrderItem {
        int ID PK
        int OrderID FK
        int PizzaID FK
        int Quantity
        string Customizations
    }
    Payment ||--|| Order : "pays_for"
    Payment {
        int ID PK
        int OrderID FK
        float Amount
        string PaymentMethod
        date PaymentDate
        string PaymentStatus
    }
    Employee ||--o{ Task : "performs"
    Employee {
        int ID PK
        string Name
        string Role
        string ContactNumber
    }
    Task ||--|| Order : "fulfills"
    Task {
        int ID PK
        int OrderID FK
        int EmployeeID FK
        string Description
        time StartTime
        time EndTime
    }
    Ingredient ||--o{ StockOrderDetail : "included_in"
    Ingredient {
        int ID PK
        string Name
        int QuantityInStock
        int ReorderLevel
        int SupplierID FK
    }
    Supplier ||--o{ StockOrder : "supplies"
    Supplier {
        int ID PK
        string Name
        string ContactNumber
        string Email
        string Address
    }
    StockOrder ||--o{ StockOrderDetail : "contains"
    StockOrder {
        int ID PK
        int SupplierID FK
        date Date
        float TotalCost
    }
    StockOrderDetail {
        int ID PK
        int StockOrderID FK
        int IngredientID FK
        int Quantity
        float Price
    }
    Feedback ||--|| Customer : "given_by"
    Feedback {
        int ID PK
        int CustomerID FK
        int OrderID FK
        date Date
        int Rating
        string Comment
    }
    Shift ||--|| Employee : "assigned_to"
    Shift {
        int ID PK
        int EmployeeID FK
        time StartTime
        time EndTime
        date Date
    }
    Delivery ||--|| Order : "delivers"
    Delivery {
        int ID PK
        int OrderID FK
        int DeliveryEmployeeID FK
        time DeliveryStartTime
        time DeliveryEndTime
        string Status
    }
    Vehicle ||--o{ Delivery : "used_for"
    Vehicle {
        int ID PK
        string Type
        string RegistrationNumber
        int DeliveryEmployeeID FK
    }

erDiagram
    Customer ||--o{ Order : "places"
    Order ||--o{ OrderItem : "contains"
    Pizza ||--o{ OrderItem : "included_in"
    Payment ||--|| Order : "pays_for"
    Employee ||--o{ Task : "performs"
    Task ||--|| Order : "fulfills"
    Ingredient ||--o{ StockOrderDetail : "included_in"
    Supplier ||--o{ StockOrder : "supplies"
    StockOrder ||--o{ StockOrderDetail : "contains"
    Feedback ||--|| Customer : "given_by"
    Shift ||--|| Employee : "assigned_to"
    Delivery ||--|| Order : "delivers"
    Vehicle ||--o{ Delivery : "used_for"
