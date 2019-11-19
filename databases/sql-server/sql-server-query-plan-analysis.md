# SQL Server: Query Plan Analysis
https://app.pluralsight.com/library/courses/sqlserver-query-plan-analysis

## Course Introduction
- View query execution plan to review a query's performance issues
- Understand what a query execution plan can and cannot tell you
- Covers: capturing execution plans, interpreting execution plans and identifying patterns in plan shapes that can inform performance tuning steps

## Why Do We Care About QPs?
- T-SQL is a declarative language (WHAT not HOW)
- Query plans tell you HOW results are being retrieved potential optimisations
- Query plans help triage and address most impactful areas

## What Doesn't A QP Tell Us?
- Locks
- Wait stats
- Data caching (or not)
- Actual vs estimated cost
- Not a replacement for `SET STATISTICS IO` or `SET STATISTICS TIME`

## Course Structure
- Capturing Query Execution Plans
- Interpreting Query Execution Plans
- Common Operators
- Noteworthy Patterns

