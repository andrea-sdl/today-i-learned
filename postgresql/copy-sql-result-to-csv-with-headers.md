# Copy the result of a Postgresql query to a CSV including the headers #

this can be achieved easily with the Copy command

```sql
Copy (
	select field1,field2
	from myschema.example_table
	) 
To '/tmp/example_table.csv' With CSV HEADER;
```

If you don't need a select because you want the full table simply do

```sql
Copy myschema.example_table
To '/tmp/example_table.csv' With CSV HEADER;
```