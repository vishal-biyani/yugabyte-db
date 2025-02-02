---
title: COPY
linkTitle: COPY
summary: COPY
description: COPY
menu:
  latest:
    identifier: api-ysql-commands-copy
    parent: api-ysql-commands
aliases:
  - /latest/api/ysql/commands/cmd_copy
isTocNested: true
showAsideToc: true
---

## Synopsis

Use a `COPY` statement to transfer data between tables and files. `COPY TO` copies from tables to files. `COPY FROM` copies from files to tables. `COPY` outputs the number of rows that were copied.

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
    {{% includeMarkdown "../syntax_resources/commands/copy_from,copy_to,copy_option.grammar.md" /%}}
  </div>
  <div id="diagram" class="tab-pane fade" role="tabpanel" aria-labelledby="diagram-tab">
    {{% includeMarkdown "../syntax_resources/commands/copy_from,copy_to,copy_option.diagram.md" /%}}
  </div>
</div>

## Semantics

### _table_name_

Specify the table, optionally schema-qualified, to be copied.

### _column_name_

Specify the list of columns to be copied. If not specified, then all columns of the table will be copied.

### _query_

Specify a `SELECT`, `VALUES`, `INSERT`, `UPDATE`, or `DELETE` statement whose results are to be copied. For `INSERT`, `UPDATE`, and `DELETE` statements, a RETURNING clause must be provided.

### _filename_

Specify the path of the file to be copied. An input file name can be an absolute or relative path, but an output file name must be an absolute path.

## Examples

- Errors are raised if the table does not exist.
- `COPY TO` can only be used with regular tables.
- `COPY FROM` can be used with tables, foreign tables, or views.

