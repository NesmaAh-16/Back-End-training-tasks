# Task 2 – Laravel MVC with Multiple Controller Methods

## Objective

Create a Laravel web application that demonstrates the **MVC pattern** by using a controller with multiple methods.
Each method should return a different Blade view and pass different types of data (strings and arrays) to be displayed using Blade and loops.

## Requirements

1. Create a controller named **`HomeController`** with **four methods**:

   * `index()`
   * `about()`
   * `features()`
   * `team()`

2. Each method must return a **separate Blade view**:

   * `index()` → `home.blade.php`
   * `about()` → `about.blade.php`
   * `features()` → `features.blade.php`
   * `team()` → `team.blade.php`

3. Data must be passed **from the controller to the view**, not created or hard-coded inside the Blade files:

   * `index()` should pass a **title** variable (a welcome message).
   * `about()` should pass an **info** variable (a short descriptive text about the page).

4. The `features()` method must:

   * Pass an **indexed array** of strings (for example: a list of Laravel features).
   * The `features.blade.php` view must display this array using a **`@foreach` loop** inside an unordered list `<ul>`.

5. The `team()` method must:

   * Pass an **associative array** (array of members, each with a `name` and `role`).
   * The `team.blade.php` view must display this data in a **table**, where each row represents a team member.
   * The table content must be generated using a loop in Blade (no manual, hard-coded rows).

6. Define the necessary **routes** in `routes/web.php` so that:

   * `/` points to `HomeController@index`
   * `/about` points to `HomeController@about`
   * `/features` points to `HomeController@features`
   * `/team` points to `HomeController@team`

7. No values should be hard-coded directly in the Blade views if they are meant to come from the controller.
   All dynamic content must be passed as variables from the controller methods.

## You should

* Visiting `http://localhost:8000/` should display:

  * A title text coming from the `index()` method via the controller.

* Visiting `http://localhost:8000/about` should display:

  * Descriptive text coming from the `about()` method.

* Visiting `http://localhost:8000/features` should display:

  * An unordered list generated from an array of features using a loop in the Blade view.

* Visiting `http://localhost:8000/team` should display:

  * A table listing team members (name and role), where rows are generated using a loop over an associative array.
