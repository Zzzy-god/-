-- 供应商表
CREATE TABLE Supplier (
    supplier_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    contact VARCHAR(50),
    phone VARCHAR(20),
    address VARCHAR(200),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 出库单（主表）
CREATE TABLE OutboundOrder (
    outbound_id INT PRIMARY KEY AUTO_INCREMENT,
    outbound_date DATE NOT NULL,
    purpose VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 借还记录表
CREATE TABLE BorrowReturn (
    borrow_id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    borrower VARCHAR(50) NOT NULL,
    borrow_date DATE NOT NULL,
    return_date DATE,
    FOREIGN KEY (product_id) REFERENCES Product(product_id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 索引优化（出入库查询）
CREATE INDEX idx_inbound_date ON InboundOrder(inbound_date);
CREATE INDEX idx_outbound_date ON OutboundOrder(outbound_date);
