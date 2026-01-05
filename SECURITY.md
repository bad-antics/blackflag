# HIVE-MIND & SPAWN - SECURITY DOCUMENTATION

**Developed by: bad-antics Development Team & antX**  
**Copyright © 2026**

---

## 🔒 SECURITY HARDENING OVERVIEW

Both Hive-Mind (master) and Spawn (client) applications have been hardened with enterprise-grade security features to protect your home network.

---

## ✅ IMPLEMENTED SECURITY FEATURES

### 1. **AUTHENTICATION SYSTEM**
- **256-bit Shared Secret Key** - All Spawn clients must provide the correct authentication key
- **Automatic Key Generation** - Hive-Mind generates a cryptographically secure random key on first run
- **Secure Key Storage** - Keys stored in `%APPDATA%\HiveMind\security.key` with hidden/read-only attributes

### 2. **AES-256 ENCRYPTION**
- **Military-Grade Encryption** - All network communication encrypted with AES-256
- **Unique Keys Per Installation** - Each Hive-Mind installation has unique encryption keys
- **Encrypted Messages** - Commands and responses fully encrypted in transit

### 3. **RATE LIMITING**
- **Connection Throttling** - Maximum 1 connection every 2 seconds per IP address
- **Prevents Spam** - Blocks rapid-fire connection attempts
- **Automatic Cleanup** - Old connection records automatically purged

### 4. **BRUTE FORCE PROTECTION**
- **Failed Attempt Tracking** - Monitors authentication failures per IP
- **Automatic Lockout** - 5 failed attempts = 15 minute lockout
- **IP-Based Blocking** - Attackers automatically blocked

### 5. **INPUT SANITIZATION**
- **XSS Protection** - Dangerous characters escaped
- **Length Limits** - Input capped at 1000 characters
- **Injection Prevention** - SQL/Command injection attacks blocked

### 6. **CREDENTIAL PROTECTION**
- **Windows DPAPI** - Credentials encrypted at rest on Windows
- **File Permissions** - chmod 600 on Linux/macOS (owner read/write only)
- **Secure Delete** - Credentials can be safely removed

### 7. **NETWORK SECURITY**
- **Port 49152** - Dynamic/private port range (less targeted)
- **Local Network Only** - Not exposed to internet by default
- **Connection Validation** - Every message validated and authenticated

---

## 🚀 USAGE GUIDE

### **HIVE-MIND (Master Controller)**

1. **First Launch**
   - Run as Administrator: `Start-Process "dotnet" -ArgumentList "run" -Verb RunAs`
   - Watch the boot sequence - you'll see security initialization
   - Security keys automatically generated and saved

2. **Getting the Authentication Key**
   - Click `[SHOW AUTH KEY]` button
   - Key is displayed in terminal and copied to clipboard
   - **KEEP THIS KEY SECURE** - anyone with this key can connect

3. **Starting the Command Server**
   - Click `[START SERVER]` to listen on port 49152
   - DEFCON level changes to 3 (heightened readiness)
   - Server now accepts authenticated Spawn connections

4. **Security Best Practices**
   - Only give the auth key to trusted machines
   - Don't share the key publicly or over unsecured channels
   - Regenerate keys if compromised (manually delete `security.key`)

### **SPAWN (Client)**

1. **First Setup**
   - Run Spawn on remote machine
   - When prompted, enter the authentication key from Hive-Mind
   - Choose whether to save credentials (recommended)

2. **Saved Credentials**
   - Credentials encrypted and stored locally
   - Windows: Protected with DPAPI (user-level encryption)
   - Linux/macOS: File permissions 600 (owner only)

3. **Automatic Check-In**
   - Spawn checks in every 5 seconds
   - Each check-in is authenticated and encrypted
   - Failed authentication stops the client

4. **Security Indicators**
   - ✓ Green checkmark = Successful authentication
   - ✗ Red X = Authentication failed
   - Yellow warning = Connection issue

---

## 🔐 TECHNICAL DETAILS

### **Encryption Algorithm**
- **AES-256-CBC** - Industry standard symmetric encryption
- **256-bit Keys** - Maximum security strength
- **Unique IV** - Prevents pattern analysis

