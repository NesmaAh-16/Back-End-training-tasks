# Task 1 – Laravel Hello World with Dynamic Name

## Objective

Create a basic Laravel web application where the homepage (`/`) displays a static message and a personalized greeting using a dynamic name.

## Requirements

1. The homepage must display the following two lines:
   - The static message: **"Hello, World!"**
   - A personalized greeting that uses a dynamic name variable, for example: **"Hello, Ali"**.

2. The name must be passed from the **route** to the **Blade view** as a variable.
   - The name must **not** be hard-coded directly inside the Blade view.

3. The page must be implemented using a **Blade view**, not by returning a plain string from the route.

## You should

- Visiting `http://localhost:8000/` shows:
  - `Hello, World!`
  - `Hello, Ali` (or any other name stored in the variable).
- The name value is passed from the route to the view as a variable, not hard-coded inside the Blade file.
