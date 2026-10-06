--- 
title: vw_usage_metrics
hide_title: false
hide_table_of_contents: false
keywords:
  - vw_usage_metrics
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

Creates, updates, deletes, gets or lists a <code>vw_usage_metrics</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="vw_usage_metrics" /></td></tr>
<tr><td><b>Type</b></td><td>View</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.vw_usage_metrics" /></td></tr>
</tbody></table>

## Fields

See the SQL Definition (view DDL) for fields returned by this view.

## `SELECT` Examples

```sql
SELECT
  *
FROM homebrew.formula.vw_usage_metrics;
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
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install.30d'), '$.' || formula_name) as installs_30d,
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install.90d'), '$.' || formula_name) as installs_90d,
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install.365d'), '$.' || formula_name) as installs_365d,
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install_on_request.30d'), '$.' || formula_name) as install_on_requests_30d,
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install_on_request.90d'), '$.' || formula_name) as install_on_requests_90d,
JSON_EXTRACT(JSON_EXTRACT(analytics, '$.install_on_request.365d'), '$.' || formula_name) as install_on_requests_365d	
FROM
homebrew.formula.formula
WHERE formula_name IN ('stackql')
```

</TabItem>
<TabItem value="Postgres">

```sql
SELECT
name as formula_name,
json_extract_path_text(json_extract_path_text(analytics, 'install', '30d'), formula_name) as installs_30d,
json_extract_path_text(json_extract_path_text(analytics, 'install', '90d'), formula_name) as installs_90d,
json_extract_path_text(json_extract_path_text(analytics, 'install', '365d'), formula_name) as installs_365d,
json_extract_path_text(json_extract_path_text(analytics, 'install_on_request', '30d'), formula_name) as install_on_requests_30d,
json_extract_path_text(json_extract_path_text(analytics, 'install_on_request', '90d'), formula_name) as install_on_requests_90d,
json_extract_path_text(json_extract_path_text(analytics, 'install_on_request', '365d'), formula_name) as install_on_requests_365d
FROM
homebrew.formula.formula
WHERE formula_name IN ('stackql')
```

</TabItem>
</Tabs>
