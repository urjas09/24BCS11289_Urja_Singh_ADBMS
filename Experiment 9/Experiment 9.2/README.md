CREATE TABLE employee2 (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR2(100),
    per_hour_salary NUMBER(10,2),
    working_hours NUMBER(10,2),
    payable_amount NUMBER(10,2)
);


INSERT INTO employee2 (emp_id, emp_name, per_hour_salary, working_hours, payable_amount)
VALUES (101, 'Amit', 500, 8, 0);

INSERT INTO employee2 (emp_id, emp_name, per_hour_salary, working_hours, payable_amount)
VALUES (102, 'Rahul', 60, 7, 0);

INSERT INTO employee2 (emp_id, emp_name, per_hour_salary, working_hours, payable_amount)
VALUES (103, 'Priya', 550, 9, 0);



CREATE OR REPLACE TRIGGER trg_cal_payableamt
BEFORE INSERT OR UPDATE ON employee2
FOR EACH ROW
BEGIN
    
    :NEW.payable_amount := :NEW.working_hours * :NEW.per_hour_salary;
    
    IF :NEW.payable_amount > 25000 THEN 
        RAISE_APPLICATION_ERROR(-20003, 'PAYABLE AMOUNT GREATER THAN 25000 NOT ALLOWED');
    END IF;
END;
/



CREATE OR REPLACE TRIGGER trg_print_msg
AFTER INSERT OR UPDATE ON employee2
BEGIN
   
    DBMS_OUTPUT.PUT_LINE('ROWS UPDATED SUCCESSFULLY');
END;
/



UPDATE employee2 SET working_hours = 10 WHERE emp_id = 101;


SELECT * FROM employee2;

