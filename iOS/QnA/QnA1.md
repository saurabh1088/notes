#  QnA

## Explain iOS Architecture.

iOS Architecture consists of four layers as shown in below diagram.

![iOS Architecture](resources/ios_architecture.png "iOS Architecture")

### Core OS

This layer is directly on top of device's underlying hardware. This layer is responsible
for basic operating system services like

- Memory management
- Handling file system
- Threading and concurrency
- Low level networking
- Access to external accessories
- Security & Encryption features like Secure Enclave
- Device drivers helping communicate with harware components like CPU, GPU, storage etc.
- Components for power management
- Inter Process Communication (IPC) 

Core OS includes below frameworks

- Core Bluetooth Framework
- External Accessories Framework
- Accelerate Framework
- Security Services Framework
- Local Authorization Framework

### Core Services

- GCD
- iCloud Storage
- In-app purchase


### Media Services


### Cocoa Touch
