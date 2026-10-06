--- 
title: vw_info
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_info
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

Creates, updates, deletes, gets or lists a <code>vw_info</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_info" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_info" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_info;
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
full_name,
generated_date,
homepage,
JSON_EXTRACT(versions, '$.stable') as latest_version,
license,
deprecated,
disabled
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
full_name,
generated_date,
--desc as description,
homepage,
json_extract_path_text(versions, 'stable') as latest_version,
license,
deprecated,
disabled
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'          
```

</TabItem>
</Tabs>
