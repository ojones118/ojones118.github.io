---
title: "Complex Post Example"
date: 2025-10-03 14:00:00 +0000
categories: [Test]
tags: [advanced, first]
---
Here’s an introduction to the post.
<details>
<summary>Section: Setup & Requirements</summary>
List the hardware, tools, software versions, prerequisites here.
```bash
# Example installation command
sudo apt update && sudo apt install xyz
```
</details>
<details>
<summary>Section: Step  by Step Guide</summary>
1. First step: do A
2. Next step: do B
3. Then: run this command
Best Practices
• Keep summary titles short and descriptive (e.g., 'Setup & Requirements').
• Avoid nesting too many collapsibles — it can confuse readers.
• Place code blocks, images, and long text inside collapsibles to reduce page clutter.
• Style collapsibles with custom CSS if you want icons, indentation, or animations.
• Test locally with `bundle exec jekyll serve` to confirm HTML collapsibles render correctly.
Optional CSS Styling
.post-content details {
 margin: 1em 0;
 padding: 0.5em;
 border: 1px solid #ccc;
 border-radius: 6px;
}
.post-content summary {
 cursor: pointer;
 font-weight: bold;
}
  
</details>
<details>
<summary>Section: Tips & Troubleshooting</summary>
