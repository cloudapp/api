# Link Relations

A brief description of all the link relations used throughout the API. When
possible, link relations from [RFC5988][standard-links] are used.

[standard-links]: http://www.iana.org/assignments/link-relations/link-relations.xml


 - `/rels/account`: GET authenticated user's CloudApp account.
 - `/rels/drops`: GET authenticated user's drops.

## Drop Collection

 - `next`: GET the next page of drops.
 - `previous`: GET the previous page of drops.
 - `root`: _I don't think this link is necessary and will likely be remove._
 - `/rels/create`: POST to create a new drop.
 - `/rels/delete-drops`: POST a list of drop IDs to immediately and permanently
 - `/rels/restore-drops`: POST a list of drop IDs to restore from the trash.
   delete.
 - `/rels/trash-drops`: POST a list of drop IDs to move to the trash.

## Drop Item

 - `alternate`: Alternate public representations of a drop (direct content link,
   force download).
 - `canonical`: The public, sharable link.
 - `download`: A public link to download the drop's content.
 - `embed`: A public link to the drop's content.
 - `icon`: The publicly viewable thumbnail.