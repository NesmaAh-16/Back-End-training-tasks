# Task 06: Many-to-Many Relationship (Products ↔ Suppliers) with Pivot Data

## Objective
Enhance the existing **Products + Categories** system by introducing a **Many-to-Many** relationship between Products and Suppliers.  
This task focuses on working with pivot tables, storing additional relationship data, updating Blade forms, and handling validation and persistence correctly.


## Requirements

## 1) Create Supplier Model & Migration
- Create a Supplier model with a migration.
- The suppliers table must include:
  - name (string, unique)
  - email (string, unique)
  - timestamps
- Create a SupplierSeeder that inserts **at least 5 suppliers**.

## 2) Create Pivot Table (product_supplier) + Constraints
- Create a migration for a pivot table named product_supplier.
- The table must include:
  - product_id
  - supplier_id
  - cost_price (decimal)
  - lead_time_days (integer)
  - timestamps
- Foreign Keys:
  - product_id references products.id
  - supplier_id references suppliers.id
- onDelete strategy:
  - When a Product or Supplier is deleted → **cascade** (pivot rows only)
- Add a **composite unique constraint** to prevent duplicates:
  - unique(product_id, supplier_id)

## 3) Define Eloquent Relationships
- In the Product model:
  - Define a suppliers() method
  - Relationship: belongsToMany(Supplier::class)
  - Must include:
    - withPivot(['cost_price', 'lead_time_days'])
    - withTimestamps()

- In the Supplier model:
  - Define a products() method
  - Relationship: belongsToMany(Product::class)
  - Include the same pivot fields and timestamps

## 4) Seeder (Attach Suppliers to Products)
- Create a seeder (e.g. ProductSupplierSeeder) that:
  - Attaches **1–3 suppliers** to each product
  - Populates pivot data:
    - cost_price
    - lead_time_days

Note that: Pivot data must exist in the database after seeding.

## 5) Update Product Create/Edit Forms (Blade)
In products/create and products/edit views:

- Add a **Suppliers** section
- Display all suppliers (checkboxes or multi-select)
- For each selected supplier, the user must enter:
  - cost_price
  - lead_time_days

**Required Form Structure (for easier validation & grading)**  
Use the following input names:
- suppliers[SUPPLIER_ID][selected]
- suppliers[SUPPLIER_ID][cost_price]
- suppliers[SUPPLIER_ID][lead_time_days]

## 6) Store & Update Logic (Controller)
- On store:
  - Save the product
  - Attach selected suppliers with pivot data using sync() or attach()
- On update:
  - Update the product
  - Update suppliers using sync() to handle:
    - Adding suppliers
    - Removing suppliers
    - Updating pivot data

## 7) Form Validation (StoreProductRequest & UpdateProductRequest)
Validation must ensure:
- At least **one supplier** is selected
- Selected suppliers exist in the database
- Pivot data is valid for each selected supplier

**Minimum acceptable rules (conceptual):**
- suppliers must be an array with selected items
- For each selected supplier:
  - cost_price is numeric and ≥ 0
  - lead_time_days is an integer and ≥ 0

## 8) Update Views (Display Relationship)
### Products Index
- Add a **Suppliers** column
- Display supplier name with pivot data, like:
  - Supplier A (cost: 120.50, lead: 7 days)

### Product Show (or Edit)
- Display all suppliers related to the product with their pivot data.

## Expected Outcome
- A working Many-to-Many relationship between Products and Suppliers
- Pivot table correctly stores additional data (cost_price, lead_time_days)
- Users can assign and update suppliers from create/edit forms
- Relationships are saved and updated correctly
- Blade views display supplier information clearly

## Bonus (Advanced Eager Loading) 
to reduce queries and avoid the N+1 problem :
- In ProductsController@index:
  - Use eager loading: with('suppliers')
- Display the number of suppliers per product using:
  - withCount('suppliers')
