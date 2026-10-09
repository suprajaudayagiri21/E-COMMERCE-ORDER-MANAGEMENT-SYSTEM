-- E-Commerce Order Management System
-- SQL schema extracted from the uploaded capstone documentation.
-- Note: Syntax may need minor adjustment depending on your SQL platform.

CREATE TABLE Customer (
    CustomerID INTEGER PRIMARY KEY,
    FirstName VARCHAR(30) NOT NULL,
    LastName VARCHAR(30) NOT NULL,
    Email VARCHAR(100) NOT NULL UNIQUE,
    Phone VARCHAR(15) NOT NULL,
    Address VARCHAR(150) NOT NULL,
    CreatedAt DATE DEFAULT CURRENT_DATE
);

CREATE TABLE Product (
    ProductID INTEGER PRIMARY KEY,
    ProductName VARCHAR(100) NOT NULL,
    Category VARCHAR(50) NOT NULL,
    Price DECIMAL(10,2) NOT NULL CHECK (Price > 0),
    StockQuantity INTEGER NOT NULL DEFAULT 0 CHECK (StockQuantity >= 0),
    Status VARCHAR(20) NOT NULL DEFAULT 'Available'
);

CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    CustomerID INTEGER NOT NULL,
    OrderDate DATE DEFAULT CURRENT_DATE,
    TotalAmount DECIMAL(12,2) NOT NULL CHECK (TotalAmount >= 0),
    OrderStatus VARCHAR(20) NOT NULL DEFAULT 'Pending',
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID)
);

CREATE TABLE OrderItem (
    OrderItemID INTEGER PRIMARY KEY,
    OrderID INTEGER NOT NULL,
    ProductID INTEGER NOT NULL,
    Quantity INTEGER NOT NULL CHECK (Quantity > 0),
    UnitPrice DECIMAL(10,2) NOT NULL CHECK (UnitPrice > 0),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Product(ProductID)
);

CREATE TABLE Payment (
    PaymentID INTEGER PRIMARY KEY,
    OrderID INTEGER NOT NULL,
    PaymentDate DATE DEFAULT CURRENT_DATE,
    Amount DECIMAL(12,2) NOT NULL CHECK (Amount > 0),
    PaymentMethod VARCHAR(30) NOT NULL,
    PaymentStatus VARCHAR(20) NOT NULL DEFAULT 'Pending',
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

CREATE TABLE Shipment (
    ShipmentID INTEGER PRIMARY KEY,
    OrderID INTEGER NOT NULL,
    TrackingNumber VARCHAR(50) UNIQUE,
    ShippingAddress VARCHAR(200) NOT NULL,
    ShipmentDate DATE,
    DeliveryDate DATE,
    DeliveryStatus VARCHAR(30) NOT NULL DEFAULT 'Processing',
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
