
<%*
// System Prompt which ask user to enter category name
let title = await tp.system.prompt("Enter Category Name");
if (title == null) { title = "New Category" };
await tp.file.rename(title);
%>
# Category: <% title %>

### Linked Notes
```dataview
TABLE 
    file.ctime AS "Created By", 
    file.mtime AS "Updated By"
FROM [[]]
WHERE file.name != this.file.name
SORT file.mtime DESC