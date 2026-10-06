--- 
title: vw_versions
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_versions
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

Creates, updates, deletes, gets or lists a <code>vw_versions</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_versions" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_versions" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_versions;
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
JSON_EXTRACT(versions, '$.stable') as stable_version,
JSON_EXTRACT(versions, '$.head') as head_version,
CASE 
WHEN JSON_EXTRACT(versions, '$.bottle') = 1 THEN 'true'
ELSE 'false' 
END as bottle_available
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
json_extract_path_text(versions, 'stable') as stable_version,
json_extract_path_text(versions, 'head') as head_version,
CASE 
WHEN json_extract_path_text(versions, 'bottle')::boolean THEN 'true'
ELSE 'false' 
END as bottle_available
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'          
```

</TabItem>
</Tabs>
