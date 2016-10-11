1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

Select Customer.FirstName || ' ' || Customer.LastName as 'Name', Customer.CustomerId, Customer.Country from Customer
Where Customer.Country != 'USA'

2. Provide a query only showing the Customers from Brazil.

Select * from Customer
Where Customer.Country = 'Brazil'

3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.

Select Customer.FirstName || ' ' || Customer.LastName as 'Name', Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry from Customer
Join Invoice on Customer.CustomerId = Invoice.CustomerId

4. Provide a query showing only the Employees who are Sales Agents.

Select * from Employee
Where Employee.Title = 'Sales Support Agent'