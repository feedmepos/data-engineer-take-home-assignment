## FeedMe Data Engineer Take Home Assignment
Below is a take home assignment before the interview of the position. You are required to
1. Understand the situation and use case. You may contact the interviewer for further clarification.
2. Fork this repo and implement the requirement with your most familiar tools.
3. Complete the requirement and perform your own testing.
4. Provide documentation for the any part that you think is needed.
5. Commit into your own github and share your repo with the interviewer.
6. Bring the source code and functioning prototype to the interview session.

### Introduction
In this assignment, your objective is to design a solution for the efficient movement and transformation of data from a database to a data warehouse.
You have to host a SQL database as data warehouse, and build a data pipeline to continuously load data into data warehouse.

Data correctness: it is important to maintain data correctness.

Data freshness: it will be a plus if data changes reflect to data warehouse as soon as possible.

### Database Information

  - MongoDB

  - Credential: `Provided by FeedMe`

  - Data Model:
    | Enum: ITEM_STATUS |               |
    |-------------------|---------------|
    | Value             | Meaning       |
    | `draft`           | Draft         |
    | `served`          | Served        |
    | `canceled`        | Canceled      |

    | Enum: ORDER_STATUS  |               |
    |---------------------|---------------|
    | Value               | Meaning       |
    | `draft`             | Draft         |
    | `completed`         | Completed     |
    | `voided`            | Voided        |

    | Interface: Item    |               |                  |
    |--------------------|---------------|------------------|
    | Property           | Type          | Description      |
    | `name`             | string        | Item name        |
    | `status`           | ITEM_STATUS   | Item status      |
    | `quantity`         | number        | Item quantity    |
    | `price`            | number        | Item price       |
    | `total`            | number        | Total cost       |

    | Interface: Order   |               |                  |
    |--------------------|---------------|------------------|
    | Property           | Type          | Description      |
    | `status`           | ORDER_STATUS  | Order status     |
    | `items`            | Item[]        | Array of items   |
    | `total`            | number        | Order total      |
    | `timestamp`        | Date          | Order timestamp  |
    | `merchantId`       | number        | Merchant ID      |

### Control Panel 
  - [FeedMe Data Engineer Control Panel](https://feedme-data-engineer-assessment-frontend.pages.dev/)
  - Control Panel Features:
    - Random Button: Randomly creates/updates/deletes data in the database.
    - Reset Button: Resets database to the initial state; may take a few minutes to fully reset.
  - Validation Queries:
    - Sales: Aggregate sum of order items' total.
    - Quantity: Aggregate count of orders.
    - Item Quantity: Aggregate sum of order items' quantity.
 
### Demo
  1. From data warehouse, generate the results for the three queries mentioned above to validate data correctness.
  2. In the Control Panel, press "RANDOM" button to mock data changes, rerun step 1 queries to validate data correctness.
  3. Evaluate the data freshness, ensuring that the data is synced to the data warehouse as soon as possible.
  
### Tips
  - Choose the SQL database you are most familiar with as the data warehouse. 
  - Priorize data correctness and data freshness instead of query performance in this assignment.
  - Everything can be hosted locally if it will be more convenient for you.
  - Consider utilizing [MongoDB Change Stream API](https://www.mongodb.com/docs/manual/changeStreams/#change-streams) if needed.
  - Avoid overengineering, scope your working hours within 3 hours, or 1 hour per day if busy.