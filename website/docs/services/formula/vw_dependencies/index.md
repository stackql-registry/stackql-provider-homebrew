--- 
title: vw_dependencies
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_dependencies
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

Creates, updates, deletes, gets or lists a <code>vw_dependencies</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_dependencies" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_dependencies" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_dependencies;
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
JSON_EXTRACT(dependencies, '$') as dependencies,
JSON_EXTRACT(head_dependencies, '$') as head_dependencies,
JSON_EXTRACT(build_dependencies, '$') as build_dependencies,
JSON_EXTRACT(test_dependencies, '$') as test_dependencies,
JSON_EXTRACT(optional_dependencies, '$') as optional_dependencies,
JSON_EXTRACT(recommended_dependencies, '$') as recommended_dependencies
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
dependencies::json::text as dependencies,
head_dependencies::json::text as head_dependencies,
build_dependencies::json::text as build_dependencies,
test_dependencies::json::text as test_dependencies,
optional_dependencies::json::text as optional_dependencies,
recommended_dependencies::json::text as recommended_dependencies
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'          
```

</TabItem>
</Tabs>
