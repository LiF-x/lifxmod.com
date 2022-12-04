---
layout: default
last_modified_date: 2022-12-04 10:53:32 +0000
title: How can I add starter items to new characters
nav_order: 10
nav_exclude: false
parent: Tutorials
has_children: false
has_toc: false
published: false

---
### How can I add starter items to new characters?

  
Inside your server folder, there is a folder named "data" and there you will find a file named "cm_createchar.xml"

Modify this file accordingly by copy and pasting the current <item id="1463" line and changing the item id number to what you would like in your starter kit.  
  
Example:

     <?xml version="1.0" encoding="utf-8"?>
    <xml>
       <items>
          <item id="1463" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="301" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="1465" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="1466" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="1467" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="789" amount="40" vik="yes" mon="yes" eur="yes"/>
          <item id="342" amount="100" vik="yes" mon="yes" eur="yes"/>
          <item id="44" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="1580" amount="1" vik="yes" mon="yes" eur="yes"/>
          <item id="1663" amount="1" vik="yes" mon="yes" eur="yes"/>
       </items>
    </xml>