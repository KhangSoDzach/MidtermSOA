# iBanking Tuition Payment System

A web-based tuition payment system built with Node.js, Express, and MongoDB. This application allows students to search for their tuition fees and complete payments through an online banking interface.

## 🌟 Features

- **User Authentication**: Secure login with JWT tokens
- **Tuition Search**: Search tuition fees by student ID
- **Payment Processing**: Create and complete tuition payments with OTP verification
- **Payment History**: View transaction history
- **Email Notifications**: Receive OTP codes and payment confirmations via email
- **Account Management**: View account balance and profile information

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB](https://www.mongodb.com/try/download/community) (v4.4 or higher)
- npm (comes with Node.js)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/KhangSoDzach/Midterm.git
cd Midterm
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the `backend` directory with the following variables:

```env
# MongoDB Configuration
MONGODB_URI=mongodb://localhost:27017/ibanking_payment

# JWT Secret Key
JWT_SECRET=your_secret_key_here

# Email Configuration (for OTP sending)
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password

# Server Port
PORT=3000
```

**Note**: For Gmail, you need to use an [App Password](https://support.google.com/accounts/answer/185833) instead of your regular password.

### 4. Initialize Database

Run the database initialization script to populate sample data:

```bash
node backend/scripts/initMongoDB.js
```

This will create:
- Sample customer accounts
- Sample tuition fee records

## 🏃 Running the Application

### Development Mode (with auto-reload)

```bash
npm run dev
```

### Production Mode

```bash
npm start
```

The server will start on `http://localhost:3000`

## 👤 Sample Accounts

The initialization script creates several test accounts:

| Username | Password  | Student ID | Email                    | Balance      |
|----------|-----------|------------|--------------------------|--------------|
| admin    | admin123  | -          | admin@example.com        | 50,000,000 ₫ |
| user1    | user123   | -          | user1@example.com        | 25,000,000 ₫ |
| khang    | khang123  | 522H0003   | 522H0003@student.edu.vn  | 20,000,000 ₫ |
| minh     | 123123    | 522H0028   | vamila2710@gmail.com     | 18,000,000 ₫ |

## 📖 How to Use

### 1. Login

1. Navigate to `http://localhost:3000`
2. Click on the **Login** button in the header
3. Enter your username and password
4. Click **Login**

### 2. Search for Tuition Fees

1. After logging in, you'll be redirected to the home page
2. Enter your **Student ID** in the search box
3. Click **Search**
4. Your tuition fee information will be displayed

### 3. Make a Payment

1. After searching for tuition fees, click the **Pay** button
2. Review the payment details
3. Click **Create Payment**
4. An OTP code will be sent to your registered email
5. Enter the OTP code in the verification page
6. Click **Complete Payment**
7. You'll be redirected to the completion page upon successful payment

### 4. View Payment History

1. Click on **History** in the navigation menu
2. View all your past transactions
3. Filter by payment status if needed

### 5. View Account Information

1. Click on your username in the header
2. Select **Account** from the dropdown
3. View your account balance and profile information

## 🔑 API Endpoints

### Authentication
- `POST /api/login` - User login
- `GET /api/profile` - Get user profile (requires auth)

### Tuition Management
- `GET /api/tuition/student/:studentId` - Search tuition by student ID
- `GET /api/tuition/:tuitionFeeId` - Get tuition details by ID
- `POST /api/tuition/create-payment` - Create a new payment
- `POST /api/tuition/complete-payment` - Complete payment with OTP
- `POST /api/tuition/resend-otp` - Resend OTP code
- `POST /api/tuition/cancel-payment` - Cancel a pending payment

### Payment History
- `GET /api/history` - Get payment history for logged-in user

## 🛠️ Technologies Used

- **Backend**: Node.js, Express.js
- **Database**: MongoDB, Mongoose
- **Authentication**: JWT (JSON Web Tokens), bcrypt
- **Email Service**: Nodemailer
- **Frontend**: HTML, CSS, JavaScript (Vanilla)

## 🐛 Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running: `mongod` or check your MongoDB service
- Verify the `MONGODB_URI` in your `.env` file

### Email OTP Not Received
- Check your email configuration in `.env`
- Ensure you're using an App Password for Gmail
- Check spam/junk folder

### Port Already in Use
- Change the `PORT` in `.env` file
- Or stop the process using port 3000

