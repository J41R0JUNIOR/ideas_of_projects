Template project -> [BackEnd](https://github.com/J41R0JUNIOR/PicPay-Simplified)

### 💸 Simplified PicPay

**Simplified PicPay** is a simplified payment platform where users can deposit and transfer money between each other. The application was built with a focus on secure operations, well-defined business rules, and integration with simulated external services.

---

### 📌 Objective

Allow money transfers between users with appropriate validations, authentication, and notifications.

---

### 🧑‍💼 User Types

- **Common User**: Can **send and receive** transfers.
- **Merchant**: Can **only receive** transfers.

---

### 📝 Registration Requirements

All users must have:

- Full Name  
- CPF/CNPJ (must be unique)  
- Email (must be unique)  
- Password  

---

### 🔁 Transfer Rules

- **Common users** can send money to other users or merchants.  
- **Merchants** **cannot** send money, only receive.  
- The system must check if the **payer has sufficient balance** before making the transfer.  
- The transfer operation **must be transactional**. If something fails, the money must be refunded to the payer.  
- Before completing the transfer, the system must consult an **external authorization service**:

GET https://util.devi.tools/api/v2/authorize


- After the transfer, a **notification** must be sent to the recipient (user or merchant) via an external service:

POST https://util.devi.tools/api/v1/notify


⚠️ This service may be unavailable or unstable.

---

### 🔗 Transfer Endpoint

You can use the following endpoint to make a transfer:

**POST** `/transfer`  
**Content-Type**: `application/json`

### ✅ Example Payload:

```json
{
  "value": 100.0,
  "payer": 4,
  "payee": 15
}
