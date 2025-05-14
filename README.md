# WormHole
WormHole C2C Remote CMD Silent Server, Client
C2C Remote CMD WORMHOLEV1
Overview
The C2C Remote CMD is a sophisticated command and control (C2) application that enables secure remote command execution between a server and client(s) over an encrypted TCP connection. This project features robust security measures, self-preservation mechanisms, and metamorphic capabilities to evade detection.
Key Features
Security Features
AES-256 Encryption - All communications are encrypted using AES-256 with static IV
HMAC Verification - Message integrity verification using SHA-256 HMAC
Client Authentication - Strict client ID verification ("emp_pc_1" and etc(you can choose))
Connection Timeouts - Configurable timeouts for operations and heartbeats
Static Key Protection - Hardcoded encryption keys 
Client Capabilities
Metamorphic Engine - Self-modifying executables to evade signature detection
Persistence Mechanisms - Automatic startup registration via Registry Run keys
Anti-Duplication - Mutex-based single instance enforcement
Stealth Mode - Hidden console window operation
Self-Replication - Generates mutated copies with embedded IP addresses
Auto-reconnect - Exponential backoff reconnection logic
Heartbeat System - Regular keep-alive messages to maintain connection
Working Directory Tracking - Maintains current directory across commands
Server Capabilities
Multi-client Management - Concurrent client handling with thread pool
Client Monitoring - Tracks active clients with last-seen timestamps
Command Interface - Interactive shell for managing connected clients
Inactive Client Cleanup - Automatic removal of unresponsive clients
Secure Communication - End-to-end encrypted command channel
Technical Implementation
Core Components
Encryption Engine
Uses Windows CNG (BCrypt) for AES-256-CBC encryption
Implements HMAC-SHA256 for message authentication
Handles padding and data sanitization
Network Layer
Winsock2-based TCP communication
Configurable buffer sizes (64KB default)
Timeout-protected operations
Command Execution
Full command shell emulation
Working directory persistence
Output capture and sanitization
Hidden process creation
Persistence System
Automatic startup registration
Multiple instance prevention
Self-copying to alternate locations
Cleanup of old versions
Security Mechanisms
Static Analysis Evasion
Code morphing through junk instruction insertion/removal
Variable executable names (client1.exe, client2.exe, etc.)
IP address embedding in binary
Runtime Protection
Single instance enforcement via mutex
Hidden operation mode
Encrypted configuration
Usage Examples
Server Commands
list - Show connected clients
clean - Remove inactive clients
exit - Shutdown server
<client_id> <command> - Send command to client
Client Operation
Automatically connects to configured IP
Supports all standard cmd.exe commands
Maintains session state including working directory
Self-updates and maintains persistence


Advanced C2C Remote CMD WORMHOLEV2
Overview
This second-generation C2 (Command and Control) framework represents a significant evolution from the initial version, incorporating enterprise-grade security features, advanced anti-analysis techniques, and a modular architecture designed for operational security and reliability.
Key Enhancements Over Version 1
Security Architecture
Asymmetric Cryptography: RSA-2048/OAEP for secure key exchange
Perfect Forward Secrecy: Unique AES-256 session keys per client
HMAC-SHA256 Authentication: All messages integrity-protected
Key Fingerprint Verification: Trust-on-first-use key validation
Windows CryptoAPI Integration: For secure random number generation
Anti-Analysis Capabilities
Debugger Detection: Multiple detection methods including IsDebuggerPresent and CPUID checks
VM Detection: Hypervisor bit examination
Tool Blacklisting: Scans for analysis tools like OllyDbg, Wireshark and etc.
Anti-Dumping: Metamorphic code techniques to prevent static analysis
Crash Protection: Anti-debug traps when analysis detected
Operational Improvements
Multiple Persistence Mechanisms:
Registry Run keys
Scheduled Tasks (SYSTEM context)
Windows Service installation
Client Rotation: Automatic generation of new mutated binaries
Session Resilience: Heartbeat monitoring with automatic reconnection
Thread-Safe Design: Proper mutex protection for all shared resources
Technical Specifications
Cryptographic Implementation
Key Exchange: RSA-2048 with OAEP padding for AES key transmission
Session Encryption: AES-256-CBC with unique per-session keys
Message Authentication: HMAC-SHA256 with separate key material
Random Number Generation: Windows CryptGenRandom for key material
Network Protocol
Packet Structure:
4-byte length header (network byte order)
Encrypted payload
32-byte HMAC tag
Heartbeat System: 10-second keepalive messages(You can choose)
Timeout Handling: Configurable 30-second operation timeout
Client Features
Metamorphic Engine: On-the-fly binary modification
Polymorphic Engine – a technique that ensures the program's code changes every time, creating different versions that remain functional while evading detection by antivirus software.
Multiple Installation Methods:
bool InstallAutoStartFor() // Registry persistencebool InstallViaTaskScheduler() // Scheduled taskbool InstallAsService() // Windows service
Command Execution:
Full shell command support
Working directory tracking
Output capture and sanitization
Stealth Operations:
Hidden window mode
Mutex-based single instance
Automatic cleanup of old versions
Server Features
Client Management:
Concurrent client handling
Activity tracking
Graceful disconnection
Interactive Shell:
Tab-completion ready
Client targeting syntax
Built-in help system
Administration Commands:
list - Show connected client
clean - Remove inactive session
<id> <command> - Targeted execution
Security Analysis
Strengths
End-to-End Encryption: No plaintext communication
Authentication: Both client and server verify each other
Anti-Tampering: HMAC-protected messages
Operational Security: Regular binary rotation
Defense Evasion: Multiple anti-analysis techniques
Usage Examples
Server Interface
[server]> list
Connected clients (2):
- emp_pc_1 (YOUR:IP) - last active 5s (active)
- emp_pc_2 (YOUR:IP) - last active 2s (active)

[server]> emp_pc_1 sysinfo
Computer Name: WORKSTATION-01
OS: Microsoft Windows 10 Enterprise
CPU: Intel(R) Core(TM) i7-8650U CPU @ 1.90GHz
Memory: 8589934592

[server]> emp_pc_2 dir C:\\Reports
[...directory listing...]


If you want screenshots or videos showing how everything works, text me here @BlackVVSL
Both V1 and V2 are undetectable by Microsoft Defender Antivirus.
more info in telegram!
