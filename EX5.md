# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
```
CREATE TABLE employee (
  empid INT PRIMARY KEY,
  empname VARCHAR(10),
  dept VARCHAR(10),
  salary DECIMAL(10, 2)
);
```
```
CREATE TABLE salary_log (
  log_id INT AUTO_INCREMENT PRIMARY KEY,
  empid INT,
  empname VARCHAR(10),
  old_salary DECIMAL(10, 2),
  new_salary DECIMAL(10, 2),
  update_date DATE
);
```


### Create employee table:
![image](https://github.com/Jeevithaelumalai/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118708245/9dde44f9-96bc-4799-a063-6ac14d0e27f5)


### Create salary_log table
![image](https://github.com/Jeevithaelumalai/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118708245/3cb2a3cc-d597-4de8-83d9-05ad483724c3)


### PLSQL Trigger code
```
DELIMITER //

CREATE TRIGGER log_salary_update
AFTER UPDATE ON employee
FOR EACH ROW
BEGIN
  INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
  VALUES (OLD.empid, OLD.empname, OLD.salary, NEW.salary, NOW());
END;
//
DELIMITER ;
```
```
UPDATE employee
SET salary = 50000
WHERE empid = 1;
SELECT * FROM employee;
SELECT * FROM salary_log;
```


### Output:
![image](https://github.com/Jeevithaelumalai/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118708245/74165707-2775-4321-9f5e-c5106daeb703)

### Result:
The program has been implemented successfully.
