---
layout: page
title: Recipes
permalink: /recipes/
---

<div class="recipes-page">
  <p class="recipes-intro">A collection of my favorite recipes. Click on a category to filter, or browse all recipes below.</p>

  <div class="category-filters">
    <button class="category-btn active" data-category="all">All</button>
    <button class="category-btn" data-category="indian">Indian</button>
    <button class="category-btn" data-category="chaat">Chaat</button>
    <button class="category-btn" data-category="sandwich">Sandwich</button>
    <button class="category-btn" data-category="smoothie">Smoothie</button>
    <button class="category-btn" data-category="salad">Salad</button>
    <button class="category-btn" data-category="dessert">Dessert</button>
    <button class="category-btn" data-category="breakfast">Breakfast</button>
    <button class="category-btn" data-category="snack">Snack</button>
    <button class="category-btn" data-category="meal">Meal</button>
  </div>

  <div class="recipes-grid">
    {% for recipe in site.recipes %}
    <div class="recipe-card" data-categories="{{ recipe.categories | join: ' ' | downcase }}">
      <a href="{{ recipe.url | relative_url }}">
        {% if recipe.image %}
        <div class="recipe-card-image">
          <img src="{{ recipe.image | relative_url }}" alt="{{ recipe.title }}">
        </div>
        {% else %}
        <div class="recipe-card-image recipe-card-placeholder">
          <span>{{ recipe.title | slice: 0 }}</span>
        </div>
        {% endif %}
        <div class="recipe-card-content">
          <h3>{{ recipe.title }}</h3>
          <div class="recipe-card-categories">
            {% for category in recipe.categories %}
              <span class="recipe-tag">{{ category }}</span>
            {% endfor %}
          </div>
          {% if recipe.description %}
          <p class="recipe-card-description">{{ recipe.description | truncate: 100 }}</p>
          {% endif %}
        </div>
      </a>
    </div>
    {% endfor %}
  </div>

  <p class="no-recipes-message" style="display: none;">No recipes found in this category.</p>
</div>

<style>
.recipes-page {
  max-width: 1000px;
  margin: 0 auto;
}

.recipes-intro {
  margin-bottom: 1.5rem;
  color: #666;
}

.category-filters {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 2rem;
}

.category-btn {
  padding: 0.5rem 1rem;
  border: 1px solid #ddd;
  background: #fff;
  border-radius: 2rem;
  cursor: pointer;
  font-size: 0.9rem;
  transition: all 0.2s ease;
}

.category-btn:hover {
  background: #f8f9fa;
  border-color: #007bff;
}

.category-btn.active {
  background: #007bff;
  color: white;
  border-color: #007bff;
}

.recipes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

.recipe-card {
  border: 1px solid #e9ecef;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.recipe-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.recipe-card a {
  text-decoration: none;
  color: inherit;
  display: block;
}

.recipe-card-image {
  width: 100%;
  height: 180px;
  overflow: hidden;
}

.recipe-card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.recipe-card-placeholder {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.recipe-card-placeholder span {
  font-size: 3rem;
  color: white;
  font-weight: bold;
}

.recipe-card-content {
  padding: 1rem;
}

.recipe-card-content h3 {
  margin: 0 0 0.5rem 0;
  font-size: 1.1rem;
}

.recipe-card-categories {
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
  margin-bottom: 0.5rem;
}

.recipe-tag {
  background: #e9ecef;
  padding: 0.15rem 0.5rem;
  border-radius: 1rem;
  font-size: 0.75rem;
  color: #495057;
}

.recipe-card-description {
  color: #666;
  font-size: 0.9rem;
  margin: 0;
  line-height: 1.4;
}

.no-recipes-message {
  text-align: center;
  color: #666;
  padding: 2rem;
  font-style: italic;
}

.recipe-card.hidden {
  display: none;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const categoryBtns = document.querySelectorAll('.category-btn');
  const recipeCards = document.querySelectorAll('.recipe-card');
  const noRecipesMsg = document.querySelector('.no-recipes-message');

  categoryBtns.forEach(btn => {
    btn.addEventListener('click', function() {
      const category = this.dataset.category;

      // Update active button
      categoryBtns.forEach(b => b.classList.remove('active'));
      this.classList.add('active');

      // Filter recipes
      let visibleCount = 0;
      recipeCards.forEach(card => {
        const cardCategories = card.dataset.categories.toLowerCase();
        if (category === 'all' || cardCategories.includes(category)) {
          card.classList.remove('hidden');
          visibleCount++;
        } else {
          card.classList.add('hidden');
        }
      });

      // Show/hide no recipes message
      noRecipesMsg.style.display = visibleCount === 0 ? 'block' : 'none';
    });
  });
});
</script>
