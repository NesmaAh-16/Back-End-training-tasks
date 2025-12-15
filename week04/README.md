**Laravel Basic Database Operations**

**Task04: Product Validation & Data Integrity in Laravel**

**Objective:**

Enhance the existing Product CRUD module by adding **server-side form validation** and **database-level integrity rules**.  
In this task, you will create dedicated **Form Request** classes for validation, enforce constraints such as **unique product names** and **valid prices**, and improve user feedback by displaying **validation error messages** in the views.

**Requirements:**

**1. Implement Form Validation (Store + Update):**

**Create Validation (Store):**

- **name** is **required** and **unique** in the `products` table.
- **price** is **required**, must be **numeric**, and must be **greater than 0**.

**Update Validation (Update):**

- Apply the **same validation rules**.
- Ensure **name uniqueness ignores the current product** during update.

**2. Use Laravel Form Requests (Clean Code Standard):**

- Create and use:
  - **StoreProductRequest**
  - **UpdateProductRequest**

- Controllers must rely on:
  - **$request->validated()**
  instead of manual validation inside the controller.

**3. Improve User Experience in Views:**

- Display **validation errors clearly**:
  - **Under each input field**.
  - Or as a **summary list** at the top of the form.
- Preserve old input values using **`old()`**.

**4. Enforce Database Integrity (Migration Level):**

- Update the migration to ensure:
  - **name** has a **unique index**.
  - **price** uses **DECIMAL** type.
- Run migrations to apply constraints.

**5. Verify Validation Rules:**

- Empty **name** → validation fails.
- Duplicate **name** → validation fails.
- **price ≤ 0** → validation fails.
- Update without changing name → passes.
- Update with duplicate name → fails.

**Expected Outcome:**

- Invalid product input is rejected with **clear error messages**.
- Validation is handled using **Laravel Form Request** classes.
- Database integrity is enforced using:
  - **UNIQUE(name)**
  - **DECIMAL price**
- The Product CRUD module becomes more **production-ready** with **cleaner code** and **better reliability**.
