--- 
title: vw_conflicts
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_conflicts
  - formula
  - homebrew
  - infrastructure-as-code
  - configuration-as-data
  - cloud inventory
description: Query, deploy and manage homebrew resources using SQL
custom_edit_url: null
image: /img/stackql-homebrew-provider-featured-image.png
---

import CopyableCode from '@site/src/components/CopyableCode/CopyableCode';
import CodeBlock from '@theme/CodeBlock';
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Creates, updates, deletes, gets or lists a <code>vw_conflicts</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_conflicts" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_conflicts" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_conflicts;
```

## SQL Definition

<Tabs
defaultValue="Sqlite3"
values={[
{ label: 'Sqlite3', value: 'Sqlite3' },
{ label: 'Postgres', value: 'Postgres' }
]}
>
<TabItem value="Sqlite3">

```sql
SELECT
name as formula_name,
JSON_EXTRACT(conflicts_with, '$') as conflicts_with,
JSON_EXTRACT(conflicts_with_reasons, '$') as conflicts_with_reasons
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
conflicts_with::json::text as conflicts_with,
conflicts_with_reasons::json::text as conflicts_with_reasons
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'          
```

</TabItem>
</Tabs>
