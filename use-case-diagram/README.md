# Airbnb Use Case Diagram

## 📌 Overview
This diagram presents the **Use Case Diagram** for the **Airbnb Property Booking System**.  
The diagram illustrates the main actors and their interactions with the system, focusing on how users (guests, hosts and admin) and external services engage with the platform.



## Purpose
The purpose of this diagram is to provide a high-level view of the system’s functionality, identifying:

- **Primary Actors** (Guest, Host, Admin, Payment Gateway)  
- **Key Use Cases** (like Search Property, Book Property, Make Payment, Manage Listings)  
- **System Boundaries** showing what belongs inside Airbnb’s platform and what involves external entities  



##  Actors and Their Interactions

###  Guest 
The **Guest** is the primary user who searches and books properties.  

**Main Use Cases:**
-  **Search Property** – Look for available listings by location, date, and filters.  
-  **View Property Details** – View photos, amenities, price, and reviews.  
-  **Book Property** – Submit a reservation request for a chosen property.  
-  **Make Payment** – Complete payment through the integrated payment gateway.  
- **Manage Bookings** – View, modify, or cancel existing reservations.  
- **Leave Review** – Provide feedback after completing a stay.  



### 🏠 Host (Property Owner)
The **Host** lists and manages properties for booking.  

**Main Use Cases:**
- **List Property** – Add new properties with details, photos, and pricing.  
- **Update Property** – Edit property details (availability, price, amenities).  
-  **Remove Property** – Unlist properties when unavailable.  
-  **Manage Bookings** – Approve or decline booking requests.  
-  **Communicate with Guests** – Respond to guest inquiries or booking questions.  
-  **Review Guest** – Provide reviews for guests after stays.  


###  Admin (Platform Manager)
The **Admin** ensures system integrity and manages compliance.  

**Main Use Cases:**
-  **Verify User Accounts** – Approve or reject guest and host registrations.  
-  **Verify Listings** – Review property details to ensure compliance.  
-  **Monitor Transactions** – Track payments and booking activities.  
-  **Handle Disputes** – Resolve conflicts between guests and hosts.  
-  **Manage Platform Policies** – Enforce rules, terms of service, and community guidelines.  


##  Notes
- The **Payment Gateway** is an **external system** that handles secure payment transactions.  
- The **System Boundary** represents all functionalities managed by Airbnb’s platform.  
