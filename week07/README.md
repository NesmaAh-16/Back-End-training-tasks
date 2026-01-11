# Task 07: Authentication & Authorization (Products ↔ Users Ownership)

## Objective
Enhance the existing **Products + Categories + Suppliers** system by introducing **Authentication** and **Authorization**.
By:
- Adding user accounts (register/login/logout)
- Protecting product management routes
- Linking products to their owners (users)
- Restricting update/delete actions to authorized users only
- Updating Blade views to respect permissions
- Writing basic feature tests to validate access rules

## Requirements
## 1) Install Authentication (Laravel Breeze)
Install Laravel Breeze authentication scaffolding.

The system must provide:
- Register
- Login
- Logout

**Authentication must work correctly (users can register and login successfully)**.

## 2) Add Product Ownership (user_id) + Constraints
Enhance the existing products table by adding ownership information.

Create a migration that adds:
- user_id (foreign key)

Foreign Keys:
- user_id references users.id

onDelete strategy:
- Must be applied intentionally (restrict / cascade / set null)

**Every product must belong to the user who created it**.

## 3) Define Eloquent Relationships
Define the relationship between Users and Products.

In the User model:
- Define a products() method
- Relationship: hasMany(Product::class)

In the Product model:
- Define a user() method
- Relationship: belongsTo(User::class)

## 4) Store Owner Automatically (Controller Logic)
Update product store logic.
On store:
- Save the product
- Assign the owner automatically (based on the logged-in user)

Rules:
- The form must NOT contain user_id
- The controller must NOT accept user_id from request input
- Ownership must be assigned internally by the system

## 5) Protect Product Management Routes (Middleware)
Protect product management routes so only logged-in users can access them.

Routes that must require authentication:
- products.create
- products.store
- products.edit
- products.update
- products.destroy

Public routes:
- You may keep products.index and products.show public OR protect them
- Choose one approach and apply it consistently

## 6) Authorization Using Policy (ProductPolicy)
Create and apply a ProductPolicy to enforce access control rules.
Rules:
- A user can update/delete a product only if they own it

Required policy methods:
- update
- delete

**Unauthorized access must be blocked (403 Forbidden for logged-in users)**.

## 7) Update Blade Views (Permission Display)
Update Blade templates so the UI respects permissions.

Products Index:
- Add an Owner column (user name/email)
- Display Edit/Delete buttons only for authorized users

Create/Edit forms:
- Must not contain ownership fields

## 8) Feature Tests (Authentication + Authorization)
Create Feature tests to confirm security rules.

Minimum required tests:
1) Guest users cannot access protected routes (create/edit/update/delete)
2) Logged-in user cannot update/delete products they do not own (403)
3) Logged-in user can update/delete their own products

## Expected Outcome
- Authentication system working (register/login/logout)
- Products linked to users via user_id
- Product management routes protected
- Authorization rules correctly enforced
- Blade views reflect permissions (buttons hidden when not allowed)
- Feature tests validate security behavior

## Bonus
- Add Admin role and allow admin to manage all products
- Improve project structure and code cleanliness
