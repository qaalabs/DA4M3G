# ERD Revision: Table Design Scenarios

Pick one scenario below and design an ERD for it: identify the entities, their attributes, primary keys, foreign keys, and the relationships (with cardinality) between them.

---

## Group A: Library Management System

We need a database to manage our library's books, members, copies, and loans. Each book has an ISBN, title, author, genre, and publication year. For each member we assign a membership number, and we need to store their name, address, and contact number. Each copy represents a physical instance of a book, with a unique barcode, the book it represents, condition status, and shelf location. Finally, loans all have unique IDs, recording which member borrowed which copy, along with the loan date and due date.

*Suggested tables: Books, Members, Copies, Loans*

---

## Group B: Restaurant Reservation System

We need a database to handle our restaurant's menu items, customers, tables, and reservations. Each menu item has a unique code, name, category, price, and description of ingredients. For each customer we create a customer ID, and we need to store their name, phone number, and email address. Each table in the restaurant has a table number, seating capacity, location in the restaurant, and status. Finally, reservations all have unique IDs, specifying which customer has booked which table, along with the date, time, and party size.

*Suggested tables: MenuItems, Customers, Tables, Reservations*

---

## Group C: Vehicle Hire System

We need a database to manage our hire vehicles, clients, bookings, and rental agreements. Each vehicle has a registration number, make, model, vehicle type, and daily hire rate. For each client we assign a client number, and we need to store their name, driving licence number, and contact details. Each booking represents a potential hire with a booking reference, the client making the booking, requested dates, and pickup location. Finally, rental agreements all have unique IDs, linking a confirmed booking to a specific vehicle, with actual pickup date and expected return date.

*Suggested tables: Vehicles, Clients, Bookings, RentalAgreements*

---

## Group D: Conference Management System

We need a database to organise our conferences, delegates, sessions, and registrations. Each conference has a unique code, title, organising body, duration in days, and theme description. For each delegate we allocate a delegate number, and we need to store their name, organisation, and email address. Each session is a presentation within a specific conference, with a session ID, scheduled date/time, the conference it belongs to, and the venue room. Finally, registrations all have unique IDs, recording which delegate is attending which session.

*Suggested tables: Conferences, Delegates, Sessions, Registrations*
