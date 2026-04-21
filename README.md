# AWS Cloud DevOps Journey 🚀

## Day 1: AWS IAM Fundamentals & Best Practices

Today, I explored **AWS IAM (Identity and Access Management)** and learned how to secure an AWS account using industry-standard best practices.

### 🔐 IAM Best Practices I Learned:
1. **Root Account Safety:** Avoid using the root account for daily tasks. Use it only for initial setup.
2. **Group-Based Permissions:** Instead of assigning permissions to individual users, add users to a **Group** and assign permissions to the group.
3. **Strong Authentication:** Always implement a strong **Password Policy** and enable **MFA (Multi-Factor Authentication)** for an extra layer of security.
4. **Programmatic Access:** Use **Access Keys** for CLI (Command Line Interface) and SDK access instead of passwords.
5. **Zero Sharing Policy:** Never share Access Keys or Passwords. Use IAM Roles for cross-service communication.
6. **Auditing:** Regularly check permissions using the **IAM Credential Report**.

### 🛠️ Hands-on Progress:
- [x] Created an IAM User and added to an 'Admin' Group.
- [x] Enabled MFA for the Root Account.
- [x] Installed and configured **AWS CLI** on WSL (Ubuntu).
- [x] Verified connection using `aws iam get-user`.

---
*Follow my journey as I build my cloud skills!* ☁️
