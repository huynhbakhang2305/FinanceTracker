# FinanceTracker
📌 Personal Finance Management System


Name: Huynh Ba Khang
Final Exam – MongoDB & Streamlit

📖 Introduction

This project is a personal finance management system built with Python, Streamlit, and MongoDB.
The application allows users to manage categories, transactions, and budgets in a multi-user environment, ensuring data integrity, validation, and data leak prevention.

The project focuses on solving critical backend problems using MongoDB operations and is designed to satisfy the final exam requirements.

🛠️ Technologies Used

Python

Streamlit

MongoDB (PyMongo)

MongoDB Aggregation Pipeline

Google OAuth Login

👤 User Authentication

Users log in using Google Authentication

Each user has a unique user_id

All data (categories, transactions, budgets) is strictly scoped by user_id to prevent data leaks

✅ Implemented Exam Topics
🔹 Topic 2 – Category Delete (3 points)
🎯 Problem

When deleting a category, related transactions may become orphaned, leading to data inconsistency.

🧠 Solution

A safe category deletion mechanism is implemented with three strategies:

Block

Prevents deletion if there are transactions using the category.

Reassign

Reassigns affected transactions to a default category (Others).

Cascade

Deletes all transactions related to the category.

🔧 Implementation

Implemented in category_model.py

Uses MongoDB operations:

count_documents

update_many

delete_many

delete_one

🖥️ UI Support

Displays number of affected transactions

Allows user to select delete strategy

Requires confirmation before deletion

✔️ Ensures no orphan transactions
✔️ Maintains data integrity

🔹 Topic 6 – Transaction Validation (3 points)
🎯 Problem

Transactions may be created or updated with invalid categories, causing inconsistent data.

🧠 Solution

Before adding or updating a transaction:

The system validates whether the selected category exists for the current user

Invalid transactions are rejected immediately

🔧 Implementation

Implemented in transaction_model.py

Validation applied to:

add_transaction

update_transaction

Uses:

Category existence check via MongoDB

User-based data scoping

✔️ Result

Prevents invalid category usage

Ensures transaction-category consistency

Fully complies with validation requirements

🔹 Topic 3 – User Deletion & Data Leak Prevention (3 points)
🎯 Problem

Deleting a user without cleaning related data may cause data leaks and leave unused records in the database.

🧠 Solution

A secure user deletion process is implemented:

Deletes the user

Deletes all related data:

Transactions

Budgets

Categories

🔧 Implementation

Implemented in user_model.py

Uses MongoDB:

delete_many

delete_one

Returns a deletion summary for verification

✔️ Result

No leftover data

No cross-user data access

Ensures complete data isolation

🔐 Data Security & Integrity

Every query includes user_id

Prevents unauthorized access to other users’ data

No shared data between users

🧪 Testing

All features tested locally

MongoDB Atlas used for deployment

Edge cases handled:

Invalid category

Deleting category with existing transactions

Deleting users with existing data

✅ Conclusion

This project successfully fulfills the required exam topics:

Category Delete Safety

Transaction Validation

User Deletion & Data Leak Prevention

All requirements are implemented using MongoDB best practices, ensuring correctness, security, and scalability.
