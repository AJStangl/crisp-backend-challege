# CRISP backend code challenge

## Prerequisites

You will need to have git and [dotnet 6 SDK installed](https://dotnet.microsoft.com/en-us/download/dotnet/6.0). Note that this code will only run on net6 specifically.

## Background 
The purpose of this challenge is to demonstrate one's ability to code up a REST API. The web-application with dotnet run
```cmd
dotnet run src/CRISP.BackendChallenge
```
from the project root. Or Feel free to use any IDE you are comfortable using to run the server.  

Feel free to test out the server to make sure it works and think about how you might want to solve the questions below, 
but please don't start coding up a solution before the scheduled interview time.

Note that we are using Entity Framework as an ORM for this scaffold and that the underlying database in sqlite. The database should be seeded with data on initialization of 
the context.

## Tables
There are two tables in the database `Employee` and `Login`
The sql statement below defines the schema for the two tables (note the relationship):

```sql
```sql
create table Employees
(
    Id         INTEGER not null
        constraint PK_Employees
            primary key autoincrement,
    Name       TEXT    not null,
    Department INTEGER not null
);

create table Logins
(
    Id         INTEGER not null
        constraint PK_Logins
            primary key autoincrement,
    PersonId   INTEGER not null,
    LoginDate  TEXT    not null,
    EmployeeId INTEGER
        constraint FK_Logins_Employees_EmployeeId
            references Employees
);

create index IX_Logins_EmployeeId
    on Logins (EmployeeId);
```

The `Logins` table tracks all of the logins for the people in person.

## Tasks
We already have code for to retrieve all employees as an example with an example to build upon.

Implement The Following For The Employee Controller:
  - Get By Id
  - Create
  - Update by Id
  - Delete by Id
  - Search
    - id
    - name
    - department
    - startDate
    - endDate
    - behavior to include all logins for the employee
    - Sort Order On Login Dates (latest first)

The API should follow general RESTful conventions.


- Implement Unit Test For in the `test\CRISP.BackendChallenge.Tests` folder (if time permits)


## Things We Are Looking For:
1. Ability to understand/constrain the problem
2. Well organized clean code
3. Thoughtful REST endpoints
4. Ability to isolate and debug problems as they arise
5. Familiarity with C#, dotnet, and comfort working within an existing repo
6. Familiarity and comfort writing tests