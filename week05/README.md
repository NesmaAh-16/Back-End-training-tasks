# Task 05: Eloquent Relationships & Category Association

## Objective
Enhance the Product Management System by introducing a relational database structure.
In this task, you will create a Category entity and establish a One-to-Many relationship between Categories and Products, 
ensuring data is organized and efficiently retrieved.

## Requirements

### 1. Create Category Model & Migration
* Generate a Category model with a migration file.
* The categories table must include a name field (string, unique).
* Create a CategorySeeder to populate the table with at least 5 categories (e.g., Electronics, Fashion, Home, etc.).

### 2. Database Relationship (Migration Level)
* Add a category_id field to the products migration.
* Define a Foreign Key constraint linking category_id to the id on the categories table.
* Implement an appropriate onDelete strategy (e.g., cascade or set null).

### 3. Define Eloquent Relationships
* In Product Model: Define the category() method using the belongsTo relationship.
* In Category Model: Define the products() method using the hasMany relationship.

### 4. Update CRUD & Form Validation
* Forms: Modify the Create and Edit views to include a `<select>` dropdown containing all available categories.
* StoreProductRequest & UpdateProductRequest: Add validation for category_id:
  * Must be required.
  * Must exist in the categories table.
* Controller: Ensure the category_id is correctly saved during store and update operations.

### 5. Query Optimization & View Enhancement
* Eager Loading: Use `Product::with('category')` in the Controller to avoid the N+1 query problem.
* Index View: Display the Category Name in a new column within the products table.

## Expected Outcome
* Relational Database: A functioning One-to-Many relationship between Categories and Products.
* Dynamic UI: Product forms now include a dynamic category selection.
* Data Integrity: Validation ensures products are always linked to a valid category.
* Clean Code: Queries are optimized using Eloquent Eager Loading, and the code follows Laravel standards.
