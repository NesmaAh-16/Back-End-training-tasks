### **Laravel Basic Database Operations**

**Task03(2): Product CRUD Operations in Laravel**

## **Objective:**

Create a Laravel web application to demonstrate basic database operations. In this task, 
you will create a Product model(you make it),generate a migration to define the table schema,
and use a seeder to insert dummy data into the database.You will also implement CRUD operations for managing products.

## **Requirements:**

1. **Implement CRUD Operations for the Product Model:**

   * **Create**: Implement functionality to add new products via a form.
   * **Read**: Implement functionality to display a list of all products.
   * **Update**: Implement functionality to edit the details of an existing product.
   * **Delete**: Implement functionality to remove a product from the database.

2. **Create Views for Displaying and Managing Data:**

   * Create a view to display a list of all products.
   * Create a form to add new products.
   * Create a form to edit existing products.

3. **Verify Data in the Database:**

   * Ensure that the products table is created and populated with at least **five dummy products**.
   * Verify that the CRUD operations are working correctly by testing the functionality to add, update, and delete products.

## **Expected Outcome:**

* A products table will be created in the database with the fields: id, name, price, created_at, and updated_at.
* **Five dummy products** will be inserted into the products table via the seeder.
* The application will successfully perform CRUD operations on the products table:
  * Add new products.
  * View the list of products.
  * Edit existing products.
  * Delete products.
* A simple interface will allow users to interact with the products (via a form and a product list).
