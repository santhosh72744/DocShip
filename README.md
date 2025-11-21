DocShip – International Document Courier Platform

DocShip is a complete end-to-end web application that allows users to estimate shipping charges, enter addresses, auto-extract address details, make payments, and generate a final shipping label for sending documents from USA → India using FedEx or UPS.

🚀 Features
1. Shipment Estimation

User selects:

Shipping type (Document)

Source Country (USA)

Destination Country (India)

5-digit U.S. ZIP

6-digit Indian PIN

Backend validates ZIP and PIN.

Estimate returned includes:

Price in INR + USD

Delivery days (FedEx: 5 days, UPS: 7 days)

2. Address collection 

DocShip includes an intelligent auto address parser.

Users can paste a full address, and the system automatically extracts.


If the user prefers manual input, the app supports full address entry:



4. Payment Processing

Users enter:

Card Number

Name on Card

Expiry

CVV

Backend saves payment details and returns:

Payment Reference ID

5. Shipping Label Generation

After successful payment:

Shipment is saved

Tracking number is generated

Payment reference saved

Final shipping label displays:

Courier (FedEx/UPS)

Tracking Number

Pickup & Destination addresses

Paid amount

6. Local Storage Persistence

All progress is saved automatically:

If user refreshes the page: nothing is lost

App restores:

Current step

All form values

Estimate

Payment details

Tracking number

A Reset button clears everything and returns user to Step 1.

🏗️ Tech Stack
Frontend

React (Functional Components)

Hooks: useState, useEffect

LocalStorage for state persistence

Address parsing logic

Components:

App.js

CheckoutForm.js

PaymentModal.js

ShippingLabel.js

stepNavigator.js

validations.js

Backend

Node.js + Express

JSON File Storage (acts as DB)

shipments.json

payments.json

Validates ZIP & PIN

endpoints:

/api/estimate

/api/save-shipment

/api/save-payment

📁 Project Structure
docship/
│
├── frontend/
│   ├── src/
│   │   ├── App.js
│   │   ├── CheckoutForm.js
│   │   ├── PaymentModal.js
│   │   ├── ShippingLabel.js
│   │   ├── stepNavigator.js
│   │   ├── validations.js
│   │   ├── addressParser.js   <-- (if in separate file)
│   │   ├── App.css
│   │   └── ...
│   └── public/
│
└── backend/
    ├── server.js
    ├── shipments.json
    ├── payments.json
    └── utils/

📦 API Endpoints
POST /api/estimate

Returns shipping price and days.

POST /api/save-shipment

Stores shipment, returns tracking number.

POST /api/save-payment

Stores payment, returns payment reference ID.

🧪 Validation Rules
ZIP (USA)

Must be exactly 5 digits

Backend-validated

PIN (India)

Must be exactly 6 digits

Only supported city ranges allowed

Modal displays supported PIN list

🔄 Reset Functionality

Clears all React state

Clears localStorage (docshipData)

Returns to Step 1

Used to start a completely new shipment

🛠️ Running the Project
Frontend
cd frontend
npm install
npm start

Backend
cd backend
npm install
node server.js


Backend runs at:

http://localhost:5000

📌 Future Enhancements

Add more couriers

Real courier API integration (FedEx/UPS API)

Auto-detect country from address

PDF export for shipping label

User accounts + shipment history

Email/SMS notifications
