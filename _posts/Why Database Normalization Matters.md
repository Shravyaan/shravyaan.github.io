---
layout: default
title: 'Why Database Normalization Matters'
---

## Building a Solid Foundation for Data
Today marks a significant shift in my upskilling journey as I moved from general cloud concepts to the specific architecture of data. My main goal was to understand **Database Normalization**, a critical process for designing databases that are efficient, organized, and scalable. I applied these concepts to design a database for an aviation system, which helped me see exactly why "clean data" is so important.

### What I learned 

* **First Normal Form (1NF): ** The journey began with the concept of "Atomicity." I learned that for a table to be in 1NF, every single cell must contain only one value—no lists or comma-separated items are allowed. It forces you to break data down into its smallest parts, ensuring that you don't have repeating groups of data that make searching and sorting impossible.
* **Second Normal Form (2NF): ** This step introduced me to the complexity of "Primary Keys." I learned that to reach 2NF, the table must already be in 1NF and must not have any "partial dependencies." This means that if you have a composite key (two columns that uniquely identify a row), every other column must rely on *both* parts of that key. If a column only relates to one half, it belongs in a different table entirely.
* **Third Normal Form (3NF): ** This was the most rigorous step, focused on removing "transitive dependencies." I learned that a column should not depend on another non-key column. For example, in my airline database, the `City` of an airport depends on the `AirportID`, not directly on the `FlightID`. The rule I’ll always remember is: data must depend on the key, the whole key, and nothing but the key.
* **Applying the Theory: ** I didn't just read about these rules; I put them into practice using a tool called `dbdiagram.io`. I designed a complete schema with three distinct tables—`Aircrafts`, `Airports`, and `Flights`—linking them with foreign keys. This visual exercise showed me how normalization actually reduces redundancy and prevents data anomalies.

So this was my experience with database normalization, and it was fascinating to see how a few strict rules can transform a messy dataset into a robust, professional database structure!
