# Recipes Collection

This folder contains all recipe markdown files for the website.

## Quick Start

To add a new recipe:
1. Create a new `.md` file in this folder (e.g., `my-new-recipe.md`)
2. Copy the template below and fill in your recipe details
3. Add any images to the `assets/` folder
4. Commit and push to GitHub

## Recipe Template

```markdown
---
layout: recipe
title: Your Recipe Name
categories:
  - Category1
  - Category2
description: A brief description of the recipe (shown on recipe cards).
image: /recipes/assets/your-image.jpg

ingredients:
  - Ingredient 1
  - Ingredient 2
  - Ingredient 3

steps:
  - First step of the recipe.
  - Second step of the recipe.
  - Third step of the recipe.

photos:
  - url: /recipes/assets/photo1.jpg
    caption: Description of photo 1
  - url: /recipes/assets/photo2.jpg
    caption: Description of photo 2

videos:
  - youtube_id: VIDEO_ID_HERE
    caption: Video description
  # OR for local videos:
  - url: /recipes/assets/video.mp4
    caption: Video description

notes: Any additional tips or notes about the recipe.
---

Optional markdown content can go here for any extra information.
```

## Available Categories

Use these categories (case-sensitive):
- Indian
- Chaat
- Sandwich
- Smoothie
- Salad
- Dessert
- Breakfast
- Snack
- Meal

A recipe can have multiple categories. For example, a Samosa Chaat can be tagged with `Indian`, `Chaat`, and `Snack`.

## Adding Images

1. Save your image in the `_recipes/assets/` folder
2. Reference it in your recipe:
   - Main image: `image: /recipes/assets/your-image.jpg`
   - Additional photos: under the `photos:` section

Supported formats: `.jpg`, `.jpeg`, `.png`, `.gif`, `.webp`

## Adding Videos

### YouTube Videos
```yaml
videos:
  - youtube_id: dQw4w9WgXcQ
    caption: How to make this dish
```

### Local Videos
Save the video in `_recipes/assets/` and reference it:
```yaml
videos:
  - url: /recipes/assets/cooking-demo.mp4
    caption: Step-by-step demonstration
```

## File Naming

- Use lowercase letters
- Replace spaces with hyphens
- Keep names descriptive but concise
- Examples: `samosa-chaat.md`, `berry-smoothie.md`, `grilled-cheese-sandwich.md`

## Editing Recipes

Simply edit the `.md` file, commit, and push. The website will update automatically.

## Removing Recipes

Delete the `.md` file and any associated images in `assets/`, then commit and push.

## Folder Structure

```
_recipes/
├── README.md           # This file
├── assets/             # All recipe images and videos
│   ├── samosa-chaat.jpg
│   └── berry-smoothie.jpg
├── samosa-chaat.md     # Recipe files
└── berry-smoothie.md
```

## Testing Locally

Run the Jekyll server to preview changes:
```bash
bundle exec jekyll serve
```
Then visit `http://localhost:4000/recipes/`
