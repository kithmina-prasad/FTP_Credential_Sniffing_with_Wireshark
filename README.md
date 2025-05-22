# 🕵️‍♂️ FTP Credential Sniffing with Wireshark

This project is part of my Network Security studies. It demonstrates how FTP (File Transfer Protocol), a commonly used but outdated file transfer protocol, exposes sensitive information such as usernames and passwords in plain text. The analysis was performed using **Wireshark**, a powerful packet analysis tool.

## 📌 Objective

To analyze FTP traffic using Wireshark and identify its security vulnerabilities, specifically focusing on the exposure of login credentials.

## 📂 About FTP

FTP (File Transfer Protocol) is a standard network protocol used for transferring files between a client and server over a TCP/IP network. It operates on ports **21 (control)** and **20 (data)**. However, FTP does **not use encryption**, making it vulnerable to attacks.

## 🔬 Methodology

- A test environment was set up with an FTP server and client on a local network.
- Wireshark was used to capture and inspect packets during an FTP login session.
- Filters applied in Wireshark:
  - `ftp`
  - `tcp.port == 21`
  - `ftp.request.command == "USER"`
  - `ftp.request.command == "PASS"`

## 🔍 Key Findings

1. **Username Exposure**  
   The `USER` command reveals the FTP username in plaintext.

2. **Password Exposure**  
   The `PASS` command exposes the FTP password without encryption.

3. **Cleartext Communication**  
   All FTP traffic, including file transfers and login credentials, is unencrypted.

## ⚠️ Security Implications

- FTP is **vulnerable to man-in-the-middle (MITM) attacks**.
- Attackers on the same network can easily intercept and read credentials.
- Unauthorized access can lead to data theft, manipulation, or system compromise.

## ✅ Recommendations

- **Avoid using FTP** for transmitting sensitive data.
- Use **SFTP (SSH File Transfer Protocol)** or **FTPS (FTP Secure)**, which encrypt both commands and data.
- Implement **firewalls**, **IDS/IPS systems**, and **network segmentation**.
- Enforce **strong authentication** and **password policies**.

## 🧪 Sample Packet Analysis

Wireshark captured the following during an FTP login:

- **Packet 37:** `USER admin`  
- **Packet 38:** `PASS 123456`

These were clearly visible in the packet details, proving FTP's lack of encryption.

![04](https://github.com/user-attachments/assets/87003321-4a0a-4e41-a16a-39d640b07da4)

![03](https://github.com/user-attachments/assets/22d82ac8-a4d9-4f89-9dbd-86cd17a72956)

![05](https://github.com/user-attachments/assets/a0a5c70d-b4ef-46ba-b4f4-ca1b1cd8223f)

![01](https://github.com/user-attachments/assets/51d017db-92b7-4cb4-8460-7288c2024784)

![02](https://github.com/user-attachments/assets/3cef7a9d-aa82-42e4-a3e5-63676ee63163)


https://github.com/user-attachments/assets/179208b3-b153-44fc-9ba5-716a9719e165


## 🛠 Tools Used

- Wireshark
- Local FTP server (e.g., vsftpd / FileZilla)
- Test network environment (VirtualBox, GNS3, or Packet Tracer)

## 🔒 Ethical Disclaimer

> This analysis was conducted in a controlled lab environment for educational purposes only.  
> **Do not perform packet sniffing on networks without proper authorization.**

## 📚 References

- [Wireshark Official Documentation](https://www.wireshark.org/docs/)
- [RFC 959 - File Transfer Protocol](https://tools.ietf.org/html/rfc959)
- [SFTP vs FTP Comparison](https://www.hostinger.com/tutorials/sftp-vs-ftp)

## 📌 Takeaway

FTP serves as a great educational example of why encryption matters. This project highlights the need for secure protocols in modern networks and reinforces the importance of securing credential transmission.







