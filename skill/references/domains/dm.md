# Data Modelling & Design — Ch.5 (11%)
| Concept | Testable angle | Common confusions |
|---|---|---|
| Relationship types | Identifying vs non-identifying; recursive; ternary | FK in PK (identifying) vs FK outside PK (non-identifying) |
| Key types | Primary, surrogate, natural, alternate, foreign, candidate, super | Surrogate = source insulation + SCD, not just performance |
| Measure additivity | Additive / semi-additive / non-additive | Snapshots = semi-additive (not summable across time) |
| Normalization | 1NF–5NF, BCNF | 3NF (transitive) vs BCNF (every determinant a candidate key) |
| SCD types | Type 0/1/2/3/6 | SCD1 overwrite vs SCD2 new row+expiry vs SCD3 new column |
| Supertype/subtype | Inheritance of PK; exclusive vs inclusive | Subtype with independent PK |
| Schema styles | Star vs snowflake | Star = denorm/perf; snowflake = normalized |
| Degenerate dimension | Dimension key in fact with no dim table | Junk or role-playing dimension |
| Canonical data model | App-neutral integration model | Logical or physical model |
| Model levels | Conceptual / Logical / Physical | Conceptual = subject areas; logical = entities; physical = tables |
| Notation | IE (crow's foot), UML, Chen, dimensional | Mixing notations |
