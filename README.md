# final-java-project

classDiagram
    OnlineShop
    User <|-- Customer
    User <|-- Seller
    User <|-- Admin
    Product <|-- Electronics
    Product <|-- Books
    Product <|-- Clothing
    Product <|-- Jewelry
    Product <|-- Cars

class OnlineShop {
        -String name
        -String webAddress
        -String supportNumber
        -List<Product> products
        -List<Order> orders
        -double totalProfit
        -List<User> users
        +getProducts()
        +getUsers()
        +OnlineShop(name, webAddress, supportNumber)
        +registerUser(user)
        +loginUser(username, password)
        +addProduct(product)
        +listProducts()
        +addOrder(order)
        +approveOrder(order)
        +viewTotalProfit()
        +registerAdmin(admin)
        +listProductsWithDetails()
    }

class User {
        -String username
        -String password
        -String email
        -String phoneNumber
        -String address
        -ShoppingCart cart
        -List<Order> orders
        -List<Product> purchasedProducts
        -double wallet
        +User(username, password, email, phoneNumber, address)
        +placeOrder(shop)
        +getUsername()
        +getPassword()
        +addFunds(amount)
        +viewProfile()
        +addToCart(product, quantity)
        +viewCart()
        +requestFunds(amount, admins)
    }

class Customer {
        +Customer(username, password, email, phoneNumber, address)
    }

class Seller {
        -String companyName
        -List<Product> availableProducts
        -boolean isApproved
        +Seller(companyName, username, password, email, phoneNumber, address)
        +setApproved(isApproved)
        +addProduct(product, shop)
    }

class Admin {
        -List<FundRequest> fundRequests
        +Admin(username, password, email, phoneNumber, address)
        +registerNewAdmin(shop, newAdmin)
        +receiveFundRequest(user, amount)
        +viewFundRequests()
        +approveFundRequest(index)
        +approveSeller(seller)
    }

class Product {
        -String name
        -double price
        -int inventory
        -List<Review> reviews
        +Product(name, price, inventory)
        +reduceInventory(quantity)
        +getName()
        +getPrice()
        +getInventory()
        +addReview(review)
        +toString()
        +getDetailedInfo()
    }

class Electronics {
        +Electronics(name, price, inventory)
    }

class Books {
        +Books(name, price, inventory)
    }

class Clothing {
        +Clothing(name, price, inventory)
    }

class Jewelry {
        +Jewelry(name, price, inventory)
    }

class Cars {
        +Cars(name, price, inventory)
    }

class ShoppingCart {
        -Map<Product, Integer> products
        +ShoppingCart()
        +addProduct(product, quantity)
        +viewCart()
        +getProducts()
        +clearCart()
    }

class Order {
        -User user
        -Map<Product, Integer> products
        -double totalCost
        -boolean isApproved
        +Order(user, products)
        +calculateTotalCost()
        +getTotalCost()
        +isApproved()
        +setApproved(approved)
        +toString()
    }

class Review {
        -String reviewer
        -String comment
        -int rating
        +Review(reviewer, comment, rating)
        +toString()
    }

class FundRequest {
        -User user
        -double amount
        +FundRequest(user, amount)
        +getUser()
        +getAmount()
        +toString()
    }
