---
_schema: default
layout: default
title: Heraldry Not Working how can this be fixed
nav_order: 5
nav_exclude: false
parent: Troubleshooting
has_children: false
has_toc: false
last_modified_date: 2022-12-04 10:47:43
---
Heraldry Not Working how can this be fixed?

\- Shut down the server first<br>\- Update DB by changing coalition From **utf8\_unicode\_ci&nbsp;**&nbsp;to the correct one **utf8\_general\_ci**<br><br>This should be done In the heraldic\_charges​​​ Table​​​​<br><br>**As pictured below**

![](/uploads/hereldryfix-1.png){: width="2800" height="726"}

Ensure you save the data after changes or they will not take effect<br><br>\- Restart the server

In some cases the coalation is not the issue, in this case you can try to run the Query below into your database using HeidiSql or a similar program<br><br>this will fix positioning issues in heraldic\_charges

```
ALTER TABLE `heraldic_charges`
    ALTER `Position` DROP DEFAULT,
    ALTER `Size` DROP DEFAULT;
ALTER TABLE `heraldic_charges`
    CHANGE COLUMN `Position` `Position` ENUM('top_left','top_center','top_right','middle_left','true_center','middle_right','bottom_left','bottom_center','bottom_right') NOT NULL AFTER `ColorIndex`,
    CHANGE COLUMN `Size` `Size` ENUM('small','medium','large') NOT NULL AFTER `Position`;
```