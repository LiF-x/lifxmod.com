---
layout: default
last_modified_date: 2022-12-03T20:38:02.000+00:00
title: Wild animals on my server are not moving and/or in water
nav_order: 5
nav_exclude: false
parent: FAQ
has_children: false
has_toc: false

---
### Wild animals on my server are not moving and/or in water?

If this happens this is a result of your navmesh, to resolve this simply turn off your server and delete the following

1. NavMesh file (nm1.nmesh)
2. cache Folder

   These are located on your server at

       data/navMeshes
3. Turn the server back on and allow the navmesh to rebuild.  
     
   This will also fix tracking issues animal foot prints not showing when you search for wild animals.