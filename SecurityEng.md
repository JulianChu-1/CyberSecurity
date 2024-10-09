## Security Engineering

### Week 1
#### Terminology
- Security engineering is about building systems to remain dependable in the face of malice, error, or mischance.
- Asset, something that has value to the organization (tangible or intangible)
- Threat, a potential cause of an incident that may **harm the assets** of an organization.
- Threat Agent, a party that is responsible for **posing a threat** to a system. An agent could be **human** or **natural**.
- Vulnerability, a **weakness** in a system that can be **exploited by a threat agent**.
- Risk, the **potential** that a threat agent would exploit a vulnerability and adversely impact the system.
- Attack, the action of exploiting a vulnerability to compromise a system.
- Security Policy, a set of rules that define the assets to protect, the security objectives to achieve, the standards to follow, and constraints of a security program.
- Security Controls, measures to protect a system according to a security policy.
- Non-Repudiation, committed actions cannot be denied by responsible actors.
- 

#### Other
1. Types of Security Activities
    - Source Code Auditing, manual and/or automated review of the source code to identify security flaws and sources of vulnerabilities.
    - SW(Software) Component Analysis, investigating third-party and open-source software components for potential security risks.
    - Vulnerability Scanning, using automated scanners to identify flaws.
    - Vulnerability Assessment, manual verification of vulnerabilities to confirm exposure, but without exploiting vulnerabilities to gain further access.
    - Penetration Testing, exploitation of identified vulnerabilities to gain further access, simulating an attack by a malicious actor.
    - Red teaming, a holistic offensive approach to simulate how real-world adversaries can attack a system/organization to achieve specific goals.
    - Security Audit, evaluation of the security controls of a system/organization in relation to their compliance with certain security objectives, policies, or standards.
    - Security Review, verifying that security policies and standards have been applied to a system. 
2. The "7 Pernicious Kingdoms" Taxonomy (7PK)
    - Input Validation and Representation, such as, buffer overflow, command injection, format string attack, integer overflow, path manipulation. SQL injection, cross-site scripting.
    - API Abuse, it can be caused by the caller failing to honor its end of contract, or by using components that are inherently unsafe.
    - Security Features, improper implementation of security mechanisms and controls.
    - Time and State, improper implementation of concurrency mechanisms that allow synchronized access to shared resources.
    - Errors, runtime errors are exceptional situations that arise due to unexpected behaviors during execution.
    - Code Quality, poor code quality could lead to unpredictable behavior.
    - Encapsulation, is used to control access to internal data and operations of a software component.
    - Deployment Environment.

### Week 2
#### Terminology
- Instruction Cycle: Fetch (from memory) $\rightarrow$ Decode (the instruction and fetch data) $\rightarrow$ Execute
- Arithmetic & Logic Unit (ALU): performs arithmetic and logical operations.
- Control Unit (CU): orchestrates the instruction execution cycle in the CPU.
- Clock: synchronizes the operations of the CPU by producing pulses at a constant rate (clock rate), which is an indicator or the CPU speed (measured in Hertz).
- Registers: internal storage locations built in the CPU to provide fast access to data.
- Cache: small but fast memory that is typically used to store a copy of frequently used data from the main memory in order to reduce average memory access time.

#### 32-bit x86 Assembly
- Each processor has an "instruction set", **assembly** is a low-level language that depends on the instruction set of a specific processor. Therefore, assembly is not portable. We will focus on the assembly for the 32-bit architecture of Intel's x86 family of processors. Such architecture is known as IA32, aka i386.
- IA32 CPU Registers
  - Eight 32-bit general-purpose registers: 
