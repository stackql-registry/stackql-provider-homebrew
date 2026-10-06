--- 
title: formula
hide_title: false
hide_table_of_contents: false
keywords:
  - formula
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

Creates, updates, deletes, gets or lists a <code>formula</code> resource.

## Overview
<table><tbody>
<tr><td><b>Name</b></td><td><CopyableCode code="formula" /></td></tr>
<tr><td><b>Type</b></td><td>Resource</td></tr>
<tr><td><b>Id</b></td><td><CopyableCode code="homebrew.formula.formula" /></td></tr>
</tbody></table>

## Fields

The following fields are returned by `SELECT` queries:

<Tabs
    defaultValue="get_formula"
    values={[
        { label: 'get_formula', value: 'get_formula' }
    ]}
>
<TabItem value="get_formula">

A JSON object containing the formula details.

<table>
<thead>
    <tr>
    <th>Name</th>
    <th>Datatype</th>
    <th>Description</th>
    </tr>
</thead>
<tbody>
<tr>
    <td><CopyableCode code="name" /></td>
    <td><code>string</code></td>
    <td>The name of the formula.</td>
</tr>
<tr>
    <td><CopyableCode code="full_name" /></td>
    <td><code>string</code></td>
    <td>The full, qualified name of the formula including the tap name (if applicable).</td>
</tr>
<tr>
    <td><CopyableCode code="aliases" /></td>
    <td><code>array</code></td>
    <td>Alternative names or aliases for the formula.</td>
</tr>
<tr>
    <td><CopyableCode code="analytics" /></td>
    <td><code>object</code></td>
    <td>Analytics data related to the formula, such as download counts or build errors. </td>
</tr>
<tr>
    <td><CopyableCode code="bottle" /></td>
    <td><code>object</code></td>
    <td>Details about the precompiled binary packages (bottles) for the formula, including URLs and checksums. </td>
</tr>
<tr>
    <td><CopyableCode code="build_dependencies" /></td>
    <td><code>array</code></td>
    <td>Dependencies required to build the formula from source. </td>
</tr>
<tr>
    <td><CopyableCode code="caveats" /></td>
    <td><code>string</code></td>
    <td>Special instructions or warnings about the formula that users should be aware of. </td>
</tr>
<tr>
    <td><CopyableCode code="conflicts_with" /></td>
    <td><code>array</code></td>
    <td>Formula names that conflict with this formula, meaning they cannot be installed simultaneously. </td>
</tr>
<tr>
    <td><CopyableCode code="conflicts_with_reasons" /></td>
    <td><code>array</code></td>
    <td>Reasons why the formula conflicts with other formulae. </td>
</tr>
<tr>
    <td><CopyableCode code="dependencies" /></td>
    <td><code>array</code></td>
    <td>Dependencies required to run the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="deprecated" /></td>
    <td><code>boolean</code></td>
    <td>Whether the formula is deprecated, meaning it is no longer supported or maintained. </td>
</tr>
<tr>
    <td><CopyableCode code="deprecation_date" /></td>
    <td><code>string</code></td>
    <td>The date on which the formula was deprecated, if it is deprecated. </td>
</tr>
<tr>
    <td><CopyableCode code="deprecation_reason" /></td>
    <td><code>string</code></td>
    <td>The reason why the formula was deprecated, if it is deprecated. </td>
</tr>
<tr>
    <td><CopyableCode code="desc" /></td>
    <td><code>string</code></td>
    <td>A short description of the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="disable_date" /></td>
    <td><code>string</code></td>
    <td>The date on which the formula was disabled, if it is disabled. </td>
</tr>
<tr>
    <td><CopyableCode code="disable_reason" /></td>
    <td><code>string</code></td>
    <td>The reason why the formula was disabled, if it is disabled. </td>
</tr>
<tr>
    <td><CopyableCode code="disabled" /></td>
    <td><code>boolean</code></td>
    <td>Whether the formula is disabled, meaning it is not available to install or use. </td>
