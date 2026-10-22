CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY,
    Amount NUMBER(12, 2)
);


INSERT INTO Orders VALUES (101, 15000.00);
INSERT INTO Orders VALUES (102, 4500.50);
INSERT INTO Orders VALUES (103, 23500.00);
INSERT INTO Orders VALUES (104, 9999.99);
INSERT INTO Orders VALUES (105, 12000.00);

DECLARE
    CURSOR c_orders IS
        SELECT Order_ID, Amount
        FROM Orders;

    v_order_id Orders.Order_ID%TYPE;
    v_amount   Orders.Amount%TYPE;

BEGIN
    OPEN c_orders;

    LOOP
        FETCH c_orders INTO v_order_id, v_amount;

        EXIT WHEN c_orders%NOTFOUND;

        IF v_amount > 10000 THEN
            DBMS_OUTPUT.PUT_LINE(
                'Order ID: ' || v_order_id || ' - High Value'
            );
        END IF;
    END LOOP;

    CLOSE c_orders;
END;
/
