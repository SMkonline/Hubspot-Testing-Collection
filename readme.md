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

## 🔐 Getting Your Access Token

### Creating a Private App

1. **Access Private Apps**:
   - Log in to your HubSpot account
   - Navigate to Settings (⚙️) > Integrations > Private Apps
   - Click "Create private app"

2. **Configure the App**:
   - **Basic Info**:
     - Name your app (e.g., "API Testing App")
     - Add a description
     - Upload an optional logo
   
   - **Required Scopes**:
     - `crm.objects.contacts` - for Contacts API
     - `crm.objects.deals` - for Deals API
     - `crm.objects.products` - for Products API
     - `crm.objects.line_items` - for Line Items API
     - `crm.objects.owners` - for Users API

   - **Webhook Configuration** (Optional):
     - In the "Webhooks" tab of your private app:
       1. Enable "Select specific subscription types"
       2. Choose the events you want to monitor:
          - `contact.creation` - When contacts are created
          - `contact.propertyChange` - When contact properties change
          - `deal.creation` - When deals are created
          - `deal.propertyChange` - When deal properties change
          - `product.creation` - When products are created
          - `product.propertyChange` - When product properties change
       3. Set your Target URL where webhooks will be sent
       4. Configure webhook settings:
          - Select authentication method (Basic Auth/Bearer Token)
          - Set rate limiting preferences
          - Choose retry settings for failed webhooks
       5. Test your webhook endpoint using HubSpot's test feature

     **Webhook Security Best Practices**:
     - Use HTTPS for your webhook endpoint
     - Implement webhook signature validation
     - Set up proper authentication for your endpoint
     - Monitor webhook delivery status in HubSpot
     - Configure retry attempts for failed deliveries

3. **Get Your Token**:
   - Click "Create app"
   - Copy the generated access token immediately
   - Format: `pat-na1-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`

### Security Best Practices

- Never share or commit your access token
- Store it securely in environment variables
- Create separate apps for different environments
- Regularly audit and remove unused apps
- Token can be revoked and regenerated if compromised

---

## 📄 License

MIT License
