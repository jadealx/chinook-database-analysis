# Chinook Database Analysis

## Overview

This repository contains the Chinook database, a sample database used for learning and demonstration purposes. The database simulates a digital media store, including tables related to artists, albums, customers, employees, invoices, tracks, and more.

## Files Included

- **chinook_database.sql**: This SQL file contains the schema and data for the Chinook database. It can be used to recreate the database schema and populate it with sample data.

## Analysis Performed

The following analyses have been conducted on the Chinook database:

1. **Customers Outside the US**:
   - Identified customers who are not located in the US.
   - **Query**:
     ```sql
     SELECT FirstName || ' ' || LastName AS FullName, CustomerId, Country
     FROM customers
     WHERE Country <> 'USA';
     ```

2. **Invoices by Sales Agents**:
   - Displayed invoices associated with each sales agent, including the agent's full name.
   - **Query**:
     ```sql
     SELECT e.FirstName || ' ' || e.LastName AS SalesAgentName, i.InvoiceId, i.InvoiceDate
     FROM invoices i
     JOIN employees e ON i.BilledTo = e.EmployeeId;
     ```

3. **Unique Billing Countries**:
   - Retrieved a distinct list of billing countries from the invoices.
   - **Query**:
     ```sql
     SELECT DISTINCT BillingCountry
     FROM invoices;
     ```

4. **Total Sales by Sales Agents**:
   - Calculated the total sales made by each sales agent.
   - **Query**:
     ```sql
     SELECT e.FirstName || ' ' || e.LastName AS SalesAgentName, SUM(i.Total) AS TotalSales
     FROM invoices i
     JOIN employees e ON i.BilledTo = e.EmployeeId
     GROUP BY SalesAgentName;
     ```

5. **Total Sales for 2009**:
   - Determined the total sales for the year 2009.
   - **Query**:
     ```sql
     SELECT SUM(Total) AS TotalSales2009
     FROM invoices
     WHERE strftime('%Y', InvoiceDate) = '2009';
     ```

## How to Use

1. **Download**:
   - Download the `chinook_database.sql` file from this repository.

2. **Import**:
   - Use a SQL management tool (like SQLite Studio) to import the SQL file into your database system.

3. **Analyze**:
   - Execute the provided SQL queries to perform analysis on the data.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The Chinook database is provided by [Chinook Database](https://github.com/lerocha/chinook-database).
- Thanks to [SQLite Studio](https://sqlitestudio.pl/) for the database management tool used for this project.

