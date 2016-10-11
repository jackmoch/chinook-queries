1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

Select Customer.FirstName || ' ' || Customer.LastName as 'Name', Customer.CustomerId, Customer.Country from Customer
Where Customer.Country != 'USA'

