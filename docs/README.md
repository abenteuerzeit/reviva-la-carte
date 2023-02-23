# Documentation

In this folder, you can find all the documentation created by the developers. 


## High-Level Design

### Modular Monolith with Vertical Slices

Modules are the high-level components that make up the app. Each module represents a specific area of functionality that the app provides, such as user management, meal planning and generation, grocery list and product recommendations, recipe management, sharing, and delivery management and payment

Each module is a self-contained set of features that are related to a specific domain or functional area of the application. The features within a module are designed to work together to provide a cohesive set of capabilities and functionality for that specific domain. By organizing the application into modules, it becomes easier to manage and maintain as the codebase grows and becomes more complex.

- User Management Module depends on the Delivery and Payment Module: The User Management Module requires access to the Delivery and Payment Module to complete checkout and process payment for meal plans.
- Meal Planning and Generation Module depends on Grocery List and Product Recommendations Module and Recipe Module: The Meal Planning and Generation Module relies on the Grocery List and Product Recommendations Module to generate shopping lists for users based on real products available in their area. It also depends on the Recipe Module to generate meal plans for users.
- Sharing Module depends on the Recipe Module: The Sharing Module relies on the Recipe Module to provide recipes that users can share with others.
- Delivery and Payment Module: This module does not depend on any other modules in the app, but all other modules depend on it to complete checkout and process payment.
- Grocery List and Product Recommendations Module and Recipe Module: These modules do not depend on any other modules in the app, but the Meal Planning and Generation Module depends on both of them to generate meal plans and shopping lists for users.

### Code Organization and Structure

```
meal-planner-app/
├── user-management/
│   ├── src/
│   ├── tests/
│   └── README.md
├── meal-planning/
│   ├── src/
│   ├── tests/
│   └── README.md
├── recipe-management/
│   ├── src/
│   ├── tests/
│   └── README.md
├── grocery-list/
│   ├── src/
│   ├── tests/
│   └── README.md
├── sharing/
│   ├── src/
│   ├── tests/
│   └── README.md
├── delivery-payment/
│   ├── src/
│   ├── tests/
│   └── README.md
└── README.md
```
