Here’s a comprehensive **README.md** file for your **Genesis 360 Superapp** repository. This file will serve as a guide for developers, outlining project goals, structure, and steps to set up the development environment.

---

# **Genesis 360 Superapp**

### **Introduction**
**Genesis 360** is a comprehensive, interconnected platform that addresses critical global challenges such as climate change, renewable energy, socioeconomic inequality, personalized healthcare, and medical research. It combines biblical principles with cutting-edge technology, scientific advancements, and philosophical insights to create sustainable and ethical solutions for individuals and societies.

This repository contains the source code for **Genesis 360**, built with **Flutter** for mobile applications and **Firebase Data Connect** for scalable and secure database management.

---

## **Table of Contents**
1. [Project Overview](#project-overview)
2. [Technologies Used](#technologies-used)
3. [Project Structure](#project-structure)
4. [Getting Started](#getting-started)
5. [Firebase Data Connect Setup](#firebase-data-connect-setup)
6. [Running the App](#running-the-app)
7. [Schema Migrations](#schema-migrations)
8. [Testing](#testing)
9. [Deployment](#deployment)
10. [License](#license)

---

## **Project Overview**
Genesis 360 focuses on the following pillars:
- **Discernment Engine**: AI-powered decision-making for personalized healthcare, sustainable practices, and socioeconomic empowerment.
- **Love and Compassion Network**: Community-building, volunteer opportunities, and behavioral tracking for social impact.
- **Stewardship and Climate Action Platform**: Real-time data on climate change and renewable energy with blockchain integration for transparency.
- **Medical Research Crowdsourcing**: Anonymized health data for global medical research and crowdsourced clinical trials.
- **Impact Advocacy Hub**: Policy advocacy, civic engagement, and ethical leadership with biblical guidance.
- **Impact Investment Marketplace**: Connecting investors with social enterprises through ethical investing platforms.

---

## **Technologies Used**
- **Flutter**: Cross-platform mobile framework used for building the app (iOS and Android).
- **Firebase Data Connect**: A scalable, serverless service for managing relational data using **Cloud SQL**.
- **GraphQL**: For querying and mutating data in the backend.
- **Firebase Authentication**: For secure user authentication.
- **Firebase Cloud Messaging (FCM)**: For real-time notifications.
- **Blockchain**: Used for ensuring transparency in energy trading and carbon offset records.
- **Google Cloud Functions**: For serverless backend processes, including calculating carbon offsets and handling user actions.

---

## **Project Structure**
```plaintext
genesis360-dataconnect/
├── dataconnect/                    # Firebase Data Connect and database files
│   ├── schema/                     # SQL schema definitions
│   ├── connectors/                 # GraphQL connectors and resolvers
│   ├── services/                   # Service layer for business logic
│   ├── schema_migrations/          # Database migrations
│   └── logs/                       # Log files for debugging
├── app/                            # Main Flutter app code
│   ├── modules/                    # Modular architecture by feature
│   └── shared/                     # Shared UI components and utilities
├── test/                           # Unit and integration tests
├── assets/                         # Static assets (images, fonts)
├── pubspec.yaml                    # Flutter project configuration
├── README.md                       # Project documentation
└── .gitignore                      # Git ignore file
```

- **dataconnect/schema/**: Contains SQL schema definitions for each module (e.g., healthcare, sustainability, advocacy).
- **dataconnect/connectors/**: GraphQL queries and resolvers for interacting with Firebase Data Connect.
- **dataconnect/services/**: Business logic for handling API interactions and module-specific functionality.
- **app/modules/**: Contains Flutter code for each module, separated by feature (e.g., healthcare, sustainability).
- **test/**: Unit and integration tests for the various modules and services.

---

## **Getting Started**

### **Prerequisites**
- **Node.js** and **npm**: Install the latest version from [nodejs.org](https://nodejs.org/).
- **Flutter**: Follow the official installation guide at [flutter.dev](https://flutter.dev/docs/get-started/install).
- **Firebase CLI**: Install via npm:
  ```bash
  npm install -g firebase-tools
  ```
- **VS Code**: Install [VS Code](https://code.visualstudio.com/) with the **Firebase Data Connect** extension.

### **Installation**
1. **Clone the repository**:
   ```bash
   git clone https://github.com/paycoo-droid/genesis360-dataconnect.git
   cd genesis360-dataconnect
   ```

2. **Install dependencies** for the Flutter app:
   ```bash
   cd ./app
   flutter pub get
   ```

3. **Initialize Firebase** in the `dataconnect/` directory:
   ```bash
   cd ./dataconnect
   firebase init
   ```
   - Select **Data Connect** and any other Firebase services you want to use (e.g., Authentication, Hosting).

---

## **Firebase Data Connect Setup**

### **1. Create Firebase Data Connect Service and Cloud SQL Instance**
- Open **Firebase Data Connect** in the Firebase Console and set up a **Cloud SQL instance**.
- Choose the appropriate **server region** and ensure you are on the **Blaze plan**.

### **2. Configure Firebase Data Connect**
- In `dataconnect/dataconnect.yaml`, ensure your **serviceId**, **instanceId**, and **database** match your Firebase project:
   ```yaml
   specVersion: "v1alpha"
   serviceId: "genesis360-service"
   location: "us-central1"
   schema:
     datasource:
       postgresql:
         database: "genesis360-db"
         cloudSql:
           instanceId: "your-instance-id"
   ```

---

## **Running the App**

### **1. Running the Firebase Emulators**
Start Firebase Data Connect emulators to test locally:
```bash
cd ./dataconnect
firebase emulators:start
```

### **2. Running the Flutter App**
In the **app/** folder, run the Flutter app on a simulator or device:
```bash
cd ./app
flutter run
```

---

## **Schema Migrations**
Use the Firebase CLI to compare and apply database schema changes.

1. **Check for schema differences**:
   ```bash
   firebase dataconnect:sql:diff
   ```

2. **Apply schema migrations**:
   ```bash
   firebase dataconnect:sql:migrate
   ```

---

## **Testing**
Run unit and integration tests to ensure the functionality of each module.

1. **Run tests** for each module:
   ```bash
   flutter test test/<module_name>_tests.dart
   ```

2. **Continuous Integration**: Integrate testing with your CI pipeline (e.g., GitHub Actions).

---

## **Deployment**

### **1. Deploy Firebase Data Connect**
Deploy the Firebase Data Connect services and any schema migrations:
```bash
firebase deploy --only dataconnect
```

### **2. Deploy Hosting and Cloud Functions**
Deploy the web app and serverless functions for notifications and background tasks:
```bash
firebase deploy --only hosting,functions
```

---

## **License**
This project is licensed under the **Apache 2.0 License**. You may freely use and modify this project as long as proper attribution is provided. See the `LICENSE` file for more details.

---

## **Contributing**
We welcome contributions! Please create a pull request or submit an issue for any feature suggestions, bug reports, or improvements. Follow our **contributing guidelines** in the `CONTRIBUTING.md` file.

---

This README provides the basic overview and setup instructions necessary to start developing on the **Genesis 360** Superapp. Ensure that you update this file as the project evolves, particularly when new features are added or significant changes are made to the workflow.



# Firebase Data Connect Quickstart

## Introduction

This is a sample app for the preview version of Firebase DataConnect. This service is currently in Private Preview at no cost for a limited time. Sign up for the program at [Firebase Data Connect](https://firebase.google.com/products/data-connect). This quickstart will not work if you don't have access to the preview.

## Getting Started with Firebase DataConnect

Follow these steps to get up and running with Firebase DataConnect. For more detailed instructions, check out the [official documentation](https://firebase.google.com/docs/data-connect/quickstart).

### 1. Create a New Data Connect Service and Cloud SQL Instance

1. Open [Firebase Data Connect](https://console.firebase.google.com/u/0/project/_/dataconnect) in your Firebase Console project and select **Get Started**.
2. Create a new Data Connect service and a Cloud SQL instance. Ensure the Blaze plan is active. Find pricing details at [Firebase Pricing](https://firebase.google.com/pricing).
3. Choose your server region. If you plan to use vector search, select `us-central1`.
4. Wait for the Cloud SQL instance to be provisioned. Once it's ready, you can manage it in the [Cloud Console](https://console.cloud.google.com/sql).

### 2. Set Up Firebase CLI

Ensure the Firebase CLI is installed and up to date:

```bash
npm install -g firebase-tools
```

### 3. Cloning the Repository

This repository contains the quickstart to help you explore the functionalities of DataConnect.

1. Clone this repository to your local machine.
2. Navigate to the `dataconnect` folder and initialize your Firebase project:

    ```bash
    cd ./dataconnect
    ```

   *(Optional)*: If you plan to use other Firebase features, run `firebase init` instead, and select both DataConnect options as well as any additional feature you want to use.

### 4. Installing VS Code Extension

1. Install [VS Code](https://code.visualstudio.com/).
2. Download and install the [Firebase DataConnect extension](https://marketplace.visualstudio.com/items?itemName=GoogleCloudTools.firebase-dataconnect-vscode).
3. Open this quickstart in VS Code and log in to your Firebase account using the Firebase extension.
4. In the Firebase DataConnect VSCode extension, click **Start Emulators** and confirm that the emulators are running in the terminal.

### 5. Populating the Database

1. In VS Code, open `dataconnect/movie_insert.gql`. Ensure the emulators in the Firebase DataConnect extension are running.
2. You should see a **Run (local)** button at the top of the file. Click this to insert mock movie data into your database.
3. Check the DataConnect Execution terminal to confirm that the data was added successfully.

### 6. Running the App

1. Navigate to the `app` folder and install dependencies:

    ```bash
    cd ./app
    npm install
    ```

2. Start the app:

    ```bash
    npm run dev
    ```

### 7. Deployment

1. Create a Web App in the [Firebase Console](https://console.firebase.google.com) and take note of your App ID.
2. In the Firebase Console, click on **Add App**. You can ignore the SDK setup for now, but note the generated `firebaseConfig` object.
3. Replace the `firebaseConfig` in `app/src/lib/firebase.tsx`:

    ```javascript
    const firebaseConfig = {
      apiKey: "API_KEY",
      authDomain: "PROJECT_ID.firebaseapp.com",
      projectId: "PROJECT_ID",
      storageBucket: "PROJECT_ID.appspot.com",
      messagingSenderId: "SENDER_ID",
      appId: "APP_ID"
    };
    ```

4. Build the web app for hosting deployment:

    ```bash
    cd ./app
    npm run build
    ```

5. Set up Firebase Authentication with Google Sign-In. Optionally, allow domains for [Firebase Auth](https://firebase.google.com/docs/auth/web/hosting) in your project console (e.g., `http://127.0.0.1`).
6. Allow domains for Firebase Auth in your [project console](https://console.firebase.google.com/project/_/authentication/settings) (e.g., `http://127.0.0.1`).
7. In `dataconnect/dataconnect.yaml`, ensure that your `instanceId`, `database`, and `serviceId` match your project configuration:

    ```yaml
    specVersion: "v1alpha"
    serviceId: "your-service-id"
    location: "us-central1"
    schema:
      source: "./schema"
      datasource:
        postgresql:
          database: "your-database-id"
          cloudSql:
            instanceId: "your-instance-id"
    connectorDirs: ["./movie-connector"]
    ```

8. Deploy your project:

    ```bash
    npm install -g firebase-tools
    firebase login --reauth
    firebase use --add
    firebase deploy --only dataconnect,hosting
    ```

9. To compare schema changes, run:

    ```bash
    firebase dataconnect:sql:diff
    ```

10. If the changes are acceptable, apply them with:

    ```bash
    firebase dataconnect:sql:migrate
    ```

## License

© Google, 2024. Licensed under an [Apache-2](../../LICENSE) license.
