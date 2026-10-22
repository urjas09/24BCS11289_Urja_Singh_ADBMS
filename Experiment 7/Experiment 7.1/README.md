CREATE TABLE stu (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    course_id INT,
    marks INT
);


INSERT INTO stu VALUES (1, 'Aman', 101, 75);
INSERT INTO stu VALUES (2, 'Riya', 101, 35);
INSERT INTO stu VALUES (3, 'Karan', 101, 60);
INSERT INTO stu VALUES (4, 'Neha', 102, 45);
INSERT INTO stu VALUES (5, 'Rahul', 102, 30);
INSERT INTO stu VALUES (6, 'Priya', 102, 80);


DECLARE
    CURSOR c_staff IS
        SELECT student_name, marks
        FROM stu
        ORDER BY marks DESC
        FETCH FIRST 5 ROWS ONLY;
        
    v_name stu.student_name%TYPE;
    v_salary stu.marks%TYPE;
BEGIN
    OPEN c_staff;
    
    LOOP
        FETCH c_staff INTO v_name, v_salary;
        
        EXIT WHEN c_staff%NOTFOUND;
        
        DBMS_OUTPUT.PUT_LINE(
            'Name: ' || v_name || ' Salary: ' || v_salary
        );
    END LOOP;
    
    CLOSE c_staff;
END;
/
