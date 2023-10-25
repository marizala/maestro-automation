# maestro-automation
This project demonstrates the use of Maestro to automate a mobile app.


## 🚀 Getting Started

### 🚧 Prerequisites

> Disclaimer: The content, code, and testing of this project have been developed and evaluated primarily using Windows and Android testing perspectives. For other configurations, please refer to [maestro.mobile.dev](https://maestro.mobile.dev/) website for guidelines.

Before you can run this project, you must have the following software installed on your computer:

- WSL2 (Window Subsystem for Linux)
- Java Development Kit (JDK) version 11 or later
- SDK and emulator setup _(on this case, I used Android Studio)_
- Mobile application under test

#### 🚨 Mobile application under test
* [Toyota Link](https://play.google.com/store/apps/details?id=au.com.toyota.EntuneToyota&hl=en) 
* [Lexus Enform](https://play.google.com/store/apps/details?id=au.com.intelematics.EntuneLexus&hl=en_AU) <br/>
  Note that the app files are not uploaded into this repository intentionally.

### 🛠️ Installation
1. Run the following command to install Maestro.
   ```sh
   curl -Ls "https://get.maestro.mobile.dev" | bash
   ```
   Or, you may follow the environment setup directly from the [maestro.mobile.dev](https://maestro.mobile.dev/) website depending on your system [here](https://maestro.mobile.dev/getting-started/installing-maestro). 
2. Clone this repository to your local machine. 
   ```sh
   https://github.com/marizala/maestro-automation.git
   ```

### 👨🏼‍🔬Tests
This project contains 2 sample test cases that demonstrate how to use Maestro to interact with mobile app in Android platform.


#### 🧪 Test Cases
* `get-started.yaml`: Application onboarding process (accept Terms and Conditions, allow permission requests) and basic map actions.
* `trip-CRUD.yaml`: Basic create, read, update and delete of a trip record.


### 🏃🏽 How to run the tests locally
1. Run your emulator. 
   ```
   emulator -avd <device_name>
   ```

2. In Powershell, start the adb server.
   ```
   adb -a -P 5037 nodaemon server
   ```

3. Open WSL2 terminal in the project root directory and run these commands.
   ```
   adb kill-server
   export ADB_SERVER_SOCKET=tcp:<WINDOWS_IPV4_ADDRESS>:5037
   adb devices
   ```
4. Run your flow (test case) with this command.
   ```
   maestro --host <WINDOWS_IPV4_ADDRESS> --device <device_name> test -e APP_ID=<APP_ID> toyota-link/tests/trip-CRUD.yaml
   ```


#### ⚙️ Useful commands (Android)

* To install the mobile application `adb -s <device_name> install <apk file>`
* To clear app data `adb shell pm clear <app_id>`
  
### 📹 Demo
`get-started.yaml`

https://github.com/marizala/maestro-automation/assets/37069334/58be529f-092b-4a01-8e06-67026c651207

`trip-CRUD.yaml`

https://github.com/marizala/maestro-automation/assets/37069334/497ac335-2c8c-407c-8e80-0fcf9da9fe00

### 🏃🏽 How to run the tests on Maestro Cloud
1. Open WSL2 terminal in the project root directory and login to the CLI by running this command.
   
   ```
   maestro login
   ```
   > Sign in using your email address then the login link will be sent over to complete the process. If this is your first time logging in, you'll be prompted to create an account. Follow the printed instructions to complete the login process.
2. Run your flow on Maestro Cloud with this command.
   ```
   maestro cloud --include-tags smoke -e APP_ID=<APP_ID> --app-file='<APP_FILE_PATH>' --flows='toyota-link/'

   ```
   ![maestro-cloud-terminal](https://github.com/marizala/maestro-automation/assets/37069334/5c862851-9cea-4c4a-ac5c-24e77c29bc70)

   ![maestro-cloud](https://github.com/marizala/maestro-automation/assets/37069334/2082d15d-294d-4c03-8e7b-9b1afbba6f3e)
