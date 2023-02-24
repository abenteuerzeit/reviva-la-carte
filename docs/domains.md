# Domain and Module Specs

## Domains and subdomains

## User Management

- Entities: User, Role, Permission
- Value Objects: Credentials, UserProfile

## Meal Planning and Generation

- Entities: MealPlan, Meal, Recipe, Ingredient
- Value Objects: MealPreference, DietaryRestriction

## Recipe Management

- Entities: Recipe, Ingredient
- Value Objects: RecipeCategory, IngredientCategory

## Grocery List and Product Recommendations

- Entities: GroceryList, Product, Ingredient
- Value Objects: Location

## Sharing

- Entities: SharedMealPlan
- Value Objects: -

## Delivery and Payment

- Entities: Order, Payment
- Value Objects: Address, PaymentMethod


## Modules

1. User Management Module: handles user authentication, authorization, and profile management.
2. Meal Planning and Generation Module: generates meal plans based on user preferences and dietary restrictions.
3. Recipe Module: allows users to search, create, and manage recipes.
4. Grocery List and Product Recommendations Module: generates grocery lists based on the meal plan and offers product recommendations.
5. Sharing Module: allows users to share meal plans with others.
6. Delivery and Payment Module: manages the delivery and payment of orders.


## Assignment of domains and subdomains to each module

### User Management Module

User Management Domain: User Management, User, Role, Permission, Credentials, UserProfile

### Meal Planning and Generation Module

Meal Planning Domain: Meal Planning and Generation, MealPlan, Meal, Recipe, Ingredient, MealPreference, DietaryRestriction

### Recipe Module

Recipe Management Domain: Recipe Management, Recipe, Ingredient, RecipeCategory, IngredientCategory

### Grocery List and Product Recommendations Module

Grocery List Domain: Grocery List and Product Recommendations, GroceryList, Product, Ingredient, Location

### Sharing Module:

Sharing Domain: Sharing, SharedMealPlan

### Delivery and Payment Module

Delivery and Payment Domain: Delivery and Payment, Order, Payment, Address, PaymentMethod

## Module Dependencies

User Management Module depends on the Delivery and Payment Module

- The User Management Module requires access to the Delivery and Payment Module to complete checkout and process payment for meal plans.

Meal Planning and Generation Module depends on Grocery List and Product Recommendations Module and Recipe Module

- The Meal Planning and Generation Module relies on the Grocery List and Product Recommendations Module to generate shopping lists for users based on real products available in their area. It also depends on the Recipe Module to generate meal plans for users.

Sharing Module depends on the Recipe Module

- The Sharing Module relies on the Recipe Module to provide recipes that users can share with others.

Delivery and Payment Module

- This module does not depend on any other modules in the app, but all other modules depend on it to complete checkout and process payment.

Grocery List and Product Recommendations Module and Recipe Module
- These modules do not depend on any other modules in the app, but the Meal Planning and Generation Module depends on both of them to generate meal plans and shopping lists for users.


## Details

| Domain/Subdomain | Description | Modules | Entities | Value Objects | 
| --- | --- | --- | --- | --- | 
| User Management | Handles user authentication, authorization, and profile management | User Management Module | User, Role | Email, Password, Name | 
| Meal Planning and Generation | Generates meal plans based on user preferences and dietary restrictions | Meal Planning and Generation Module | Meal Plan, Meal | Meal Preference, Dietary Restriction | 
| Recipe | Allows users to search, create, and manage recipes | Recipe Module | Recipe | Ingredient, Instruction, Time, Servings | 
| Grocery List and Product Recommendations | Generates grocery lists based on the meal plan and offers product recommendations | Grocery List and Product Recommendations Module | Grocery List, Product Recommendation | Product, Quantity | 
| Sharing | Allows users to share meal plans with others | Sharing Module | Meal Plan Share | - | 
| Delivery and Payment | Manages the delivery and payment of orders | Delivery and Payment Module | Order, Payment | Address, Payment Method |

### additional domain and subdomain details

#### User Management

Entities:
- User: represents a registered user in the system and contains information such as email, name, and password.
- Role: represents a role that a user can have, such as admin or regular user.

Value Objects:
- Email: a value object representing a valid email address.
- Password: a value object representing a hashed password.
- Name: a value object representing a user's name.

#### Meal Planning and Generation

Entities:
- Meal Plan: represents a collection of meals planned for a given period of time.
- Meal: represents a single meal in a meal plan and contains information such as recipe and serving size.

Value Objects:
- Meal Preference: represents a user's preference for certain types of meals, such as vegetarian or low-carb.
- Dietary Restriction: represents a user's dietary restriction, such as gluten-free or vegan.

#### Recipe

Entities:
- Recipe: represents a recipe in the system and contains information such as ingredients, instructions, and cooking time.

Value Objects:
- Ingredient: represents an ingredient in a recipe and contains information such as name, quantity, and unit of measurement.
- Instruction: represents a step in a recipe's instructions.
- Time: a value object representing the time required to prepare and cook a recipe.
- Servings: a value object representing the number of servings a recipe yields.

#### Grocery List and Product Recommendations

Entities:
- Grocery List: represents a list of items that a user needs to purchase for their meal plan.
- Product Recommendation: represents a recommended product for a user to purchase based on their grocery list.

Value Objects:
- Product: represents a product that a user can purchase, such as a specific brand of milk or type of pasta.
- Quantity: represents the quantity of a product that a user needs to purchase.

#### Sharing

Entities:
- Meal Plan Share: represents a shared meal plan and contains information such as the recipient's email and any message from the sender.

#### Delivery and Payment

Entities:
- Order: represents an order placed by a user and contains information such as the meal plan, delivery address, and payment details.
- Payment: represents a payment made by a user for their order.

Value Objects:
- Address: represents a delivery address and contains information such as street address, city, and zip code.
- Payment Method: represents a user's chosen payment method, such as credit card or PayPal.
