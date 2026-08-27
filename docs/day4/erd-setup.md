# ERD Revision: Approach

A quick recap of the process before you start on your scenario.

1. **Identify the entities.** Read the scenario and pick out the nouns that need their own table (e.g. Book, Member).
2. **Identify the attributes.** For each entity, list the pieces of data it needs to store.
3. **Identify the primary key.** Pick (or add) the attribute that uniquely identifies each row.
4. **Identify the relationships.** Work out how entities connect, and the cardinality of each (one-to-many, many-to-many, etc.).
5. **Add the foreign keys.** For a one-to-many relationship, the FK goes on the "many" side. For a many-to-many relationship, add a junction table.

Work through your scenario in this order - don't jump straight to drawing boxes and lines.
