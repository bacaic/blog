---
title: Add a module manually with Prestashop 1.7
date: 2018-05-28T00:55:37+00:00
permalink: /2018/05/add-a-module-manually-with-prestashop-1-7/
categories: [opensource,prestashop]
---

Your UI is not working? Your Backoffice doesn't allow you to install a module anymore because you tweaked it? You can install a module by hand in SQL directly by following this tutorial.

<!--more-->

## Module & tabs install
  1. Make sure your module is avalaible locally under `/modules/my_module/my_module.php`
  2. Go to your database and run:

```sql
# Module
insert into _module (name, version, active) values ('my_module', '1.0.0', 1); # keep the id
insert into _module_shop (id_module, id_shop) values (use_the_id, 1);
# Tabs
```

## Module & tabs uninstall
```sql
# Module
delete from ps_module_shop where id_module = XXX;
delete from ps_module where name = 'my_module';
# Tabs
delete from ps_tab where module = 'my_module';
```
