---
title: "Weird service portal instance"
subtitle: ""
summary: ""
date: 2017-10-26T20:25:56-05:00
---

So today I was working on a widget [Accept / Reject
Solution](/post/2017-10-26-sp-accept-reject/). I found a
[share](https://share.servicenow.com/app.do#/detailV2/b419262413caa600f609d6076144b030/overview)
that looked like it would meet all of my needs. It looked great, until I
tried rejecting a custom extended task table.

I couldn't easily set it to work so I backed it out and determined I'd
just roll my own, however that share updated a existing `sp_instance`.
After I backed out the update set that `sp_instance` record was still
there. I couldn't get it to fall off the page regardless what I tried;

-   Record didn't exist at this point so couldn't delete it.
-   Recreated empty table, and inserted the record with the referenced
    sys\_id via [setNewGuidValue](https://sn.jace.pro/GlideRecord/#setNewGuidValue). At
    this point I could set Active to false, but I wanted it gone.
-   Tried Deleting the record from the column record, but it would only
    ever delete the actual record on it's table and not from the related
    list of `sp_instance`s.

I ended up making a new column, moving all widgets over, then deleted
the old column.
