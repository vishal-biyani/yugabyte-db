---
title: CREATE INDEX
linkTitle: CREATE INDEX
summary: Create index on a table in a database
description: CREATE INDEX
menu:
  latest:
    identifier: api-ysql-commands-create-index
    parent: api-ysql-commands
aliases:
  - /latest/api/ysql/commands/ddl_create_index
isTocNested: true
showAsideToc: true
---

## Synopsis

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
    {{% includeMarkdown "../syntax_resources/commands/create_index,index_elem.grammar.md" /%}}
  </div>
  <div id="diagram" class="tab-pane fade" role="tabpanel" aria-labelledby="diagram-tab">
    {{% includeMarkdown "../syntax_resources/commands/create_index,index_elem.diagram.md" /%}}
  </div>
</div>

## Semantics

`CONCURRENTLY`, `USING method`, `COLLATE`, `NULL` order, and `TABLESPACE` options are not yet supported.

### UNIQUE

Enforce that duplicate values in a table are not allowed.

### INCLUDE clause

Specify a list of columns which will be included in the index as non-key columns.

#### _name_

 Specify the name of the index to be created.

#### _table_name_

Specify the name of the table to be indexed.

#### _column_name_

Specify the name of a column of the table.

#### _expression_

Specify one or more columns of the table and must be surrounded by parentheses.

- `ASC` indicates ascending sort order.
- `DESC` indicates descending sort order.