</tr>
<tr>
    <td><CopyableCode code="generated_date" /></td>
    <td><code>string (date)</code></td>
    <td>The date when the formula information was last generated or updated. </td>
</tr>
<tr>
    <td><CopyableCode code="head_dependencies" /></td>
    <td><code>object</code></td>
    <td>Dependencies required for installing the HEAD version (directly from the source repository). </td>
</tr>
<tr>
    <td><CopyableCode code="homepage" /></td>
    <td><code>string</code></td>
    <td>URL to the formula's homepage or project page. </td>
</tr>
<tr>
    <td><CopyableCode code="installed" /></td>
    <td><code>array</code></td>
    <td>Versions of the formula that are currently installed. </td>
</tr>
<tr>
    <td><CopyableCode code="keg_only" /></td>
    <td><code>boolean</code></td>
    <td>Whether the formula is keg-only, meaning it is not symlinked into the Homebrew prefix and can be accessed only by its fully qualified name. </td>
</tr>
<tr>
    <td><CopyableCode code="keg_only_reason" /></td>
    <td><code>string</code></td>
    <td>The reason why the formula is keg-only, if it is keg-only. </td>
</tr>
<tr>
    <td><CopyableCode code="license" /></td>
    <td><code>string</code></td>
    <td>The license under which the formula is distributed. </td>
</tr>
<tr>
    <td><CopyableCode code="link_overwrite" /></td>
    <td><code>array</code></td>
    <td>File paths that this formula might request to overwrite during installation. </td>
</tr>
<tr>
    <td><CopyableCode code="linked_keg" /></td>
    <td><code>string</code></td>
    <td>The version of the formula that is currently linked into Homebrews prefix. </td>
</tr>
<tr>
    <td><CopyableCode code="oldname" /></td>
    <td><code>string</code></td>
    <td>Previous name for the formula, if it was renamed.</td>
</tr>
<tr>
    <td><CopyableCode code="oldnames" /></td>
    <td><code>array</code></td>
    <td>All previous names the formula had.</td>
</tr>
<tr>
    <td><CopyableCode code="optional_dependencies" /></td>
    <td><code>array</code></td>
    <td>Dependencies that are optional, meaning they are not required to run the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="options" /></td>
    <td><code>array</code></td>
    <td>Options that can be passed to the formula when installing it. </td>
</tr>
<tr>
    <td><CopyableCode code="outdated" /></td>
    <td><code>boolean</code></td>
    <td>Whether the formula is outdated, meaning a newer version is available. </td>
</tr>
<tr>
    <td><CopyableCode code="pinned" /></td>
    <td><code>boolean</code></td>
    <td>Whether the formula is pinned, meaning it is not upgraded when running `brew upgrade`. </td>
</tr>
<tr>
    <td><CopyableCode code="post_install_defined" /></td>
    <td><code>boolean</code></td>
    <td>Whether a post-installation script is defined for the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="recommended_dependencies" /></td>
    <td><code>array</code></td>
    <td>Dependencies that are recommended, meaning they are not required to run the formula but are suggested for additional functionality. </td>
</tr>
<tr>
    <td><CopyableCode code="requirements" /></td>
    <td><code>array</code></td>
    <td>Non-formula requirements for the formula, such as specific hardware or software conditions. </td>
</tr>
<tr>
    <td><CopyableCode code="revision" /></td>
    <td><code>integer</code></td>
    <td>The package revision number, used for versioning beyond the version number. </td>
</tr>
<tr>
    <td><CopyableCode code="ruby_source_checksum" /></td>
    <td><code>object</code></td>
    <td>Checksum details for the Ruby source code of the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="ruby_source_path" /></td>
    <td><code>string</code></td>
    <td>The file path to the Ruby source code of the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="service" /></td>
    <td><code>object</code></td>
    <td>Details if the formula can run as a service or background process. </td>
</tr>
<tr>
    <td><CopyableCode code="tap" /></td>
    <td><code>string</code></td>
    <td>The GitHub repository (tap) where the formula is located.</td>