### **Authentication Flow**
1. Spawn creates message: `AUTH|<token>|<command>`
2. Spawn encrypts entire message with AES-256
3. Hive-Mind receives encrypted message
4. Hive-Mind decrypts and validates token
5. Hive-Mind checks rate limits and lockouts
6. If valid, Hive-Mind processes command and sends encrypted response

### **Rate Limiting Details**
- **Sliding Window**: 2-second minimum between connections from same IP
- **Lockout Duration**: 15 minutes after 5 failed authentication attempts
- **Automatic Cleanup**: Old records purged every connection check

### **Storage Locations**
- **Hive-Mind Keys**: `%APPDATA%\HiveMind\security.key`
- **Spawn Credentials (Windows)**: `%APPDATA%\Spawn\credentials.dat`
- **Spawn Credentials (Linux/macOS)**: `~/.config/Spawn/credentials.dat`

---

## ⚠️ SECURITY WARNINGS

### **NOT RECOMMENDED FOR INTERNET EXPOSURE**
- This system is designed for **local network use only**
- Do **NOT** port forward port 49152 on your router
- Do **NOT** expose Hive-Mind to the public internet

### **Additional Hardening for Production Use**
If you need internet exposure, add:
- **TLS/SSL** - Transport layer encryption (HTTPS equivalent)
- **Certificate Pinning** - Prevent man-in-the-middle attacks
- **IP Whitelisting** - Only allow specific IPs to connect
- **VPN** - Use VPN instead of direct internet exposure

### **Physical Security**
- Protect machines with Hive-Mind installed (they have the master keys)
- Use full-disk encryption on all machines
- Strong passwords on all accounts

---

## 🔄 KEY ROTATION

If you believe your keys have been compromised:

1. **Stop Hive-Mind**
2. **Delete** `%APPDATA%\HiveMind\security.key`
3. **Restart Hive-Mind** - New keys will be generated
4. **Get new auth key** and distribute to all Spawn clients
5. **Update all Spawn clients** with new credentials

---

## 📊 MONITORING

### **Watch for These in Hive-Mind Terminal:**
- `> AUTHENTICATION FAILED - ACCESS DENIED` - Someone tried wrong key
- Multiple rapid connection attempts - Possible attack
- Connections from unexpected IPs - Investigate

### **Watch for These in Spawn:**
- `✗ Authentication failed` - Check if auth key is correct
- Repeated connection failures - Hive-Mind may be down or keys changed

---

## 🆘 TROUBLESHOOTING

### **"Authentication Failed" on Spawn**
1. Verify you copied the correct auth key from Hive-Mind
2. Click `[SHOW AUTH KEY]` in Hive-Mind to see current key
3. Delete Spawn credentials and re-enter key

### **"Access Denied" from Hive-Mind**
1. Check if IP is locked out (wait 15 minutes)
2. Verify Spawn has correct authentication key
3. Check Hive-Mind terminal for specific error messages

### **Can't Connect to Hive-Mind**
1. Verify Hive-Mind server is running
2. Check firewall isn't blocking port 49152
3. Verify IP address and port number are correct

---

## 📝 CHANGELOG

**v1.0 HARDENED (2026-01-01)**
- Added AES-256 encryption for all network communication
- Implemented 256-bit authentication system
- Added rate limiting and brute force protection
- Input sanitization and validation
- Secure credential storage with DPAPI/file permissions
- Changed default port to 49152 (dynamic/private range)
- Security status displayed in boot sequence
- [SHOW AUTH KEY] button for easy key distribution

---

## 📄 LICENSE & CREDITS

**Developed by:** bad-antics Development Team & antX  
**Copyright:** © 2026 All Rights Reserved

This software is provided "as is" without warranty of any kind. Use at your own risk.

---

## 🔗 QUICK REFERENCE

| Feature | Details |
|---------|---------|
| **Encryption** | AES-256-CBC |
| **Authentication** | 256-bit shared secret |
| **Port** | 49152 (dynamic/private range) |
| **Rate Limit** | 1 connection per 2 seconds per IP |
| **Lockout** | 5 failed attempts = 15 min ban |
| **Storage** | DPAPI (Windows) / chmod 600 (Unix) |

**KEEP YOUR AUTHENTICATION KEY SECURE!**
