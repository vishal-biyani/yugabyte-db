---
title: CREATE TABLE
linkTitle: CREATE TABLE
summary: Create a new table in a database
description: CREATE TABLE
menu:
  latest:
    identifier: api-ysql-commands-create-table
    parent: api-ysql-commands
aliases:
  - /latest/api/ysql/ddl_create_table/
isTocNested: true
showAsideToc: true
---

## Synopsis

Use the `CREATE TABLE` statement to create a new table in a database. It defines the table name, column names and types, primary key, and table properties.

## Syntax

<ul class="nav nav-tabs nav-tabs-yb">
  <li >
    <a href="#grammar" class="nav-link active" id="grammar-tab" data-toggle="tab" role="tab" aria-controls="grammar" aria-selected="true">
      <i class="fas fa-file-alt" aria-hidden="true"></i>
      Grammar
    </a>
  </li>
  <li>
    <a href="#diagram" class="nav-link" id="diagram-tab" data-toggle="tab" role="tab" aria-controls="diagram" aria-selected="false">
      <i class="fas fa-project-diagram" aria-hidden="true"></i>
      Diagram
    </a>
  </li>
</ul>

<div class="tab-content">
  <div id="grammar" class="tab-pane fade show active" role="tabpanel" aria-labelledby="grammar-tab">
    {{% includeMarkdown "../syntax_resources/commands/create_table,table_elem,column_constraint,table_constraint,storage_parameter.grammar.md" /%}}
  </div>
  <div id="diagram" class="tab-pane fade" role="tabpanel" aria-labelledby="diagram-tab">
    {{% includeMarkdown "../syntax_resources/commands/create_table,table_elem,column_constraint,table_constraint,storage_parameter.diagram.md" /%}}
  </div>
</div>

## Semantics

- Storage parameters through the `WITH` clause are accepted [for PostgreSQL compatibility](https://www.postgresql.org/docs/11/sql-createtable.html#SQL-CREATETABLE-STORAGE-PARAMETERS), but they will be ignored. The exceptions are `oids=true` and `user_catalog_table=true`, which are explicitly disallowed and will result in an error being thrown.

### _qualified_name_

- An error is raised if `qualified_name` already exists in the specified database.

### _name_

are identifiers (`qualified_name` can be a qualified name).

### _expression_

For DEFAULT keyword must be of the same type as the column it modifies. It must be of type boolean for CHECK constraints.

### _param_name_

Represent storage parameters [as defined by PostgreSQL](https://www.postgresql.org/docs/11/sql-createtable.html#SQL-CREATETABLE-STORAGE-PARAMETERS).

### _param_value_

### PRIMARY KEY

- Currently defining a primary key is required.
- Primary key can be defined in either `column_constraint` or `table_constraint` but not in both of them.
- Each row in a table is uniquely identified by its primary key. 

### FOREIGN KEY

Foreign keys are supported starting v1.2.10.

## Examples

### Table with primary key

```sql
postgres=# CREATE TABLE sample(k1 int, 
                               k2 int, 
                               v1 int, 
                               v2 text, 
                               PRIMARY KEY (k1, k2));
```

### Table with check constraint

```sql
postgres=# CREATE TABLE student_grade (student_id int, 
                                       class_id int, 
                                       term_id int, 
                                       grade int CHECK (grade >= 0 AND grade <= 10), 
                                       PRIMARY KEY (student_id, class_id, term_id));
```

### Table with default value

```sql
postgres=# CREATE TABLE cars (id int PRIMARY KEY, 
                              brand text CHECK (brand in ('X', 'Y', 'Z')), 
                              model text NOT NULL, 
                              color text NOT NULL DEFAULT 'WHITE' CHECK (color in ('RED', 'WHITE', 'BLUE')));
```

### Table with foreign key constraint

```sql
postgres=# create table products(id int primary key, 
                                 descr text);
postgres=# create table orders(id int primary key, 
                               pid int references products(id) ON DELETE CASCADE, 
                               amount int);
```

## See also

[`DROP TABLE`](../ddl_drop_table)
[`ALTER TABLE`](../ddl_alter_table)
[`INSERT`](../dml_insert)
[`SELECT`](../dml_select)
