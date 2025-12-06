# Laravel Basic Database Operations

## Task3: Basic Database Operations: Model, Migration, and Seeder

## Objective:
Create a Laravel web application to demonstrate basic database operations. In this task, you will create a Product model,
generate a migration to define the table schema, and use a seeder to insert dummy data into the database.

## Requirements:

1. **Create the Product Model and Migration:**
   - Generate the Product model and migration file using the Artisan command
   - Edit the migration file to define the schema for the products table
     - id: Primary key.
     - name: String field for the product name.
     - price: Decimal field for the product price.
     - timestamps: Automatically manages the created_at and updated_at columns.
   - Run the migration to create the table

2. **Create a Seeder to Add Dummy Products:**
   - Generate a seeder for the Product model
   - Edit the seeder file to insert at least three dummy products into the `products` table:
   - Run the seeder to populate the products table
     
3. **Verify Data in the Database:**
   - Check the database to ensure the products table has been created and populated with the dummy data.
   - Alternatively, use Tinker to check the data:

## Expected Outcome:
- A products table should be created in your database with the following fields: id, name, price, created_at, and updated_at.
- The ProductSeeder should populate the table with at least three dummy products.
- The data should be visible in the database or accessible via Tinker.

### Tips:
- **Mass Assignment Protection**: Ensure that you define the $fillable property in your model to protect against mass-assignment vulnerabilities.
- **Seeder and Migration Workflow**: Always run the migration first to create the table, followed by the seeder to insert data.
- **Use Tinker**: Test operations like creating new records or checking existing data using Tinker.

## How to Submit:
1. Upload your project to a GitHub repository.
2. Ensure your code is clean and well-commented.
3. Include a README.md file with instructions on how to run the application and perform the migrations and seeders.


