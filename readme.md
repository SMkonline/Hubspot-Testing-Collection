# 📘 HubSpot API Collection

This Postman Collection provides pre-built requests for interacting with the HubSpot CRM API. It covers key operations for Contacts, Deals, Products, Line Items, and Users, including dynamic test data generation and automatic associations.

## 📦 Overview

- **Platform**: [HubSpot CRM API v3](https://developers.hubspot.com/docs/api/crm)
- **Format**: Postman Collection v2.1
- **Authentication**: Bearer Token (set `access_token` in environment)

---

## 🔑 Environment Variables

| Key              | Description                    |
|------------------|--------------------------------|
| `access_token`   | Your HubSpot private app token |
| `contact_id`     | Generated after creating a contact |
| `deal_id`        | Generated after creating a deal |
| `productId`      | ID of the created product |
| `lineItemId`     | ID of the created line item |

---

## 📁 Folders & Requests

### 👤 Contacts

| Request         | Method | Description                  |
|-----------------|--------|------------------------------|
| Create Contact  | POST   | Creates a new CRM contact    |
| Get Contact     | GET    | Fetches a contact by ID      |

Automatically generates random:
- Email
- First & last names
- Company
- Phone number

---

### 💼 Deals

| Request         | Method | Description                          |
|-----------------|--------|--------------------------------------|
| Create Deal     | POST   | Creates a new deal associated with a contact |
| Get Deal        | GET    | Fetches a deal by ID                 |

Randomly selects a deal stage from HubSpot defaults.

---

### 🛍️ Products

| Request           | Method | Description                  |
|-------------------|--------|------------------------------|
| Create Product    | POST   | Creates a product with name, price, and SKU |
| Search Products   | POST   | Searches for products by name |

Random values generated:
- Product name (e.g., *Premium Laptop*)
- Description
- Price
- SKU

---

### 🧾 Line Items

| Request                    | Method | Description                     |
|----------------------------|--------|---------------------------------|
| Create Line Item           | POST   | Creates a new line item         |
| Associate Line Item to Product | POST | Batches line item with product  |
| Associate Line Item to Deal    | PUT   | Links line item with deal       |

Uses stored product and deal data for dynamic associations.

---

### 👥 Users

| Request                         | Method | Description                              |
|----------------------------------|--------|------------------------------------------|
| Search Users with Associated Deals | POST   | Filters users who have deals associated |

---

## 🧪 Tests & Automation

Every request includes:
- Pre-request scripts to generate dynamic variables
- Tests to assert success responses and store IDs
- Global scripts to check for token and validate response time

---

## 🚀 How to Use

1. **Import Collection** into Postman.
2. **Create an Environment** with the variable `access_token`.
3. **Run Requests** sequentially or via a Collection Runner.

---

## 🛡️ Notes

- Make sure to replace `{{access_token}}` with a valid token.
- IDs generated from one request are reused in others using environment variables.
- Some requests (like Line Item association) are conditional on existing values.

---

## 🤝 Contributing

This collection is designed to simplify testing HubSpot integrations. Feel free to fork or extend it for your use cases.

---

## 📄 License

MIT License
