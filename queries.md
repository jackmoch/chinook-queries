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

5. Provide a query showing a unique list of billing countries from the Invoice table.

Select Invoice.BillingCountry from Invoice
Group by Invoice.BillingCountry

6. Provide a query showing the invoices of customers who are from Brazil.

Select * from Invoice
Join Customer on Invoice.CustomerId = Customer.CustomerId
Where Customer.Country = 'Brazil'

7. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name

Select Invoice.*, Employee.FirstName || ' ' || Employee.LastName as 'Full Name' from Invoice
Join Customer on Invoice.CustomerId = Customer.CustomerId
Join Employee on Customer.SupportRepId = Employee.EmployeeId

8. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.

Select Invoice.Total, Customer.FirstName || ' ' || Customer.LastName as 'Customer Name', Employee.FirstName || ' ' || Employee.LastName as 'Employee Name' from Invoice
Join Customer on Invoice.CustomerId = Customer.CustomerId
Join Employee on Customer.SupportRepId = Employee.EmployeeId

9. How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?

Select Count(*) as 'Total Invoices' from Invoice
Where Invoice.InvoiceDate like '%2011%' or Invoice.InvoiceDate like '%2009%'

Select Sum(Invoice.Total) as '2009 Total' from Invoice
Where Invoice.InvoiceDate like '%2009%'

Select Sum(Invoice.Total) as '2011 Total' from Invoice
Where Invoice.InvoiceDate like '%2011%'

10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.

Select Count(*) as 'Total Line Items' from InvoiceLine
Where InvoiceLine.InvoiceId = '37'

11. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. 

Select InvoiceLine.InvoiceId, Count(*) 'Total Lines' from InvoiceLine
Group by InvoiceLine.InvoiceId

12. Provide a query that includes the track name with each invoice line item.

Select Track.Name, InvoiceLine.InvoiceLineId from InvoiceLine
Join Track on InvoiceLine.TrackId = Track.TrackId

13. Provide a query that includes the purchased track name AND artist name with each invoice line item.

Select Track.Name, Artist.Name, InvoiceLine.InvoiceLineId from InvoiceLine
Join Track on InvoiceLine.TrackId = Track.TrackId
Join Album on Track.AlbumId = Album.AlbumId
Join Artist on Album.ArtistId = Artist.ArtistId

14. Provide a query that shows the # of invoices per country.

Select Customer.Country, Count(Invoice.InvoiceId) from Customer
Join Invoice on Customer.CustomerId = Invoice.CustomerId
Group by Customer.Country

15. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resultant table.

Select Count(*) as 'Total Tracks', Playlist.Name from PlaylistTrack
Join Playlist on PlaylistTrack.PlaylistId = Playlist.PlaylistId
Group by PlaylistTrack.PlaylistId

16. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.

Select Track.Name, Album.Title, MediaType.Name, Genre.Name from Track
Join Album on Track.AlbumId = Album.AlbumId
Join MediaType on Track.MediaTypeId = MediaType.MediaTypeId
Join Genre on Track.GenreId = Genre.GenreId