## ERD-REVISION: Table Design Scenarios (revision)

Lab: docs/day4/erd-revision.md

- Revision activity, reused from DE5M2 Day 1 ("Table Design Scenarios") - not previously used in DA4M3G
- Revises Day 1's ~02-ERD~ theory block - a quick recap of PK/FK and cardinality notation before starting is worth doing if it's been a few days
- Four independent scenarios (Library, Restaurant, Vehicle Hire, Conference) - assign one per group/pair
    - Fewer than 4 groups: drop a scenario rather than doubling one up, so no group finishes early with nothing to compare
    - More than 4 groups: two groups on the same scenario works well - they compare designs at the end
- Groups identify entities, attributes, PK/FK, and relationship cardinality
- Suggested table names are given as a hint, not a full answer
- No tool specified - whiteboard, paper, or a diagramming tool of the trainer's choice
- While circulating, check for the usual slips: a many-to-many left as two 1:M lines with no junction table, missing FK on the "many" side, an attribute that's really its own entity (e.g. Category inside MenuItems)
- Debrief: pick one group per scenario to talk through their design to the room - ask them to justify one relationship's cardinality, not just read out the table list
