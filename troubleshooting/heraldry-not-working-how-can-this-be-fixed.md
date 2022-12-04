---
layout: default
last_modified_date: 2022-12-04T10:47:43.000+00:00
title: Heraldry Not Working how can this be fixed
nav_order: 5
nav_exclude: false
parent: Troubleshooting
has_children: false
has_toc: false
published: false

---
Heraldry Not Working how can this be fixed?

\- Shut down the server first  
\- Update DB by setting coalition to **utf8_unicode_ci**  
\- Restart the server

Alternatively, you can run the Query below into your database using HeidiSql or a similar program

    ALTER TABLE `heraldic_charges`
        ALTER `Position` DROP DEFAULT,
        ALTER `Size` DROP DEFAULT;
    ALTER TABLE `heraldic_charges`
        CHANGE COLUMN `Position` `Position` ENUM('top_left','top_center','top_right','middle_left','true_center','middle_right','bottom_left','bottom_center','bottom_right') NOT NULL AFTER `ColorIndex`,
        CHANGE COLUMN `Size` `Size` ENUM('small','medium','large') NOT NULL AFTER `Position`;

 