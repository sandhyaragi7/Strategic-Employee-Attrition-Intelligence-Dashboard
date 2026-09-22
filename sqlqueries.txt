create database employee_attritiondb;
use employee_attritiondb;

select * from employee_attrition; 
select count(*) from employee_attrition;

/*Department-level attrition count.*/
select department, count(*) as total_employees,sum(case when attrition ='yes' then 1 else 0 end) as attrition_count from employee_attrition group by department;

/*Baseline wellbeing average*/
select avg(burnout_score), avg(engagement_score), avg(work_life_balance_score) from employee_attrition;

/*NULL/missing-value check.*/
select monthly_income,age from employee_attrition where monthly_income is null or age is null;

/*workload comparison by work mode.*/
select work_mode, avg(overtime_hours_per_week) from employee_attrition group by work_mode;