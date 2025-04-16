# VM Group Project – Deploying a .NET 8 Web API to Azure Linux VM 🌐

This project demonstrates how to deploy a simple .NET 8 Web API to an Azure Virtual Machine (VM) running Ubuntu. It was created as part of our group assignment in the Cloud Development program at JENSEN Yrkeshögskola.

## 👥 Group Members
- Sanali Sewwandi  
- Patricio Martinez  
- Gurdip Bola  
- Sravani Obul Reddy Gari  
- Cesar Tuncay  

## 📌 Project Goals
- Create and configure a secure Azure VM
- Deploy a .NET 8 C# Web API to the VM
- Expose the API securely using a Network Security Group (NSG)
- Run the API as a background service using systemd
- Limit access to specific IPs for better security

---

## ✅ Steps We Followed

### 1. Infrastructure Setup
- Created a **Resource Group**, **Virtual Network**, and **Subnet** in Azure.
- Deployed an **Ubuntu Linux VM**.
- Created and applied **NSG rules**:
  - Opened **port 22** for SSH (restricted to home IP)
  - Opened **port 5062** for API access (restricted to school IP)

### 2. API Setup & Deployment
- Cloned the GitHub repo on the VM:
  ```
  git clone https://github.com/RMSSanali/vm-groupproject.git
  cd vm-groupproject/ApiForGroup
  ```
- Built and ran the API using .NET 8:
  ```
  dotnet build
  dotnet ApiForGroup.dll --urls "http://0.0.0.0:5062"
  ```
- Confirmed that the API is running and accessible from the browser or via curl.

### 3. Run as a Linux Systemd Service
Created a `groupapi.service` file to ensure the API starts automatically on reboot:
```bash
sudo systemctl enable groupapi.service
sudo systemctl start groupapi.service
```

### 4. Security Measures
- Used **Azure IAM** to assign roles:
  - Contributor: `azurejensen074`
  - Reader: `Fredrik.dahl`
- Limited API access (port 5062) to **school IP only**

---

## 🔗 API Access

Once deployed, the API can be accessed via:
```
http://<your-vm-public-ip>:5062
```

> Note: Access is restricted to school IP for security.

---

## 🧪 How to Test the API

Use your browser or a tool like curl/Postman to access:
```
GET http://<public-ip>:5062/status
```

Expected response:
```
"API is running"
```

---

## ⚙️ Tech Stack
- .NET 8
- C#
- Ubuntu Server 22.04 LTS
- Azure Virtual Machine
- Azure Network Security Groups (NSG)
- systemd (Linux service)

---

## 📅 Deadline
The project was completed before the final deadline: **25 April 2025, 15:00**.

---

## 📁 Repository Structure
```
vm-groupproject/
├── ApiForGroup/       # Main API code
├── .gitignore
└── README.md          # You're reading it! 😄
```

---

## 📜 Assignment Requirements (Summary)
✔ Create infrastructure in Azure  
✔ Deploy and expose a C# API on a secure port  
✔ Test API functionality from client  
✔ Apply security rules (NSG, IAM)

---

## 🏁 Status
✅ Project Completed  
📢 Ready for demonstration!

---

## 🔐 Note
SSH and API access are IP-restricted for security purposes.

---

## 📧 Contact
For questions, contact any team member or open an issue on this repo.
