Introduction:
In this assessment, you will be tasked with designing a solution to consolidate transactional databases into a data warehouse. The task involves processing a MongoDB transactional database. Your goal is to choose a database for the data warehouse, implement a working application/data pipeline to continuously load data into data warehouse. Ensure data correctness, and data freshness. This note will guide you through the situation, questions, and offer advice to help you succeed in this assignment.

Objective: Implement a solution to consolidate MongoDB transactional databases into a data warehouse.

Database Information:

  - Data Credential: `Provided by FeedMe`

  - Data Model:
    | Enum: ITEM_STATUS |               |                |                  |
    |-------------------|---------------|----------------|------------------|
    | Value             | Meaning       |                |                  |
    | `draft`           | Draft         |                |                  |
    | `served`          | Served        |                |                  |
    | `canceled`        | Canceled      |                |                  |

    | Enum: ORDER_STATUS |               |                   |                  |
    |---------------------|---------------|-------------------|------------------|
    | Value               | Meaning       |                   |                  |
    | `draft`             | Draft         |                   |                  |
    | `completed`         | Completed     |                   |                  |
    | `voided`            | Voided        |                   |                  |

    | Interface: IItem   |               |                  |                  |
    |--------------------|---------------|------------------|------------------|
    | Property           | Type          | Description      |                  |
    | `name`             | string        | Item name        |                  |
    | `status`           | ITEM_STATUS   | Item status      |                  |
    | `quantity`         | number        | Item quantity    |                  |
    | `price`            | number        | Item price       |                  |
    | `total`            | number        | Total cost       |                  |

    | Interface: IOrder  |               |                  |                  |
    |--------------------|---------------|------------------|------------------|
    | Property           | Type          | Description      |                  |
    | `status`           | ORDER_STATUS  | Order status     |                  |
    | `items`            | IItem[]       | Array of items   |                  |
    | `total`            | number        | Order total      |                  |
    | `timestamp`        | Date          | Order timestamp  |                  |
    | `merchantId`       | number        | Merchant ID      |                  |

Control Panel URL: [FeedMe Data Engineer Control Panel](https://feedme-data-engineer-assessment-frontend.pages.dev/)
  - Validation Queries:
    - Sales: Aggregate sum of order items' total.
    - Quantity: Aggregate count of orders.
    - Item Quantity: Aggregate sum of order items' quantity.
  - Control Panel Features:
    - Random Button: Randomly creates/updates/deletes data in the transactional database. Ensure this data successfully loads into the data warehouse.
    - Reset Button: Resets data to the initial state; may take a few minutes.
 
Requirements:
  1. Generate the results for the three queries mentioned above to validate data correctness.
  2. Press the "RANDOM" button in the Control Panel, and rerun the three queries to validate data correctness.
  3. Evaluate the data freshness, ensuring that the data is synced to the data warehouse as soon as possible.
  
Tips:
  - Choose a database your are familiar with. Priorize data correctness and data freshness instead of query performance.
  - Avoid overengineering, scope your working hours within 3 hours, or 1 hour per day if busy.
  - Consider leveraging the MongoDB Change Stream API if needed.