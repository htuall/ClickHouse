---
description: 'Settings for MergeTree which are in `system.merge_tree_settings`'
slug: /operations/settings/merge-tree-settings
title: 'MergeTree tables settings'
---

import ExperimentalBadge from '@theme/badges/ExperimentalBadge';
import BetaBadge from '@theme/badges/BetaBadge';

System table `system.merge_tree_settings` shows the globally set MergeTree settings.

MergeTree settings can be set in the `merge_tree` section of the server config file, or specified for each `MergeTree` table individually in
the `SETTINGS` clause of the `CREATE TABLE` statement.

Example for customizing setting `max_suspicious_broken_parts`:

Configure the default for all `MergeTree` tables in the server configuration file:

```text
<merge_tree>
    <max_suspicious_broken_parts>5</max_suspicious_broken_parts>
</merge_tree>
```

Set for a particular table:

```sql
CREATE TABLE tab
(
    `A` Int64
)
ENGINE = MergeTree
ORDER BY tuple()
SETTINGS max_suspicious_broken_parts = 500;
```

Change the settings for a particular table using `ALTER TABLE ... MODIFY SETTING`:

```sql
ALTER TABLE tab MODIFY SETTING max_suspicious_broken_parts = 100;

-- reset to global default (value from system.merge_tree_settings)
ALTER TABLE tab RESET SETTING max_suspicious_broken_parts;
```

## MergeTree settings {#mergetree-settings}
<!-- The settings below are autogenerated by the script at 
https://github.com/ClickHouse/clickhouse-docs/blob/main/scripts/settings/autogenerate-settings.sh
-->
