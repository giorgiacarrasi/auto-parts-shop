# Database Module - Exam 

## Preface
The main aim is to automate the management system of a car parts warehouse.
The specifications of the system, acquired through interview, are those below reported.
Analyze these specifications, filter the ambiguities present and then group them in a homogeneous way.
Identify the links between the various groups of specifications thus obtained.
Realize the design of the conceptual model and represent the specifications (after the phase of
reorganization) with a schema of the Entity-Relationship model. Carry out the logical design
of the database of the information system and its implementation both in the relational model
than in a non relational model based on document management.

## Specifications
Consider a database that contains information about the purchases of customers of a store of
car parts.
Customers are interested in the tax code or VAT number, which identifies them, the name, the address of residence
complete with zip code, city, province and region.
Of each expense of a customer concern the number of the invoice, which identifies it, the date, the total of
shopping, the method of payment (electronic, cash) and, for each product, the quantity, the price
paid and any discount applied (product on promotion).
Of each part concerned the code, which identifies it, the description, the category, the vehicles
compatible, the unit cost and the selling price. Products may be affected by
promotions, with temporary price reduction, from a certain date and for a number
set of days.

## Required SQL queries 

1. For a specific customer, determine the quantities of each product purchased in a
given period;
2. For a given product, determine the number of distinct customers who have
purchased in a given period;
3. Identify all customers who have purchased a promotional product, indicating the
Postal code of residence;
4. For a specific CAP, identify customers who have made purchases in a particular CAP
period;
5. For a specific car model, identify the turnover of the items in a given
period;
6. For each promotion item, determine the quantity sold in a given item
period;
7. Customers who have not made an electronic payment in the current year;
8. The customer who has spent more in a given period;
9. For a specific postal code, the average expenditure per invoice over a given period;
10. For each category of product, the total price paid for those sold in a
given period.

## Analysis 

### Assumptions
Given the current database the following assumptions are made: 

-  It's assumed that all Italian Regions, Provinces, Cities and Postcodes are present in the database
-  Every customer in the database purchased at least once at the car parts warehouse
-  Each product belongs to a single category
-  Each replacement is compatible with one or more vehicles
-  The invoice number is equivalent to the receipt of purchase
-  One or more products belong to a promotion
-  A product may have 0 or N promotions
-  If the Brand is present has at least one vehicle in the database

## Key-points related to the main entities: 
-	Key-points related to Customer: For each customer it’s known about name, surname, identifiy code and residence address. A customer could be a Company or a Private Customer.
-	Key-points related to Order: For each order that is placed it’s known a identify code and the data where order has been placed. Each order contains one or more products.
-	Key-points related to Vehicle: For each vehicle it’s known a identify code and the name vehicle. Each vehicle is producted by a Brand that we identify with a ID code and the brand name. 
-	Key-points related to Product: Each product is marked with a identify code, the name, a short description, the selling price, the unit cost price. A product could be on sale or not. If the product is on sale it’s known a identifier code that mark the product on sale, the percentage off, and the data where promotion starts and ends. 
-	Key-points related to Payment: When an order is placed the customer does the payment. The payment could be with cash or electronic. For the last one we know also the identifier transaction code.

# Glossary Terms
|     **Terms**    |     **Synonymous**                                                                      |     **LinkedTo**                    |     **Description**                                                                                                            |
|------------------|-----------------------------------------------------------------------------------------|-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
|     Customer     |     User/Buyer                                                                          |     Shopping,   Product             |     A person that   buys on a shopping session.                                                                                |
|     Expense      |     /                                                                                   |     Customer,   Product             |     Total   purchases during a shopping session made by a Customer                                                             |
|     Product      |             /                                                                           |     Expense,   Product              |     Product is   contained in Expense. It could be buy in quantities that Customer needs, and   it could be on sale or not.    |
|     Promotion    |     Reduction of   Price Cost                                                           |     Product                         |     A special percentage   off on a price product. This condition could interest one or more product or   neither.             |
|     Payment      |             /                                                                           |     Expense,   Product, Customer    |     An order   could be pay using more than a Payment Type. Cash or electronic payment.                                        |
| Category         | A category standardizes a group of products that share similar qualities or functions.  |     /                               | Product                                                                                                                        |
# ER Model 
## First Version 

[IMMAGINE SCHEMA] 

On the first version we can find different entities.
- **Customer**: this entity represents a person who buy prodcuts at the special parts shop. The Customer has some data that we use to identify himself. The <mark>id_code</mark> is the unique code client. We know also the _Residence Address_ and general informations as name and surname. The entity presents the specification _Company_ or _PrivateCustomer_ useful to understand the type of Customer. Based on the result the Customer will be associated on the attribute _VAT_ or _id_code_. 

A Customer could place one or more order. 

- **Order**: the entity _order_ represents the purchase that could contains at least one or more products. Each order got the idenitifier code, _id_code_, and the data where is placed. 

A order belongs to a single customer. 


