# SQL_projects

create database pizzahut;

SELECT * FROM pizzahut.pizzas;

SHOW columns FROM pizzahut.orders; 

create table orders( order_id int not null	,
order_date date not null,
order_time time not null,
primary key (order_id));


Q1.  retrive the total numbers of orders placed

select count(order_id) as total_orders from orders;

Q2. calcualte the total revenue generated from pizza sales.

SELECT 
    SUM(order_details.quantity * pizzas.price)
FROM
    order_details
        JOIN
    pizzas ON order_details.pizza_id = pizzas.pizza_id; 
    
Q3. identify the highest priced pizza

select pizza_types.name, pizzas.price from pizza_types join pizzas on pizza_types.pizza_type_id = pizzas.pizza_type_id
order by pizzas.price desc limit 1 ;  

Q4. identify the most common pizza size ordered 

SELECT 
    quantity, COUNT(order_details_id)
FROM
    order_details
GROUP BY quantity;

secondquery

SELECT 
    pizzas.size,
    COUNT(order_details.order_details_id) AS order_count
FROM
    pizzas
        JOIN
    order_details ON pizzas.pizza_id = order_details.pizza_id
GROUP BY pizzas.size
ORDER BY order_count DESC;




