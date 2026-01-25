### Task 11: Soft Delete, Trash, Restore, Final Delivery

## Objective
Implement **safe deletion** using Soft Deletes with a dedicated **Trash** page that supports
**Restore** and **Force Delete**, enforce **proper authorization**, provide **demo seed data**,
add **minimum tests**, and finalize the project with a clean **README + screenshots**.

## Requirements
# 1) Soft Deletes
Add Soft Delete support to products.
- Add deleted_at column to the products table (migration).
- Enable SoftDeletes in the Product model.
- Ensure default product listings **exclude trashed products** automatically.

## 2) Trash Page
Create a Trash page to manage soft-deleted products.
- Route (auth protected): GET /products/trash
- List only soft-deleted products using onlyTrashed().
- Display fields:
  - Name
  - Category
  - Supplier
  - Owner
  - Deleted At (deleted_at)
- Actions per trashed product:
  - Restore
  - Force Delete

## 3) Authorization (Policy + Blade)
Prevent cross-user trash actions and enforce correct permissions.
- Restore / Force Delete allowed only for:
  - Product owner
  - Admin (if available)
- Enforce via:
  - Policy (server-side authorization)
  - Hide Restore/Force Delete buttons in Blade when unauthorized
- Unauthorized access must return **403 Forbidden**.

## 4) Seeders (Demo Data)
Seed realistic demo data with correct relationships.
- Seed Categories.
- Seed Suppliers.
- Seed Products with correct relations:
  - category_id
  - supplier_id
  - user_id
- Provide at least one known demo user (credentials must be included in README).

## 5) Tests (Minimum)
Add minimum feature coverage for trash/restore flow.
- Soft delete moves product to trash:
  - Not visible in normal list
  - Visible in trash list
- Restore returns product to the normal list.
- Recommended: Non-owner restore/forceDelete returns **403**.

## 6) README + Final Delivery
Make the project submission-ready.
- README includes setup steps:
  - Install dependencies
  - Run migrations
  - Run seeders
  - Start the app

- Add required screenshots:
  - Dashboard
  - Products index (cards/search/filter)
  - Trash page


## Expected Outcome
- Soft delete works properly.
- Trash page supports Restore + Force Delete.
- Authorization prevents cross-user trash actions.
- Seeders provide realistic demo data.
- Minimum tests confirm trash/restore flows.
- README + screenshots make the project submission-ready.


## Bonus: Advanced Trash Management + Delivery Polish
Go beyond basic access control by adding features that make 
the Trash system feel **complete**, **safe**, and **professional**.

# Bonus Requirements
# 1) Bulk Actions (Trash Power Tools)
Add bulk operations on the Trash page.
- Add checkbox selection for trashed products.
- Add bulk actions:
  - Bulk Restore (restore selected)
  - Bulk Force Delete (delete selected permanently)
- Enforce authorization on bulk endpoints (no bypassing Policy).

# 2) Smart Filters + Search (Trash UX Upgrade)
Make Trash easy to navigate.
- Add keyword search (by product name).
- Add filters:
  - Category
  - Supplier
  - Owner (admin-only if applicable)
- Add sorting:
  - Newest deleted first (default)
  - Oldest deleted first (optional)

# 3) Safety Guardrails (Confirmation + Anti-Accident)
Prevent accidental permanent deletion.
- Add confirmation modal for Force Delete.
- Optional safety rule:
  - Prevent Force Delete if deleted less than X minutes ago (cooldown), or require extra confirmation text.
    
# 4) Auto-Cleanup Command (Pro Touch)
Add maintenance support for old trashed products.
- Create an Artisan command to permanently delete products trashed for more than N days.
- Document how to run it manually.
- Optional: show how to schedule it in `Kernel.php`.
  
# 5) Better UX Feedback
Make actions feel polished.

- Flash messages:
  - Moved to Trash
  - Restored Successfully
  - Deleted Permanently
- Empty states:
  - Trash is empty
  - No results found for filters/search

# 6) Extra Tests 
- Bulk restore works and respects authorization.
- Bulk force delete works and respects authorization.
- Trash filters/search return correct results.

# Bonus Expected Outcome
- Trash page supports bulk actions, search, and filters.
- Force Delete is safer with confirmations/guardrails.
- Cleanup command supports real-world maintenance.
- UI/UX looks polished and professional.
- Tests prove bonus features work correctly.
