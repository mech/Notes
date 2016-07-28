# Interesting Queries

```sql
SELECT c.key, c.x_key, c.tags
       x.name
FROM context c
JOIN x ON c.x_key = x.key
WHERE c.key = ANY (ARRAY[145545, 223444, 3344443, -- 11,000 other keys --])
  AND c.x_key = 1
  AND c.tags @> ARRAY[E'blah'];
```