</tr>
<tr>
    <td><CopyableCode code="tap_git_head" /></td>
    <td><code>string</code></td>
    <td>The latest commit SHA of the tap repository containing the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="test_dependencies" /></td>
    <td><code>array</code></td>
    <td>Dependencies required for running the formulas tests. </td>
</tr>
<tr>
    <td><CopyableCode code="urls" /></td>
    <td><code>object</code></td>
    <td>URLs related to the formula, such as the source URL. </td>
</tr>
<tr>
    <td><CopyableCode code="uses_from_macos" /></td>
    <td><code>array</code></td>
    <td>Dependencies that are provided by macOS, which the formula can use. </td>
</tr>
<tr>
    <td><CopyableCode code="uses_from_macos_bounds" /></td>
    <td><code>array</code></td>
    <td>The minimum and maximum macOS versions that the formula can use. </td>
</tr>
<tr>
    <td><CopyableCode code="variations" /></td>
    <td><code>object</code></td>
    <td>Different variations of the formula, potentially for different operating systems or configurations. </td>
</tr>
<tr>
    <td><CopyableCode code="version_scheme" /></td>
    <td><code>integer</code></td>
    <td>Versioning scheme used by the formula. </td>
</tr>
<tr>
    <td><CopyableCode code="versioned_formulae" /></td>
    <td><code>array</code></td>
    <td>Other versions of the formula available as separate formulae.</td>
</tr>
<tr>
    <td><CopyableCode code="versions" /></td>
    <td><code>object</code></td>
    <td>The version numbers of the formula, including the stable, head, and bottle versions. </td>
</tr>
</tbody>
</table>
</TabItem>
</Tabs>

## Methods

The following methods are available for this resource:

<table>
<thead>
    <tr>
    <th>Name</th>
    <th>Accessible by</th>
    <th>Required Params</th>
    <th>Optional Params</th>
    <th>Description</th>
    </tr>
</thead>
<tbody>
<tr>
    <td><a href="#get_formula"><CopyableCode code="get_formula" /></a></td>
    <td><CopyableCode code="select" /></td>
    <td><a href="#parameter-formula_name"><code>formula_name</code></a></td>
    <td></td>
    <td>Retrieve detailed information about a specific Homebrew formula.</td>
</tr>
</tbody>
</table>

## Parameters

Parameters can be passed in the `WHERE` clause of a query. Check the [Methods](#methods) section to see which parameters are required or optional for each operation.

<table>
<thead>
    <tr>
    <th>Name</th>
    <th>Datatype</th>
    <th>Description</th>
    </tr>
</thead>
<tbody>
<tr id="parameter-formula_name">
    <td><CopyableCode code="formula_name" /></td>
    <td><code>string</code></td>
    <td>The name of the formula.</td>
</tr>
</tbody>
</table>

## `SELECT` examples

<Tabs
    defaultValue="get_formula"
    values={[
        { label: 'get_formula', value: 'get_formula' }
    ]}
>
<TabItem value="get_formula">

Retrieve detailed information about a specific Homebrew formula.

```sql
SELECT
name,
full_name,
aliases,
analytics,
bottle,
build_dependencies,
caveats,
conflicts_with,
conflicts_with_reasons,
dependencies,
deprecated,
deprecation_date,
deprecation_reason,
desc,
disable_date,
disable_reason,
disabled,
generated_date,
head_dependencies,
homepage,
installed,
keg_only,
keg_only_reason,
license,
link_overwrite,
linked_keg,
oldname,
oldnames,
optional_dependencies,
options,
outdated,
pinned,
post_install_defined,
recommended_dependencies,
requirements,
revision,
ruby_source_checksum,
ruby_source_path,
service,
tap,
tap_git_head,
test_dependencies,
urls,
uses_from_macos,
uses_from_macos_bounds,
variations,
version_scheme,
versioned_formulae,
versions
FROM homebrew.formula.formula
WHERE formula_name = '{{ formula_name }}' -- required
;
```
</TabItem>
</Tabs>
