<%*
// 1. Get the topic from a popup box
let topic = await tp.system.prompt("What did you learn today?");
if (topic == null || topic == "") { topic = "Untitled"; }

// 2. Format today's date
let date = tp.date.now("YYYY-MM-DD");

// 3. Create the new filename (e.g., 2026-01-04 Gemini Logic)
let newTitle = `${date} ${topic}`;

// 4. Rename the current file
await tp.file.rename(newTitle);

// 5. Ask for the category (to link to your Base hubs)
let category = await tp.system.prompt("Category? (e.g. Gemini)");
-%>

---
created: <% tp.file.creation_date("YYYY-MM-DD HH:mm") %>
category: [[<% category %>]]
source_url: <% tp.system.prompt("Source URL?") %>

---
