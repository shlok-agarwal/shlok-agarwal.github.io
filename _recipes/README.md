# Recipes Collection

This folder contains recipe markdown files. Images go in `assets/recipes/`.

## Quick Start

To add a new recipe:
1. Create a new `.md` file in `_recipes/` folder (e.g., `my-new-recipe.md`)
2. Copy the template below and fill in your recipe details
3. Add any images to `assets/recipes/` folder
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
image: /assets/recipes/your-image.jpg

ingredients:
  - Ingredient 1
  - Ingredient 2
  - Ingredient 3

steps:
  - First step of the recipe.
  - Second step of the recipe.
  - Third step of the recipe.

photos:
  - url: /assets/recipes/photo1.jpg
    caption: Description of photo 1

videos:
  - youtube_id: VIDEO_ID_HERE
    caption: Video description

notes: Any additional tips or notes about the recipe.
---
```

## Available Categories

- Indian
- Chaat
- Sandwich
- Smoothie
- Salad
- Dessert
- Breakfast
- Snack
- Meal

A recipe can have multiple categories.

## Adding Images

1. Save images in `assets/recipes/` folder
2. Reference with path `/assets/recipes/your-image.jpg`

## Folder Structure

```
shlok-agarwal.github.io/
├── _recipes/                    # Recipe markdown files
│   ├── egg-salad-sandwich.md
│   └── ...
└── assets/
    └── recipes/                 # Recipe images
        ├── egg-salad-sandwich-dish.jpg
        └── ...
```

## Testing Locally

```bash
bundle exec jekyll serve
```
Then visit `http://localhost:4000/recipes/`
