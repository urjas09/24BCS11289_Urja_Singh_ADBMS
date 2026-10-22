CREATE TABLE stu (
    student_name VARCHAR(50),
    course_id INT,
    marks INT
);

INSERT INTO stu VALUES
('Aman', 101, 75),
('Riya', 101, 35),
('Karan', 101, 60),
('Neha', 102, 45),
('Rahul', 102, 30),
('Priya', 102, 80);

-- MySQL syntax uses standard views
CREATE VIEW stud_view AS
SELECT student_name, marks
FROM stu;

-- No REFRESH command is needed for a standard view
SELECT * FROM stud_view;