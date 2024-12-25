
# JavaScript Array and Object Operations Guide

A comprehensive guide to common operations for working with arrays and objects in JavaScript. This guide includes various methods for transforming, filtering, and manipulating arrays of objects and converting between arrays and objects.

## Table of Contents
1. [Array to Object Conversions](#array-to-object-conversions)
2. [Filtering and Mapping](#filtering-and-mapping)
3. [Counting and Aggregation](#counting-and-aggregation)
4. [Sorting and Merging](#sorting-and-merging)
5. [Array Manipulation](#array-manipulation)
6. [Object Operations](#object-operations)
7. [Advanced Operations](#advanced-operations)

## Array to Object Conversions

### Convert Array of Objects to Single Object
```javascript
const arr = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' }
];

const result = arr.reduce((acc, obj) => {
  acc[obj.id] = obj.name;
  return acc;
}, {});

// Result: { 1: 'Alice', 2: 'Bob' }
```

## Filtering and Mapping

### Filter Objects and Extract Specific Properties
```javascript
const users = [
  { id: 1, name: 'Alice', age: 25 },
  { id: 2, name: 'Bob', age: 18 }
];

const result = users
  .filter(user => user.age >= 20)
  .map(user => user.name);

// Result: ['Alice']
```

## Counting and Aggregation

### Count Property Value Occurrences
```javascript
const data = [
  { type: 'fruit' },
  { type: 'vegetable' },
  { type: 'fruit' }
];

const result = data.reduce((acc, item) => {
  acc[item.type] = (acc[item.type] || 0) + 1;
  return acc;
}, {});

// Result: { fruit: 2, vegetable: 1 }
```

## Sorting and Merging

### Sort Array of Objects by Property
```javascript
const users = [
  { id: 1, name: 'Alice', age: 25 },
  { id: 2, name: 'Bob', age: 18 }
];

const result = users.sort((a, b) => a.age - b.age);

// Result: [
//   { id: 2, name: 'Bob', age: 18 },
//   { id: 1, name: 'Alice', age: 25 }
// ]
```

### Merge Arrays Based on Common Key
```javascript
const arr1 = [{ id: 1, name: 'Alice' }];
const arr2 = [{ id: 1, age: 25 }];

const result = arr1.map(item => ({
  ...item,
  ...arr2.find(obj => obj.id === item.id)
}));

// Result: [{ id: 1, name: 'Alice', age: 25 }]
```

## Array Manipulation

### Extract Unique Property Values
```javascript
const data = [
  { category: 'fruit' },
  { category: 'vegetable' },
  { category: 'fruit' }
];

const result = [...new Set(data.map(item => item.category))];

// Result: ['fruit', 'vegetable']
```

### Flatten Nested Arrays
```javascript
const data = [
  { id: 1, tags: ['a', 'b'] },
  { id: 2, tags: ['c', 'd'] }
];

const result = data.flatMap(item => item.tags);

// Result: ['a', 'b', 'c', 'd']
```

## Object Operations

### Add New Property to Objects
```javascript
const users = [
  { name: 'Alice' },
  { name: 'Bob' }
];

const result = users.map(user => ({
  ...user,
  isActive: true
}));

// Result: [
//   { name: 'Alice', isActive: true },
//   { name: 'Bob', isActive: true }
// ]
```

### Group Objects by Property
```javascript
const data = [
  { id: 1, type: 'fruit' },
  { id: 2, type: 'vegetable' },
  { id: 3, type: 'fruit' }
];

const result = data.reduce((acc, item) => {
  acc[item.type] = acc[item.type] || [];
  acc[item.type].push(item);
  return acc;
}, {});

// Result: {
//   fruit: [
//     { id: 1, type: 'fruit' },
//     { id: 3, type: 'fruit' }
//   ],
//   vegetable: [
//     { id: 2, type: 'vegetable' }
//   ]
// }
```

## Advanced Operations

### Find Maximum Value
```javascript
const data = [
  { id: 1, value: 10 },
  { id: 2, value: 20 }
];

const result = Math.max(...data.map(item => item.value));

// Result: 20
```

### Deep Copy Objects
```javascript
const data = [{ id: 1 }, { id: 2 }];
const result = JSON.parse(JSON.stringify(data));
```

### Transform Object to Array
```javascript
const obj = { a: 1, b: 2 };
const result = Object.entries(obj).map(([key, value]) => ({
  key,
  value
}));

// Result: [
//   { key: 'a', value: 1 },
//   { key: 'b', value: 2 }
// ]
```

## Contributing
Feel free to submit issues and enhancement requests.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

# JavaScript Array of Objects - Interview and Practice Questions

This document contains 20 practical JavaScript array of objects manipulation problems, demonstrating various array methods like `reduce()`, `map()`, `filter()`, `sort()`, and `some()`.

## Problem Set 1: Basic Array Operations

### 1. Find the Most Expensive Product

**Question**: Given an array of product objects, each having name, price, and category, find the most expensive product.

```javascript
const products = [
  { name: "Laptop", price: 1200, category: "Electronics" },
  { name: "Phone", price: 800, category: "Electronics" },
  { name: "Shoes", price: 150, category: "Fashion" },
  { name: "Headphones", price: 250, category: "Electronics" },
];

const mostExpensiveProduct = products.reduce((max, product) => {
  return product.price > max.price ? product : max;
});

console.log(mostExpensiveProduct);
// Output: {name: "Laptop", price: 1200, category: "Electronics"}
```

**Technique**: The `reduce()` method iterates over the array and keeps track of the product with the highest price.

### 2. Filter Products by Category

**Question**: Filter out all products from the "Electronics" category from the array of products.

```javascript
const electronicsProducts = products.filter(
  (product) => product.category === "Electronics"
);

console.log(electronicsProducts);
// Output: All Electronics category products
```

**Technique**: The `filter()` method selects all products that belong to the "Electronics" category.

### 3. Calculate Total Value of Products

**Question**: Calculate the total price of all the products in the array.

```javascript
const totalValue = products.reduce((sum, product) => sum + product.price, 0);

console.log(totalValue); // Output: Total sum of all product prices
```

**Technique**: The `reduce()` method sums up the prices of all products in the array.

## Problem Set 2: Advanced Array Manipulations

### 4. Find Products Within a Price Range

**Question**: Find products that cost between $200 and $1000.

```javascript
const affordableProducts = products.filter(
  (product) => product.price >= 200 && product.price <= 1000
);

console.log(affordableProducts);
// Output: Products within the specified price range
```

**Technique**: The `filter()` method is used to select products within a specified price range.

### 5. Check Product Category Uniformity

**Question**: Check if all products in the array belong to the "Electronics" category.

```javascript
const allElectronics = products.every(
  (product) => product.category === "Electronics"
);

console.log(allElectronics); // Output: true or false
```

**Technique**: The `every()` method checks if all products match the given condition.

## Additional Important Techniques

### Remove Duplicates

```javascript
const uniqueProducts = [
  ...new Map(products.map((product) => [product.name, product])).values(),
];
```

### Group Products by Category

```javascript
const groupedByCategory = products.reduce((group, product) => {
  const { category } = product;
  if (!group[category]) {
    group[category] = [];
  }
  group[category].push(product);
  return group;
}, {});
```

### Sort Products

```javascript
// Sort by price
const sortedByPrice = products.sort((a, b) => a.price - b.price);

// Sort alphabetically by name
const sortedByName = products.sort((a, b) => a.name.localeCompare(b.name));
```

## Key Takeaways

- `reduce()`: Powerful for aggregations and transformations
- `filter()`: Excellent for selecting subset of items
- `map()`: Great for transforming arrays
- `sort()`: Useful for ordering items
- `some()` and `every()`: Helpful for checking array conditions

## Best Practices

1. Use immutable methods when possible
2. Chain array methods for complex transformations
3. Use arrow functions for concise code
4. Consider performance for large arrays

## Learning Resources

- [MDN Web Docs: Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [JavaScript.info: Array Methods](https://javascript.info/array-methods)

## Contribution

Feel free to add more examples or improve existing ones!

## License

MIT

# Advanced JavaScript Array of Objects Interview Questions (Extended Set)

## Problem Set 3: Advanced Manipulation and Analysis

### 11. Complex Object Transformation and Filtering

**Question**: Transform an array of user objects with nested skills, filter users with specific skill proficiency, and create a summary.

```javascript
const users = [
  {
    id: 1,
    name: "Alice",
    skills: [
      { name: "JavaScript", level: 9 },
      { name: "React", level: 8 },
    ],
    department: "Engineering",
  },
  {
    id: 2,
    name: "Bob",
    skills: [
      { name: "Python", level: 7 },
      { name: "Machine Learning", level: 6 },
    ],
    department: "Data Science",
  },
];

// Find users with specific skill proficiency
const highSkillUsers = users.filter((user) =>
  user.skills.some((skill) => skill.name === "JavaScript" && skill.level >= 8)
);

// Transform users to skill summary
const skillSummary = users.map((user) => ({
  name: user.name,
  topSkill: user.skills.reduce((max, skill) =>
    skill.level > max.level ? skill : max
  ),
  totalSkillScore: user.skills.reduce((sum, skill) => sum + skill.level, 0),
}));

console.log(highSkillUsers);
console.log(skillSummary);
```

**Technique**: Nested array manipulation, `filter()`, `some()`, and multi-level `reduce()`.

### 12. Nested Object Deep Comparison

**Question**: Compare two arrays of complex objects with nested structures, identifying differences.

```javascript
const compareObjects = (arr1, arr2) => {
  const diffKeys = (obj1, obj2) => {
    const keys1 = Object.keys(obj1);
    const keys2 = Object.keys(obj2);
    return {
      added: keys2.filter((k) => !keys1.includes(k)),
      removed: keys1.filter((k) => !keys2.includes(k)),
      modified: keys1.filter(
        (k) =>
          keys2.includes(k) &&
          JSON.stringify(obj1[k]) !== JSON.stringify(obj2[k])
      ),
    };
  };

  return arr1
    .map((item, index) => ({
      index,
      changes: diffKeys(item, arr2[index] || {}),
    }))
    .filter(
      (change) =>
        change.changes.added.length ||
        change.changes.removed.length ||
        change.changes.modified.length
    );
};

const oldData = [
  { id: 1, name: "Product A", details: { price: 100 } },
  { id: 2, name: "Product B", details: { price: 200 } },
];

const newData = [
  { id: 1, name: "Product A", details: { price: 150 } },
  { id: 3, name: "Product C", details: { price: 300 } },
];

console.log(compareObjects(oldData, newData));
```

**Technique**: Deep object comparison, complex transformation and filtering.

### 13. Advanced Data Normalization

**Question**: Normalize a nested array of transaction data into a flat, aggregated structure.

```javascript
const transactions = [
  {
    user: { id: 1, name: "Alice" },
    purchases: [
      { product: "Laptop", amount: 1200, category: "Electronics" },
      { product: "Headphones", amount: 250, category: "Electronics" },
    ],
  },
  {
    user: { id: 2, name: "Bob" },
    purchases: [
      { product: "Shoes", amount: 150, category: "Fashion" },
      { product: "Watch", amount: 300, category: "Accessories" },
    ],
  },
];

const normalizedData = transactions.flatMap((transaction) =>
  transaction.purchases.map((purchase) => ({
    userId: transaction.user.id,
    userName: transaction.user.name,
    ...purchase,
  }))
);

const categorySummary = normalizedData.reduce((acc, transaction) => {
  if (!acc[transaction.category]) {
    acc[transaction.category] = {
      totalAmount: 0,
      userCount: new Set(),
      purchases: [],
    };
  }

  acc[transaction.category].totalAmount += transaction.amount;
  acc[transaction.category].userCount.add(transaction.userId);
  acc[transaction.category].purchases.push(transaction);

  return acc;
}, {});

console.log(normalizedData);
console.log(categorySummary);
```

**Technique**: `flatMap()`, nested object transformation, set-based aggregation.

### 14. Conditional Grouping and Scoring

**Question**: Create a sophisticated ranking system for products based on multiple criteria.

```javascript
const products = [
  {
    name: "Laptop",
    price: 1200,
    ratings: [4.5, 4.7, 4.6],
    features: ["touchscreen", "lightweight"],
    category: "Electronics",
  },
  {
    name: "Smartphone",
    price: 800,
    ratings: [4.2, 4.3, 4.1],
    features: ["5G", "camera"],
    category: "Electronics",
  },
];

const rankProducts = (products) => {
  return products
    .map((product) => ({
      ...product,
      averageRating:
        product.ratings.reduce((a, b) => a + b, 0) / product.ratings.length,
      // Feature complexity factor
      complexScore:
        5 -
        product.price / 500 + // Price factor (lower price = higher score)
        product.ratings.reduce((a, b) => a + b, 0) / product.ratings.length + // Rating factor
        product.features.length * 0.5,
    }))
    .sort((a, b) => b.complexScore - a.complexScore);
};

console.log(rankProducts(products));
```

**Technique**: Multi-dimensional scoring, complex sorting.

### 15. Dynamic Object Composition and Validation

**Question**: Create a flexible product validation and augmentation system.

```javascript
const validationRules = {
  name: (value) => value && value.length > 2,
  price: (value) => value > 0,
  category: (value) => ["Electronics", "Fashion", "Home"].includes(value),
};

const validateAndEnhanceProducts = (products) => {
  return products.map((product) => {
    const validationResults = Object.keys(validationRules).map((key) => ({
      field: key,
      isValid: validationRules[key](product[key]),
      value: product[key],
    }));

    return {
      ...product,
      isValid: validationResults.every((result) => result.isValid),
      validationDetails: validationResults,
      enhancedProduct: {
        ...product,
        id: product.id || Math.random().toString(36).substr(2, 9),
        createdAt: new Date().toISOString(),
      },
    };
  });
};

const products = [
  { name: "Laptop", price: 1200, category: "Electronics" },
  { name: "X", price: -50, category: "Invalid" },
];

console.log(validateAndEnhanceProducts(products));
```

**Technique**: Dynamic validation, object composition, metadata augmentation.

### 16. Time-based Data Analysis

**Question**: Analyze time-series data with complex aggregations and filtering.

```javascript
const salesData = [
  {
    date: "2023-01-15",
    product: "Laptop",
    revenue: 1200,
    region: "North",
  },
  {
    date: "2023-02-20",
    product: "Smartphone",
    revenue: 800,
    region: "South",
  },
];

const analyzeTimeSeries = (data) => {
  const monthlyRevenue = data.reduce((acc, sale) => {
    const month = sale.date.slice(0, 7);
    if (!acc[month]) {
      acc[month] = {
        totalRevenue: 0,
        productBreakdown: {},
        regions: new Set(),
      };
    }

    acc[month].totalRevenue += sale.revenue;
    acc[month].productBreakdown[sale.product] =
      (acc[month].productBreakdown[sale.product] || 0) + sale.revenue;
    acc[month].regions.add(sale.region);

    return acc;
  }, {});

  return monthlyRevenue;
};

console.log(analyzeTimeSeries(salesData));
```

**Technique**: Time-based aggregation, complex object construction.

### 17. Cross-referencing Multiple Arrays

**Question**: Match and enrich data across different arrays.

```javascript
const users = [
  { id: 1, name: "Alice", email: "alice@example.com" },
  { id: 2, name: "Bob", email: "bob@example.com" },
];

const orders = [
  { userId: 1, product: "Laptop", amount: 1200 },
  { userId: 2, product: "Smartphone", amount: 800 },
];

const reviews = [
  { userId: 1, rating: 4.5, comment: "Great product" },
  { userId: 2, rating: 4.2, comment: "Good experience" },
];

const enrichedData = users.map((user) => {
  const userOrders = orders.filter((order) => order.userId === user.id);
  const userReviews = reviews.filter((review) => review.userId === user.id);

  return {
    ...user,
    orders: userOrders,
    reviews: userReviews,
    totalSpent: userOrders.reduce((sum, order) => sum + order.amount, 0),
    averageRating:
      userReviews.reduce((avg, review) => avg + review.rating, 0) /
      userReviews.length,
  };
});

console.log(enrichedData);
```

**Technique**: Cross-array referencing, data enrichment.

### 18. Recursive Object Transformation

**Question**: Flatten and transform nested object hierarchies.

```javascript
const departments = [
  {
    name: "Engineering",
    teams: [
      {
        name: "Frontend",
        members: [
          { name: "Alice", role: "Developer" },
          { name: "Bob", role: "Designer" },
        ],
      },
      {
        name: "Backend",
        members: [{ name: "Charlie", role: "Architect" }],
      },
    ],
  },
];

const flattenDepartments = (departments) => {
  const flattenedEmployees = [];

  departments.forEach((dept) => {
    dept.teams.forEach((team) => {
      team.members.forEach((member) => {
        flattenedEmployees.push({
          departmentName: dept.name,
          teamName: team.name,
          ...member,
        });
      });
    });
  });

  return flattenedEmployees;
};

console.log(flattenDepartments(departments));
```

**Technique**: Recursive object flattening, nested structure transformation.

### 19. Dynamic Reporting and Aggregation

**Question**: Create a flexible reporting system with configurable metrics.

```javascript
const salesData = [
  {
    product: "Laptop",
    category: "Electronics",
    revenue: 1200,
    region: "North",
  },
  {
    product: "Smartphone",
    category: "Electronics",
    revenue: 800,
    region: "South",
  },
];

const createReport = (data, reportConfig) => {
  return reportConfig.reduce((report, config) => {
    const { type, field } = config;

    switch (type) {
      case "total":
        report[`total${field}`] = data.reduce(
          (sum, item) => sum + item[field],
          0
        );
        break;
      case "average":
        report[`average${field}`] =
          data.reduce((sum, item) => sum + item[field], 0) / data.length;
        break;
      case "groupBy":
        report[`groupBy${field}`] = data.reduce((groups, item) => {
          const key = item[field];
          groups[key] = (groups[key] || 0) + 1;
          return groups;
        }, {});
        break;
    }

    return report;
  }, {});
};

const reportConfig = [
  { type: "total", field: "revenue" },
  { type: "average", field: "revenue" },
  { type: "groupBy", field: "category" },
];

console.log(createReport(salesData, reportConfig));
```

**Technique**: Dynamic reporting, configurable aggregation.

### 20. Event Correlation and Tracking

**Question**: Correlate and analyze complex event streams.

```javascript
const events = [
  {
    type: "login",
    userId: 1,
    timestamp: "2023-06-01T10:00:00Z",
    details: { device: "mobile" },
  },
  {
    type: "purchase",
    userId: 1,
    timestamp: "2023-06-01T10:15:00Z",
    details: { product: "Laptop", amount: 1200 },
  },
  {
    type: "logout",
    userId: 1,
    timestamp: "2023-06-01T10:30:00Z",
    details: { duration: 1800 },
  },
];

const analyzeUserJourney = (events) => {
  const userJourneys = events.reduce((journeys, event) => {
    if (!journeys[event.userId]) {
      journeys[event.userId] = {
        events: [],
        timeline: [],
        summary: {},
      };
    }

    const journey = journeys[event.userId];
    journey.events.push(event);
    journey.timeline.push(event.timestamp);

    // Dynamic summary generation
    journey.summary[event.type] = (journey.summary[event.type] || 0) + 1;

    return journeys;
  }, {});

  return Object.entries(userJourneys).map(([userId, journey]) => ({
    userId: Number(userId),
    ...journey,
    journeyDuration:
      new Date(journey.timeline[journey.timeline.length - 1]) -
      new Date(journey.timeline[0]),
  }));
};

console.log(analyzeUserJourney(events));
```

**Technique**: Event correlation, complex journey tracking.

## Performance and Best Practices

- Use appropriate array methods based on data complexity
- Minimize nested iterations
- Consider performance for large datasets
- Leverage built-in JavaScript methods
- Use memoization for repeated complex calculations

## Emerging Patterns

- Functional programming approaches
- Immutable data transformations
- Composable and reusable logic
- Dynamic configuration

## Learning Paths

1. Master basic array methods
2. Understand complex transformations
3. Learn functional programming concepts
4. Practice with real-world scenarios

## Recommended Reading

- Functional JavaScript Programming
- Advanced JavaScript Techniques
- Data Manipulation Patterns
