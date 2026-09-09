# ERD Revision: Approach

A quick recap of the process before you start on your scenario.

**Conceptual model**

1. **Identify the entities.** Read the scenario and pick out the nouns that need their own table (e.g. Book, Member).
2. **Plan the relationships.** Work out how entities connect, and the cardinality of each (one-to-many, many-to-many, etc.) - no attributes yet.

**Logical model**

3. **Add the attributes.** For each entity, list the columns it needs to store, then review and refine the column names.
4. **Allocate keys.** Give each entity a primary key, then add foreign keys - on the "many" side for a one-to-many relationship, or via a junction table for many-to-many.

Work through your scenario in this order - don't jump straight to drawing boxes and lines.
