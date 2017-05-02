# How to search in array fields #
Nice example, took from a comment in HN that explains how to use arrays to search for multiple components in a record.

Really good example.

Field name
```sql  
  ingredients VARCHAR[]
```

Index

```sql  
  USING GIN (ingredients)
```

search with operator like @>
```sql  
  SELECT * FROM table WHERE ingredients @> ARRAY['mushrooms', 'sour cream']
```

