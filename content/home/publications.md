---
# An instance of the Pages widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: pages

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 60

title: Publications
subtitle: 'Free-to-read open access versions of all publications can be found via links with the{{< icon name="open-access" pack="ai" >}}icon.<br><br>

For an up-to-date list of publications, check out my {{< icon name="google-scholar" pack="ai" >}}[Google Scholar](https://scholar.google.com/citations?user=jxApK7gAAAAJ&hl=en).'



content:
  # Filter on criteria
  filters:
    folders:
      - publication
    tag: ''
    category: ''
    publication_type: ''
    author: ''
    exclude_featured: false
    exclude_future: false
    exclude_past: false
  # Choose how many pages you would like to display (0 = all pages)
  count: 5
  # Choose how many pages you would like to offset by
  offset: 0
  # Page order: descending (desc) or ascending (asc) date.
  order: desc
design:
  # Choose a view for the listings:
  view: citation
  columns: '2'
---
