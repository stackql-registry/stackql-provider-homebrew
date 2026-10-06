--- 
title: vw_urls
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_urls
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

Creates, updates, deletes, gets or lists a <code>vw_urls</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_urls" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_urls" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_urls;
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
homepage,
JSON_EXTRACT(urls, '$.stable.url') as stable_url,
JSON_EXTRACT(urls, '$.stable.tag') as stable_tag,
JSON_EXTRACT(urls, '$.stable.revision') as stable_revision,
JSON_EXTRACT(urls, '$.stable.using') as stable_using,
JSON_EXTRACT(urls, '$.stable.checksum') as stable_checksum,
JSON_EXTRACT(urls, '$.head.url') as head_url,
JSON_EXTRACT(urls, '$.head.branch') as head_branch,
JSON_EXTRACT(urls, '$.head.using') as head_using
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
homepage,
json_extract_path_text(urls, 'stable', 'url') as stable_url,
json_extract_path_text(urls, 'stable', 'tag') as stable_tag,
json_extract_path_text(urls, 'stable', 'revision') as stable_revision,
json_extract_path_text(urls, 'stable', 'using') as stable_using,
json_extract_path_text(urls, 'stable', 'checksum') as stable_checksum,
json_extract_path_text(urls, 'head', 'url') as head_url,
json_extract_path_text(urls, 'head', 'branch') as head_branch,
json_extract_path_text(urls, 'head', 'using') as head_using
FROM
homebrew.formula.formula
WHERE formula_name = 'stackql'
```

</TabItem>
</Tabs>
