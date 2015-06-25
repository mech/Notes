# SQL

## Transaction Phenomena

|           Mode           |                                                                                      Description                                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| P0 (Dirty Write)         | T1 modifies data and T2 also modifies same data before T1 COMMIT/ROLLBACK. Violate consistency. ACID database don't even allow Dirty Write                                            |
| P1 (Dirty Read)          | T1 modifies data and T2 then read the data before T1 COMMIT. If T1 instead ROLLBACK, T2 will have a Dirty Read. (Uncommitted dependency)                                              |
| P2 (Non-repeatable Read) | T1 read a row, then T2 delete that row. T1 no longer can repeat that same read. Same as Dirty Read just that row was committed. (Inconsistent analysis)                               |
| P3 (Phantom)             | Same as non-repeatable read. T1 read a row using same SELECT, T2 insert/delete row that affect that same SELECT result.                                                               |
| P4 (Lost Update)         | T1 read a row, then T2 read the same row. T1 update the row and T2 update it also. T2 won but result in lost update that T1 made. (Lost or buried updates). Solved by 2-phase locking |

* [Editor example](https://technet.microsoft.com/en-us/library/aa213029(v=sql.80).aspx)

To combat these concurrency problem we need **concurrency control** through some **isolation level**.



`DELETE` is a row-level action. `DROP TABLE` is a schema-level action.

## Constraints

```sql
ALTER TABLE users ADD CONSTRAINT email_uniqueness UNIQUE (email);
ALTER TABLE users ADD CONSTRAINT email_uniqueness UNIQUE (email, account_id);

ALTER TABLE users ADD CONSTRAINT email_presence CHECK (char_length(email) > 0);

-- If someone remove company, we remove positions also
ALTER TABLE positions ADD CONSTRAINT positions_fk_company
FOREIGN KEY (company_id) REFERENCES companies(id)
ON DELETE CASCADE
```