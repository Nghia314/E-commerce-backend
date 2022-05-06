# E-commerce-backend
## Description
-  E-commerce-backend is an Api built onto express.js server that use sequelize to access to Mysql databases, and sequelize is a promise-based Node.js ORM. 
## E-commerce-backend demonstrate video and github link
- https://www.youtube.com/watch?v=ts8AyJVCEOQ - demonstrated  video url
- https://nghia314.github.io/E-commerce-backend/ - github deployed page
- https://github.com/Nghia314/E-commerce-backend - github repository page

## Table of contents
- Description
- E-commerce-backend demonstrate video and github link
- Table of contents
- Installation
- Usage
- Code snippet
- license
## Installation
`git clone`
 
`npm install mysql2`

`npm install sequelize`

`npm install dotenv`
## Usage
Run the following command in the root of your application:

`mysql -u root -p`
Enter PW
`source db/schema.sql`
`\q`
`npm run seed`
`npm start`
## Code snippet
The following code snippet shows how to get api by using find all, and the following code snippet shows how to find single caterogies by using findOne.
```
router.get('/', (req, res) => {
  // find all categories
  // be sure to include its associated Products
  Category.findAll({
    include: {
      model: Product,
      attribute: ['id', 'product_name', 'price', 'stock', 'catergory_id']
    }
  })
  .then(dbCatData => {
    if (!dbCatData) {
      res.status(404).json({ message: 'No category found' });
      return;
    }
    res.json(dbCatData);
  })
  .catch(err => {
    console.log(err);
    res.status(500).json(err);
  })
});

router.get('/:id', (req, res) => {
  // find one category by its `id` value
  // be sure to include its associated Products
  Category.findOne({
    where: {
      id: req.params.id
    },
    include: {
      model: Product,
      attribute: ['id','product_name', 'price', 'stock', 'catergory_id']
    }
  })
  .then(dbCatData => {
    if (!dbCatData) {
      res.status(404).json({ message: 'No category found' });
      return;
    }
    res.json(dbCatData);
  })
  .catch(err => {
    console.log(err);
    res.status(500).json(err);
  })
});
```
## Licenses
![Github licence](http://img.shields.io/badge/license-MIT-blue.svg)
This application is licensed under the MIT license
