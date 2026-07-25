## What Is This?
Database design and normalization is the process of organizing and structuring data in a database to ensure it is efficient, scalable, and easy to maintain. Think of it like a library where books are organized on shelves by genre, author, and title, making it easy to find a specific book. In a database, we organize data into entities, attributes, and relationships, making it easy to manage and query the data.

## How It Works Internally
### ERD (Entity Relationship Diagram) — Design Before Writing a Single Line of Code
An Entity Relationship Diagram (ERD) is a visual representation of the entities, attributes, and relationships in a database. It's like a blueprint for a building, showing the layout and connections between different rooms. An ERD helps us design the database structure before we start writing code.

### Entities, Attributes, and Relationships
Entities are like objects in the real world, such as customers or orders. Attributes are the characteristics of these entities, like a customer's name or address. Relationships define how entities interact with each other, like a customer placing an order. There are different types of relationships, such as one-to-many (a customer can have many orders) or many-to-many (an order can have many products, and a product can be part of many orders).

### 1NF — Atomic Columns, No Repeating Groups
First normal form (1NF) ensures that each column in a table contains only atomic values, meaning they cannot be broken down further. For example, a column for a customer's address should not contain multiple addresses, but rather a separate table for addresses with a foreign key referencing the customer. This is like having a separate address book for each customer.

### 2NF — No Partial Dependency on Composite Key
Second normal form (2NF) ensures that each non-key column in a table depends on the entire composite key, not just one part of it. This is like ensuring that a customer's order history is stored separately from their contact information.

### 3NF — No Transitive Dependency; Every Non-Key Column Depends Only on PK
Third normal form (3NF) ensures that if a table has a composite key, then each non-key column must depend on the entire composite key, not just one part of it. This is like ensuring that a product's price is stored separately from its description.

### When to Intentionally Denormalize — Pre-Compute Aggregates for Read Performance
Denormalization is the process of intentionally violating normal form rules to improve read performance. For example, pre-computing aggregates like total sales for a customer can improve query performance, but it requires additional maintenance to ensure data consistency.

### Always Index FK Columns — Prevents Full Table Scans on Joins
Indexing foreign key columns can significantly improve query performance by preventing full table scans when joining tables. This is like having a quick reference guide to find related information.

### Composite Keys vs Surrogate UUID PKs — Surrogate PKs Are Almost Always Better
Composite keys are keys made up of multiple columns, while surrogate keys are artificial keys, like UUIDs, that uniquely identify each row. Surrogate keys are often preferred because they are more efficient and flexible.

### Choosing FK Relationship vs Embedded JSONB — Relational Integrity vs Schema Flexibility
Foreign key relationships ensure data consistency between tables, while embedded JSONB allows for more flexible schema design. The choice between the two depends on the specific use case and performance requirements.

### Schema Decisions That Are Painful to Undo — Missing Indexes, Wrong Column Types, No Soft-Delete Strategy
Some schema decisions, like missing indexes or wrong column types, can be difficult and costly to change later on. A soft-delete strategy, which marks deleted rows as inactive instead of physically deleting them, can also be important for data recovery and auditing purposes.

## Syntax and Structure
```text
# Define entities, attributes, and relationships
entities:
  - customers
  - orders
  - products

# Define relationships between entities
relationships:
  - customers -> orders (one-to-many)
  - orders -> products (many-to-many)

# Define tables with attributes and foreign keys
tables:
  - customers:
      - id (primary key)
      - name
      - address
  - orders:
      - id (primary key)
      - customer_id (foreign key referencing customers)
      - order_date
  - products:
      - id (primary key)
      - name
      - price
  - order_items:
      - id (primary key)
      - order_id (foreign key referencing orders)
      - product_id (foreign key referencing products)
      - quantity
```

