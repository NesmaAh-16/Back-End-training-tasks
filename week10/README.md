### Task 10: Product Image Upload (Storage)

## Goal
Enable **image uploads for products** in a Laravel app with:
- strong validation
- proper storage setup
- safe updates (no crashes)
- clean UI display (thumbnail + full image)

## What You Will Build
By the end of this task, each product can have an optional image that is:
- uploaded from **Create / Edit** forms
- stored publicly using Laravel storage
- displayed across the UI with fallbacks
- replaced safely without leaving garbage files behind

## Requirements

## 1) Database Migration
Add an optional column to store the image path:
- Column name: image_path
- Type: string
- Nullable


### 2) Create & Edit Forms
Update both forms to support file uploads:

- Add a file input:
  - name: image
  - accept: image/* (optional but recommended)
- Make sure the form includes:
  - enctype="multipart/form-data" (required for file uploads)

**Validation rules:**
- Must be an **image** (jpg, png, webp, etc.)
- Max size: **2MB** (recommended)

> **Student note:** If you forget multipart/form-data, the file will not be sent at all.


## 3) Storage Setup (Public Access)
- Store files using Laravel’s **public disk**
- Run: php artisan storage:link

## 4) Create & Update Logic (Safe + Clean)
# On Create
- If an image is uploaded:
  - store it
  - save the stored path into image_path

# On Update
If a new image is uploaded:
1. Delete the old image **safely** (only if it exists)
2. Store the new image
3. Update image_path

**Important rules:**
- The update must **not crash** if the old file is missing.
- No leftover unused images after updates.

## 5) UI Display Rules
Update your pages to show images nicely:

# Index Page (Products List)
- Show a small **thumbnail**
- Use a consistent size (example: 60x60 or 80x80)
# Show Page (Single Product)
- Show a larger product image
# Fallback / Placeholder
- If image_path is empty:
  - show a placeholder image (local asset or default image)

## Expected Outcome 
- Products support optional image uploads correctly
- Images are stored in public storage and accessible in the browser
- Old images are replaced safely without errors
- UI displays thumbnails in lists and full images in detail pages
- Placeholder is shown when no image exists

## Bonus (Recommended Enhancements)
- **Live Preview (JavaScript):** show the selected image before submission
- **Standard Thumbnail Styling:** keep thumbnails uniform using CSS (object-fit: cover)
