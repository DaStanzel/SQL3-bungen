# SQL3 Übungen

# SQL Exercise 09

Under ORACLE, `SET AUTOCOMMIT ON` performs a COMMIT after each SQL statement. This setting is to be switched off for the following exercises with `SET AUTOCOMMIT OFF`. Note that a transaction end must then be explicitly executed by the `COMMIT` command. Perform the following exercises in teams of 2!

1. Create a table `TEST`, give your exercise partner all rights on this table, and insert records together.
2. Try to create a deadlock and see how the system reacts to it.
3. Person A changes a record. Determine at what point in time this change is available to person B.
4. Perform the following processing:

| User A        | User B                                                            |
|---------------|-------------------------------------------------------------------|
| read record A | performs the same action. In addition, one field of this record is changed |
|               | end transaction B                                                 |
| change record A |                                                                  |
| end transaction A |                                                                |

    a) Is this processing sequence feasible?  
    b) Modify the example so that User B changes another record. Consider what locking mechanisms Oracle uses.

5. Determine how the system reacts when both transactions insert the same record (with and without PRIMARY KEY).

6. Reproduce the following situation:

| User A             | User B          |
|--------------------|-----------------|
| update any record  |                 |
|                    | change this record |
| ROLLBACK           |                 |
|                    | COMMIT          |
| change this record |                 |
|                    | read this record|

7. Simulate the Inconsistent Analysis Problem!

| User A         | User B           |
|----------------|------------------|
| Read record A  |                  |
|                | Update record C  |
| read record B  |                  |
|                | Update record A  |
| read Record C  |                  |
|                | COMMIT           |

    Modify the example in such a way that for user A the condition of the data sets A, B, and C of a certain time is indicated!

8. 
    * User A selects a dataset according to a certain criterion.
    * User B changes the criterion according to which the selection was made.
    * User A changes a value in the previously selected dataset.
    
    What happens? What could be done so that between selection and change exactly this selected record cannot be changed by another user?

9. 
    * User B creates a table with a foreign key that references User A's table.
    * User A should now revoke the right that user B can set a reference to his table. Which values can user B insert in the foreign key column afterward?

# SQL Exercise 10

Solve the following tasks alone (each one of you)

## To the tennis club tables
1. Insert a new record in the PLAYERS table (use your own data).
2. Change the value 'F' in the column SEX to 'W'.
3. Increase all penalties above the average by 20%.
4. The player with the number 95 gets the address of the player with the number 6.
5. Delete all penalties of player 44 from 1980.
6. Persist changes from 1-5.
7. Delete all penalties of players who have played at least once in a team of the second division.
8. Undo the deletion from step 7.

## To EMP-DEPT
1. Delete all salaries that are lower than 80% of the average salary of the department, set to 80% of the average salary of the department.
2. Delete all employees who have been with the company for more than 35 years.
3. Create a number sequence with the values 50, 60, 70, 80, ...
4. Insert a new record in the DEPT table with DEPTNO corresponding to the number sequence from step 3, DNAME 'HTL' and LOC 'LEONDING'.