## Practical Example
```python
from sqlalchemy import create_engine, Column, Integer, String, ForeignKey
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker, relationship

# Create a database engine
engine = create_engine('postgresql://user:password@host:port/dbname')

# Create a base class for our models
Base = declarative_base()

# Define our models
class Customer(Base):
    __tablename__ = 'customers'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    address = Column(String)

class Order(Base):
    __tablename__ = 'orders'
    id = Column(Integer, primary_key=True)
    customer_id = Column(Integer, ForeignKey('customers.id'))
    customer = relationship('Customer', backref='orders')
    order_date = Column(String)

class Product(Base):
    __tablename__ = 'products'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    price = Column(Integer)

class OrderItem(Base):
    __tablename__ = 'order_items'
    id = Column(Integer, primary_key=True)
    order_id = Column(Integer, ForeignKey('orders.id'))
    order = relationship('Order', backref='order_items')
    product_id = Column(Integer, ForeignKey('products.id'))
    product = relationship('Product', backref='order_items')
    quantity = Column(Integer)

# Create the tables
Base.metadata.create_all(engine)

# Create a session
Session = sessionmaker(bind=engine)
session = Session()

# Add some data
customer = Customer(name='John Doe', address='123 Main St')
session.add(customer)
session.commit()

order = Order(customer_id=customer.id, order_date='2022-01-01')
session.add(order)
session.commit()

product = Product(name='Product A', price=10)
session.add(product)
session.commit()

order_item = OrderItem(order_id=order.id, product_id=product.id, quantity=2)
session.add(order_item)
session.commit()
```

## How This Connects to the Project
Before learning about database design and normalization, our project's database was a mess, with duplicate data and inefficient queries. After applying these concepts, our database is now organized, efficient, and easy to maintain. The `customers` table is used in the `orders` table through a foreign key, and the `orders` table is used in the `order_items` table through a foreign key. The `products` table is used in the `order_items` table through a foreign key. This matters to you because a well-designed database is essential for a scalable and maintainable project.

## Common Mistakes Beginners Make
**Wrong idea:** Thinking that database design is not important and can be done later.
**Correct idea:** Database design is crucial and should be done before starting to code. 
One common mistake is not indexing foreign key columns, which can lead to slow query performance. 
Another mistake is not using surrogate keys, which can lead to issues with data consistency. 
A missed configuration that can cause issues is not setting up a soft-delete strategy, which can lead to data loss. 
In an interview, you might be asked to design a database for a given scenario, and you should be able to explain your design decisions and why you chose certain data types and relationships.

## Verification Task 1
Your system shows slow query performance when retrieving customer orders. You have a large database with many customers and orders. Diagnose and fix the issue.
## Solution 1
The issue is likely due to the lack of indexing on the foreign key columns. To fix this, you can add an index to the `customer_id` column in the `orders` table and the `order_id` column in the `order_items` table.

## Verification Task 2
You are building a new e-commerce platform and need to decide between using a foreign key relationship or embedded JSONB to store order items. Defend your choice.
## Solution 2
I would choose to use a foreign key relationship to store order items. This is because foreign key relationships ensure data consistency and make it easier to query and maintain the data. Embedded JSONB can be useful for storing flexible schema data, but it can also lead to data inconsistencies and make queries more complex.

## Verification Task 3
You are given a code snippet that is supposed to retrieve all orders for a given customer, but it is not working correctly. Find and fix the bug.
```python
orders = session.query(Order).filter(Order.customer_id == customer.id)
```
## Solution 3
The bug is that the `orders` variable is a query object, not a list of orders. To fix this, you need to add a `.all()` method to the end of the query to execute it and retrieve the results.
```python
orders = session.query(Order).filter(Order.customer_id == customer.id).all()
```

## What Comes Next
The next topic is Database Migrations — Alembic. This topic is a natural follow-up to database design and normalization because it shows how to manage changes to the database schema over time. One concrete concept from this topic that will reappear in Database Migrations — Alembic is the use of SQLAlchemy's ORM to define and manage database tables.

## Reference Summary
Database design and normalization are crucial concepts for building efficient and scalable databases. A well-designed database should have a clear entity-relationship diagram, use normalization rules to ensure data consistency, and use indexing and surrogate keys to improve query performance. Common mistakes include not indexing foreign key columns, not using surrogate keys, and not setting up a soft-delete strategy. By applying these concepts, developers can build databases that are easy to maintain and query, and that support the needs of their applications. This matters to you because a well-designed database is essential for a successful project.