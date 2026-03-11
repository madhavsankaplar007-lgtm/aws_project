# Security Groups

## What is a Security Group?
A Security Group acts like a **virtual firewall or security guard** for your EC2 instances. It controls the **Inbound and Outbound traffic** rules — deciding what traffic is allowed to come in and go out of your EC2 server.

---

## Inbound Rules
Inbound rules control the **incoming traffic** — meaning any data or requests coming from the internet or outside network into the EC2 machine.

**Common Inbound Rule examples:**
| Port | Protocol | Purpose |
|------|----------|---------|
| 22 | SSH | Secure remote login to EC2 |
| 80 | HTTP | Allow web traffic |
| 443 | HTTPS | Allow secure web traffic |
| 3306 | MySQL | Allow database connections |

---

## Outbound Rules
Outbound rules control the **outgoing traffic** — meaning any data or responses going from the EC2 machine back to the internet or outside network.

**Default Outbound Rule:**
- By default, all outbound traffic is **allowed** from EC2 to the internet.

---

## Key Points

- 🔒 **Firewall** — Security Groups act as a virtual firewall protecting your EC2 instances
- 📥 **Inbound Rule** — Controls incoming traffic into the EC2 machine
- 📤 **Outbound Rule** — Controls outgoing traffic from the EC2 machine
- 🔑 **SSH (Port 22)** — Used to securely connect and manage your EC2 remotely
- 🌐 **HTTP (Port 80)** — Allows normal web traffic to reach your server
- 🔐 **HTTPS (Port 443)** — Allows secure/encrypted web traffic to reach your server
- ✅ **Stateful** — If you allow inbound traffic, the response is automatically allowed outbound
- ❌ **Deny by default** — All traffic is blocked unless you specifically create an allow rule

---

## Security Group vs NACL

| Feature | Security Group | NACL |
|---------|---------------|------|
| Level | Instance level | Subnet level |
| Type | Stateful | Stateless |
| Default | Deny all inbound | Allow all |
| Rules | Allow only | Allow and Deny |

---

## Architecture

```
Internet
    |
    ▼
Security Group (Firewall)
    |-- Inbound Rules  → Controls incoming traffic
    |-- Outbound Rules → Controls outgoing traffic
    |
    ▼
EC2 Instance
```

---

## Key Takeaways
- Security Groups are **attached to EC2 instances** not subnets
- They are **stateful** — response traffic is automatically allowed
- You can attach **multiple security groups** to one EC2 instance
- Always follow the **least privilege rule** — only open ports that are needed

---
*Documented by Madhav S R | AWS Cloud Learner*
