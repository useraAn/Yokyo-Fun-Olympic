# **Funolympics**

## **TableofContents**

- [**FunOlympics**](#fun-olympics)
  - [**Table of Contents**](#table-of-contents)
  - [**Scenario**](#scenario)
  - [**Setup**](#setup)
  - [**Running Project**](#running-project)
  - [**Role, Privileges and Access**](#role-privileges-and-access)
    - [**Role**](#role)
      - [**Guest**](#guest)
      - [**User**](#user)
      - [**Admin**](#admin)
      - [**Developer**](#developer)
    - [**Privilege**](#privilege)
      - [**Minor**](#minor)
      - [**Basic**](#basic)
      - [**Moderate**](#moderate)
      - [**Advanced**](#advanced)
    - [**Access**](#access)

## **Scenario**

The City of Yokyo had won the bid to host the next FunOlympic Games in 2019/20 but this had to be postponed due to a worldwide pandemic. During the build-up to the planned games in 2019/20 the city had already invested hugely in IT infrastructure and systems to make sure that the games would have been well organized, staffed, attended, and accessible to everyone.

Due to the pandemic restrictions, the FunOlympic committee have decided to run the 2020/21 games without the public attending the site. So now they have a number of additional projects which need to be completed before the delayed games start to ensure athletes remain healthy while attending the games and also that worldwide audiences can enjoy the games online.

The city have appointed a team of IT systems and infrastructure professionals – you are one of them. It is your job to interact with the client to clarify exact system requirements.

You will gain more information needed to complete the design and development task via client meetings and these meetings will reflect the knowledge and skill set appropriate to your programme of study. You will not be required to provide the entire solution – see details below:

The committee require you to build an online registration system for audiences to gain access to the proposed broadcast platform. The system must allow users to register, login and logout when using it, and make selections of broadcasts they wish to watch. There should also be an admin side to the system to allow an admin user to view user interactions, reset passwords etc. The prototype solution must deliver the key functionality described (you will need to interview the client to derive a full requirements list), although at this prototypical stage the inclusion of mechanisms for securing payments is not required.

## **Setup**

- You will need to copy the `.env.example` and rename to `.env` on same directory.
  
- Copy the API KEY to [`firebase-configuration.js`](./Config/app/firebase-configuration.js) file. Which can be retrieved from
  ![FirebaseConfig](./docs/FirebaseConfig.png)
 and should be replaced by your api key on `firebase-configuration.js` file

  ```js
    export const firebaseConfig = {
        apiKey:"AIzaSyD5woMGNN_P074SIskKa4j6Q2pjkY-mbFE"
    }
  ```

- You also need to get firebase Server access as by generating it from firebase as shown below
![FirebaseServiceAccount](./docs/ServiceAccount.png)

and Paste it on [`service-accountKey.js`](./Config/app/service-accountKey.js) file

```js
export const service_account = {
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
 // For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyD5woMGNN_P074SIskKa4j6Q2pjkY-mbFE",
  authDomain: "yokyo-fun-olympic.firebaseapp.com",
  databaseURL: "https://yokyo-fun-olympic-default-rtdb.firebaseio.com",
  projectId: "yokyo-fun-olympic",
  storageBucket: "yokyo-fun-olympic.appspot.com",
  messagingSenderId: "375296020267",
  appId: "1:375296020267:web:883cfc4795f138eba83f6e",
  measurementId: "G-HRRFS9BFW0"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
}

```

## **Running Project**

You can run the project on development mode using `npm run dev` and on production mode using `npm run serve`.

## **Role, Privileges and Access**

The heart of this application is maintained by the[**Role**](#role), [**Privileges**](#privilege) and [**Access**](#access). These three elements are the chain of authority that determines the access to the system.

### **Role**

Talking about role feature of application it's significance is to provide the privilege and access to different pages according to categories of role. The core categories of role are:

1. [**Guest**](#guest)
2. [**User**](#user)
3. [**Admin**](#admin)
4. [**Developer**](#developer)

#### **Guest**

Guest role is created to allow users to navigate through **_normal pages_** of the application. This role has less privilege than other roles and can only access page like `login`, `register`, `home`, `faq` and `forget-password`.

#### **User**

User role is created to allow user with more privilege and access than guest users of the application. This role has a bit more control than guest role and can access pages like `stream`, `settings`, `verify-email`, `reset-password`, `logout` and `notice` including all the feature of guest.

#### **Admin**

Admin role is created to control overall flow of application and can access almost allow of the pages. This role has most privilege and can access pages like `dashboard`, `users` and `profanity` including all the access of users.

#### **Developer**

Developer role is created to allow developers to access and manage other pages. All the beta testing pages and navigation's will be assigned to developer and after it's complete it will be assigned to admin and other roles as per requirement. Currently all the all the access of application is assigned to developer role.

### **Privilege**

There are different privilege levels for all the roles. The privilege levels define the necessity and access of page and feature of application for each role. The privilege levels of application are:

1. [**Minor**](#minor)
2. [**Basic**](#basic)
3. [**Moderate**](#moderate)
4. [**Advanced**](#advanced)

#### **Minor**

This privilege level is the lowest privilege level and it is assigned to guest role. It is used to access pages like `login`, `register`, `home`, `faq` and `forget-password`.

#### **Basic**

This privilege level is assigned to user role. It is used to access pages like `stream`, `settings`, `verify-email`, `reset-password`, `logout` and `notice` including all the feature of guest.

#### **Moderate**

This privilege level is assigned to admin role. It is used to access pages like `dashboard`, `users` and `profanity` including all the access of users.

#### **Advanced**

This privilege level is assigned to developer role. It is used to access all the pages of application.

### **Access**

Access of application is defined by the endpoint and its methods. For example `/login` is an endpoint which is required to display login page and submit login form as well. This endpoint has two methods, **`GET`** and **`POST`** and is assigned to [**Basic**](#basic) privilege. The basic privilege is then assigned [**`Guest`**](#guest) role.
