## Task 08: Layout + Dashboard (App Shell)

## Objective
Convert the project into a complete system by 
adding a unified layout and a protected dashboard page.


## Requirements
### 1) Unified Layout (resources/views/layouts/app.blade.php)
- Create a shared layout used across the main pages.
- Navbar must include links:
  - Dashboard
  - Products
  - Categories
  - Suppliers
  - Logout
- Display the logged-in user name/email in the navbar.
- The layout must render page content using @yield('content')
  (or slots if you prefer).
  
### 2) Dashboard Page (/dashboard) (Auth Protected)
- The dashboard route must require authentication.
- Show **3 Cards** (counts):
  - Total Products
  - Total Categories
  - Total Suppliers
- Show **Latest Products** table (last 5 products):
  - Columns: name, category, supplier, owner
  - Order by newest first (created_at DESC)
  - Use eager loading to avoid N+1 queries.

### 3) Flash Messages (CRUD)
- After create/update/delete actions, redirect with a flash message.
- The layout must display global flash messages:
  - success
  - error

### 4) Validation Errors (Forms)
- Show field-level validation errors clearly using @error.
- Optional: add a general error summary block at the top of each form.

## Expected Outcome
- Unified app shell (layout + navbar).
- Protected dashboard with cards + latest products.
- Clear flash messages and validation errors across the system.

## Bonus
- Active navbar link highlighting.
- Quick links from cards (View Products / Categories / Suppliers).
