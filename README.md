# reviva-la-carte

- See [System Architecture Decision](https://github.com/abenteuerzeit/reviva-la-carte/blob/development/docs/SAD.md)

Our app automates grocery shopping and generates diet plans based on user-defined nutritional requirements. It sources recipes from Edamame API and creates a shopping list with one-click checkouts and delivery. Users can share meal plans, create diet and lifestyle groups, and more. All in one convenient, easy-to-use platform

To solve the problem of creating customized food lists that meet specific nutritional requirements, we can design an e-commerce and lifestyle web application that includes a core scoring algorithm to generate a list of food items. The app would allow users to track their food inventory, plan their meals, and create a shopping list for the ingredients. In addition, users can search for recipes, create collections, and share their data with others. Below is the logical hierarchy of the app's features, domains, and subdomains, and how they relate to the problem.

Features

|Level|	Feature|
|-----|--------|
1	| Meal planning
2	| Nutritional goal templates
2	| Recipe management
2	| Shopping
2	| User management

Domains

|Level| Domain |	Description|
|-----|--------|-------------|
1	|Nutrition|	Nutritional aspects of the system, including algorithms used to calculate nutritional requirements and the scoring system for meal plans.
2	|Meal Planning|	Functionality related to generating meal plans based on nutritional requirements.
3	|Recipe Management|	Functionality related to managing recipes, collections, and sharing data with others.
3	|Nutrient Requirements|	Specific nutritional requirements of individuals, including the LBA, IA, and UBA.
3	|Shopping|	Functionality related to creating a shopping list for the ingredients.
3	|User Management|	Functionality related to managing user accounts.

Subdomains

|Level|Subdomain|Description|
|-----|---------|-----------|
1	|Nutrient Calculation|	Algorithms used to calculate the nutritional requirements for individuals and the scoring system used to evaluate meal plans based on these requirements.
2	|Meal Plan Generation|	Functionality related to generating meal plans based on nutritional requirements.
3	|Edamame Api|	A database of food items that can be used in meal planning.
3	|Recipe CRUD Operations |	Functionality related to creating, reading, updating, and deleting recipes.
3	|Recipe Collections	|Functionality related to organizing recipes into collections.
3	|Social Media Sharing|	Functionality related to sharing data with others through social media.

- The "Nutrition" domain includes the "Nutrient Calculation" subdomain that focuses on the algorithms used to calculate the nutritional requirements for individuals and the scoring system used to evaluate meal plans based on these requirements. 
- The "Meal Planning" domain encompasses the "Meal Plan Generation" subdomain that is responsible for generating meal plans based on nutritional requirements. The "Recipe Management" subdomain is also part of the "Meal Planning" domain, which includes CRUD operations for recipes, recipe collections, and social media sharing.
- The "Nutrient Requirements" subdomain is responsible for defining the specific nutritional requirements of individuals, including the LBA, IA, and UBA. The "Shopping" subdomain provides functionality related to creating a shopping list for the ingredients required for meal plans. The "User Management" subdomain handles the creation and management of user accounts.
