# Object-Relational Mapping (ORM): E-Commerce Back End


DEMO VIDEO
https://drive.google.com/file/d/1DAJp657QAyHPHT0qt49vZHPR1D8ErWvy/view?usp=sharing

DEPLOYABLE APPLICATION
<to be inserted here after initial deployment>

## Description

This application will serve as the back end for an e-commerce site. Specifically, it involves managing a database with four models: `Category`, `Product`, `Tag`, and `ProductTag`.

## Installation

1. Clone the repository and install dependencies.

```bash
# Clone the repository
git clone <your-repo-link>

# Navigate to the project directory
cd <your-repo-name>

# Install dependencies
npm install
```

2. Update the `.env` file to specify your database authentication.
3. Run the `schema.sql` file in MySQL Shell. _See the [walkthrough video](#walkthrough-video)._

```
\sql
\connect root@localhost:3306 (then enter your password in the prompt)
\source "path to schema"
```

4. Run the `seed.js` file.

```bash
npm run seed
```

5. You may now test using Insomia or other apps.

## API Usage

This application provides a RESTful API. Here are some example requests you can make using Insomnia:

- Get all categories: `GET http://localhost:3001/api/categories`
- Get a single category by id: `GET http://localhost:3001/api/categories/{id}`
- Create a new category: `POST http://localhost:3001/api/categories` with JSON body `{ "category_name": "New Category" }`
- Update a category: `PUT http://localhost:3001/api/categories/{id}` with JSON body `{ "category_name": "Updated Category" }`
- Delete a category: `DELETE http://localhost:3001/api/categories/{id}`

Similar endpoints exist for `Product`, `Tag`, and `ProductTag` models.

## Database Models

- `Category`
  - `id`
    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.
  - `category_name`
    - String.
    - Doesn't allow null values.
- `Product`
  - `id`
    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.
  - `product_name`
    - String.
    - Doesn't allow null values.
  - `price`
    - Decimal.
    - Doesn't allow null values.
    - Validates that the value is a decimal.
  - `stock`
    - Integer.
    - Doesn't allow null values.
    - Set a default value of `10`.
    - Validates that the value is numeric.
  - `category_id`
    - Integer.
    - References the `Category` model's `id`.
- `Tag`
  - `id`
    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.
  - `tag_name`
    - String.
- `ProductTag`
  - `id`
    - Integer.
    - Doesn't allow null values.
    - Set as primary key.
    - Uses auto increment.
  - `product_id`
    - Integer.
    - References the `Product` model's `id`.
  - `tag_id`
    - Integer.
    - References the `Tag` model's `id`.

### Associations

You'll need to execute association methods on your Sequelize models to create the following relationships between them:

- `Product` belongs to `Category`, and `Category` has many `Product` models, as a category can have multiple products but a product can only belong to one category.

- `Product` belongs to many `Tag` models, and `Tag` belongs to many `Product` models. Allow products to have multiple tags and tags to have many products by using the `ProductTag` through model.

## Walkthrough Video

[Walkthrough Video Link](https://www.google.com)

## Contributing

If you're open to contributions, provide instructions on how to do so.

## License

MIT
