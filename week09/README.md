### Task 09 / Products Listing Pro

> **Goal:** Upgrade the Products page into a production-style listing that supports real-world
 data browsing: **searching**, **filtering**, **sorting**, and **pagination** — all in one smooth experience.

## Objective
Transform the **Products Index** into a powerful management page where users can quickly find products,
narrow results, sort them properly, and navigate through pages without losing their selected options.

## Requirements

## 1) Search
Add a search feature that filters products by:

- **name**
- **description** *(only if the column exists)*
 Search must work **together** with filters + sorting + pagination.

## 2)  Filters
Add dropdown filters for:
 **category_id**
 **supplier_id**

Filters must be **combinable** (example: search + category + supplier).


## 3) Sorting
Add sorting options to the listing:

## By date (`created_at`)
- **Newest → Oldest** *(DESC)*
- **Oldest → Newest** *(ASC)*

## By price *(if price exists)*
**Price: Low → High** *(ASC)*
**Price: High → Low** *(DESC)*

## If no price column exists
- Sort by **name** *(at least ASC , optional ASC/DESC)*

 Use a **whitelist** for allowed sort fields + directions to prevent invalid input.

## 4) Pagination + Query Persistence
- Enable pagination on the Products list.
- Preserve search/filter/sort inputs when switching pages using:
 withQueryString()

## 5) Blade UI (Index Page)
In: resources/views/products/index.blade.php
Add a **top toolbar form** above the table that includes:
- Search input
- Category dropdown
- Supplier dropdown
- Sort dropdown
- Apply/Filter button
- Reset/Clear button *(recommended)*

Also add an **Empty State**:
- When no products match the criteria, display a clear message:
  - No products found matching your criteria.

## Expected Outcome
A clean, professional Products listing that is easy to use:
- Search works instantly and reliably  
- Filters narrow results correctly  
- Sorting behaves as expected  
- Pagination keeps the selected query options  
- UI includes a proper empty state and clear controls  
