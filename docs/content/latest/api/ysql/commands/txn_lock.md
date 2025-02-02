---
title: LOCK
linkTitle: LOCK
summary: Lock a table
description: LOCK
menu:
  latest:
    identifier: api-ysql-commands-lock
    parent: api-ysql-commands
aliases:
  - /latest/api/ysql/commands/txn_lock
isTocNested: true
showAsideToc: true
---

## Synopsis

Use the `LOCK` statement to lock a table.

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
    {{% includeMarkdown "../syntax_resources/commands/lock_table,lockmode.grammar.md" /%}}
  </div>
  <div id="diagram" class="tab-pane fade" role="tabpanel" aria-labelledby="diagram-tab">
    {{% includeMarkdown "../syntax_resources/commands/lock_table,lockmode.diagram.md" /%}}
  </div>
</div>

## Semantics

### _name_

Specify an existing table to lock.

### _lockmode_

- Only `ACCESS SHARE` lock mode is supported at this time.
- All other modes listed in _lockmode_ are under development.

## See also

- [`SET TRANSACTION`](../txn_set)
