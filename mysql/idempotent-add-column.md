# Creating an Idempotent way to add column to a table #

I recently needed to add a sql that could be executed over and over so we needed it to be idempotent.
a nice way is to use a stored procedure in the sql, you can delete it by the end of the script or leave it like that.

The procedure is
```sql
DROP procedure IF EXISTS `add_column_if_not_present`;
DELIMITER $$
CREATE PROCEDURE `add_column_if_not_present`(IN tableName varchar(100),IN columnName varchar(100),IN columnType varchar(100))
BEGIN
	IF NOT EXISTS ((SELECT * FROM information_schema.columns WHERE table_schema=DATABASE() AND table_name=tableName AND column_name=columnName)) THEN
		SET @sqlToExec =
			CONCAT('ALTER TABLE ', tableName, ' ADD COLUMN `',columnName,'` ',columnType);
		PREPARE stmt FROM @sqlToExec;
		EXECUTE stmt;
	END IF;
END
$$
DELIMITER ;
```

notice that the schema is automatically derived by the default schema in the connection. I didn't want it to be written in the sql as schemas might change name depending on the server you are in.

To add a column then you use.

```sql
CALL add_column_if_not_present('TABLE_NAME' ,'COLUMN_NAME','VARCHAR(250)')
```

you can even add other information to the columnType (for example null/not null or "AFTER" keyword) since it's being postfixed.