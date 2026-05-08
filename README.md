Queue-Based Transaction Automation using UiPath REFramework

🚀 A scalable Dispatcher–Performer automation solution built using UiPath REFramework and UiPath Orchestrator for transaction-based financial process automation.

This project demonstrates enterprise-level RPA architecture using queue-based processing, robust exception handling, secure credential management, and modular workflow design. The solution automates transaction handling in the UiDemo application by separating the process into Dispatcher and Performer workflows.  

Video Reference: https://github.com/user-attachments/assets/44ef8fa6-2b66-4e1c-aeff-d12ad04b397f

🔷 Project Architecture
```
Excel Input Data  
       ↓  
Dispatcher Workflow  
       ↓   
UiPath Orchestrator Queue  
       ↓   
Performer Workflow  
       ↓  
UiDemo Application  
       ↓  
Transaction Status Update
```

🔷 Dispatcher Workflow

The Dispatcher bot is responsible for preparing and pushing transaction data into Orchestrator queues.

Key Functionalities

• Reads Excel transaction data during the Initialization state
• Converts data into a linear transaction structure
• Pushes each row into Orchestrator Queue Items
• Dynamically retrieves Queue Name & Folder from Config
• Uses queue-based architecture for scalability

Dispatcher States

•Initialization State

  Load Config.xlsx
  Read Excel data
  Initialize DataTable

•Get Transaction Data

  Fetch next DataRow transaction

•Process State

  Add Queue Item into Orchestrator Queue

🔷 Performer Workflow

The Performer bot processes each Queue Item individually.

Key Functionalities

• Loads transaction items from Orchestrator Queue
• Initializes environment and kills unwanted applications
• Opens UiDemo application
• Processes:

  Cash In
  On-Us Check
  Non-On-Us Check
• Updates transaction status in Orchestrator

Performer States

•Initialization State

  kill existing applications
  Load Config values
  Load Queue Name & Folder dynamically
  Retrieve credentials securely from Assets

• Get Transaction Data

   Fetch Queue Item

• Process Transaction

  Open UiDemo application
  Enter transaction details
  Click Accept
  Update Queue status

🔷 Exception Handling

This project uses the standard REFramework exception handling model.

**Business Rule Exception**

Transactions with amount ≥ 10000 are marked as Business Exceptions.

Example:

    Throw New BusinessRuleException("The total deposit amount is greater than 10000, so handle manually")

• System Exception

Application failures, selector issues, or unexpected runtime failures are retried automatically through the Orchestrator Queue retry mechanism.

🔷 Secure Credential Management

🔐 Username and Password are securely stored in Orchestrator Assets using Credential type assets.

Benefits

• No hardcoded credentials  
• Improved security  
• Easy credential management  
• Enterprise-level best practice  

Credentials are retrieved during runtime using:

• Get Credential activity  
• Config-driven asset references  

🔷 Technologies Used

• UiPath Studio  
• UiPath Orchestrator  
• REFramework  
• Excel Automation  
• Queue Automation  
• Exception Handling  
• Config-driven architecture  

🔷 Features

• Dispatcher–Performer architecture  
• Queue-based transaction processing  
• Dynamic Config management  
• Secure Credential Assets  
• Business & System Exception handling  
• Retry mechanism support  
• Scalable enterprise design  
• Modular workflow structure  

🔷 How to Run

Step 1: Create Queue in Orchestrator

Step 2: Create Credential Assets in Orchestrator

Step 3: Publish Dispatcher & Performer separately

Step 4: Run Dispatcher process

Step 5: Run Performer process

🔷 Business Scenario

This automation simulates a banking transaction processing system where multiple transaction types are validated and processed using queue-based orchestration.

🔷 Best Practices Followed

• REFramework architecture  
• Config-driven workflows  
• Queue-based scalability  
• Separation of Dispatcher & Performer  
• Secure Asset management  
• Structured logging  
• Retry handling using Orchestrator Queues  

🔷 Learning Outcomes

Through this project, I gained hands-on experience in:

• Enterprise RPA architecture  
• Queue processing  
• Transaction automation  
• Exception handling strategies  
• Orchestrator integration  
• Credential asset management  
