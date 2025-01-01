## Cryptography, the science of secret writing

### Week 1
#### Terminology

- Cryptography is the study of mathematical techniques related to aspects of information security such as confidentiality, data integrity, entity authentication, and data origin authentication.
- Steganography, the science of hiding messages in other messages or images.
- CIA triad, that means confidentiality, integrity and availability
- Confidentiality, **no improper disclosure of information** (Information is not learned by unauthorized principals).
- Integrity, **no improper modification of information** (Information has not been modified by unauthorized principals).
- Availability, **no improper impairment of functionality / service** (Information can be accessed by authorized principals).
- Identification, associating an identity with a subject.
- Authentication, verifying the validity of something (usually the claimed identity of a system entity), **Principals or data origin can be identified accurately**.
- Authorization, granting or denying the permissions of a system entity to access a resource.
- Accountability, the requirement for actions of an entity to be traced uniquely to that entity.
- Physical access controls, controls access to physical resources, such as a PC or paper records.
- Logical access controls, controls access to electronic systems and resources, such as databases and electronic records.
- Discretionary access control (DAC), the owner of the object decides which subjects have which privileges.
- Mandatory access control (MAC), system-wide policies define subject access to objects, and owners cannot change this.
- Role based access control (RBAC), access is based on a common set of privileges that apply to all subjects in the same role.
- Rule-based access control (RAC), access to objects is based on a list of rules defined by the owners for each subject.
- A Reference Monitor is a mechanism used to enforce access control policies, Reference Monitor must be NEAT: Non-bypassable, Evaluable, Always Invoked, Tamper-proof.

#### Other
- Access Control Matrix Model, a protection state (relative to a set of privileges **P**) is a triple (**S**,**O**,**M**).
- Matrix ***need to write !!!!***

### Week 2
#### General cryptographic schema

- A message is to be transferred from one principal (Sender) to another (Recipient) across some sort of Internet service.
- Plaintext ***P***, Encryption ***E***, Ciphertext ***C***, Decryption ***D***
- **Symmetric** algorithms, ***Key1 = Key2***
- **Asymmetric** algorithms, different keys, public key can be published without compromising private key.
- A mathematical formalization of encryption/decryption
  ![](Asset/mathematical%20formalization.png)

#### Three characteristics of cryptographic systems
1. Type of operations used to transform plaintext into ciphertext
    - **Substitution**, each element in plaintext is mapped into another element.
    - **Transposition**, elements in plaintext are rearranged.
2. Number of key used
    - **Symmetric**, single-key, secret-key, or conventional encryption: both sender and receiver use "same" key.
    - **Asymmetric**, two-key, or public-key encryption: sender and receiver use different keys.
3. Way in which plaintext is processed
    - **Block cipher** processes input one block of elements at a time, producing an output block for each input block.
    - **Stream cipher** processes input elements continuously, producing in output one element at a time, as it goes along.

#### Cryptanalysis and brute-force attacks


### Week 3
#### Substitution
A substitution cipher is one in which the letters of plaintext are replaced by other letters or by numbers or symbols.
1. Caesar cipher
   - Replace each letter of the alphabet with the letter standing ***x*** places further down the alphabet.
   - $$ C = E(\mathbf{x}, P) = (P + \mathbf{x}) \mod 26 $$
   - Insecurity: There are only 25 keys to try. 
2. Mono-alphabetic substitution ciphers
   - Generalize Caesar cipher by allowing an arbitrary substitution.
   - Let **K** be the set of all permutations on the alphabet **A**. 26 letters $\rightarrow$ 26! possible keys.
   - Insecurity: Easy to crack using frequency analysis.
3. Homophonic substitution ciphers
   - Provide multiple substitutes for a single letter to make frequency analysis more difficult.
   - For example, A $\rightarrow$ {12, 34, 56}, we can randomly choose a string to replace it.

4. Playfair cipher
   - ![](Asset/Playfair.jpg)

5. Polyalphabetic substitution ciphers (Vigenère cipher)
   - A polyalphabetic substitution cipher based on a tableau where each row is a Caesar Cipher with incremental shift.
   ![](Asset/Vigenère.jpg)

6. Vernam cipher: XOR
   - It works on binary data (bits) rather than letters, using **XOR**, $A \oplus B$.
   - $P \oplus K = C$, $C \oplus K = P$

7. One-time pad
   - Improvement to Vernam, use a truly random key that is: as long as the message, so that the key need not be repeated, used to encrypt and decrypt a single message, and then discarded.

#### Transposition 
1. Rail fence cipher:
   - ![](Asset/Rail%20fence.jpg)

2. Rotating (turning) grilles
   - 

3. Multiple-stage columnar transposition cipher
- Write message in a rectangle, row by row, and read message off, column by column, but permute the order of the columns. Multiple stages of encryption can produce analgorithm that is significantly more difficult to cryptanalyze.

### Week 4
#### Steganography and Composite ciphers
   - Conceal the existence of the message. For example, Arrangement of words or letters, Invisible ink, Pin punctures.
   - General model of Steganography
   - ![](Asset/Steganography.jpg)
   - Watermarking and DRM (Digital Rights Management)
   - Product ciphers chain substitution-transposition combinations. One example is Rotor machines used in WW2. Used a series of cylinders, each giving one substitution, which rotated and changed after each letter was encrypted.

#### Feistel cipher
   - ![](Asset/Feistel.jpg)
   - Small block size (e.g., n = 4): equivalent to a classical cipher and thus easily attackable. However, large block size: not practical implementation and performance. So, Feistel's suggestion is **invertible product cipher**.
   - **Product cipher**: Execution of 2 or more simple ciphers in sequence so that the result is cryptographically stronger. Alternates substitutions and permutations.
   - **S-Boxes and P-Boxes**, a proposal by Shannon to develop a product cipher that alternates confuse and diffusion functions. S-Boxes "confuse" input bits; P-Boxes "diffuse" bits across S-box inpus.
   - ![](Asset/FeistelEncryption.jpg)
   - A substitution is performed on LE<sub>i</sub> by applying a **round function** F to RE<sub>i</sub> and then XORing output with LE<sub>i</sub>.F has same general structure for each round is parameterized by round subkey K<sub>i</sub>. Then a permutation is performed: interchange of two halves of data.
   - Intermediate value of decryption process equal to corresponding value of encryption process with two halves of value swapped. LD<sub>16 - i</sub> || RD<sub>16 - i</sub> = RE<sub>i</sub> || LE<sub>i</sub>
   - ![](Asset/FeistelDe.jpg)

### Week 5
#### DES, the Data Encryption Standard
   - ![](Asset/DESOverall.jpg)
   - If a 64-bit DES key is divided into 8 bytes, then the sum of the eight bit of each byte is odd. This means that 7 of the 8 bits determine the value of the 8th bit.
   - IP and IP<sup>-1</sup> has no real cryptographic significance.
   - Initially, key is passed through a **permutation** function(64 $\rightarrow$ 56), for each of 16 rounds, a subkey K<sub>i</sub> is produced by combination of a **left cicular shift** and a permutation.
   - ![](Asset/DESSingle.jpg)
   - Substitution consists of a set of 8 S-boxes, each of which accepts 6 bits as input and produces 4 bits as output. For each S<sub>i</sub>(4 * 16 matrix), first and last bits of the input to form a 2-bit number to select row, and middle 4 bits select column, then select a number to produce 4-bit output.
   - Security of DES: differential analysis, linear analysis and exhaustive search of the key space.
   - Triple DES, use 3 stages of encryption with 2 keys Key1, Key2, also can use three different keys.

#### AES, Advanced Encryption Standard

#### Linear Cryptography
- Linear Cryptanalysis refers to a category of attack launched against block ciphers.

### Week 6
#### Block cipher modes of operation
1. Electronic Codebook(ECB)
- Plaintext message broken into N independent blocks P<sub>i</sub>, each block encrypted individually with the same key, C<sub>i</sub> = E(K, P<sub>i</sub>). And each ciphertext block is decrypted also individually.
- ECB is not recommended for messages longer than a block, cuz same block of plaintext always produces the same ciphertext, and for example, the message is highly structured.
- Ideal for a short amount of data, such as an encryption key, e.g., to transmit a DES key.
2. Cipher-block Chaining (CBC)
- For C<sub>0</sub> = IV(initialization Vector) and 1 < i <= n:   
  $C_1 = E(K, IV \oplus P_1)$     
  $C_i = E(K, C_{i-1} \oplus P_i)$    
  $P_i = D(K, C_i) \oplus C_{i-1}$ 
- IV: A data block that is that same size as cipher block.
- Identical plaintext blocks mapped to different ciphertext.    
  Chaining dependencies: C<sub>i</sub> depends on all preceding plaintext.    
  Self-synchronizing: if an error occurs in C<sub>i</sub> but not in C<sub>i + 1</sub>, then C<sub>i + 2</sub> is correctly decrypted.
- CBC appropriate for encrypting messgaes of length greater than b bits, and can be used for confidentiality and for authentication.
3. Cipher Feedback (CFB)
- Rather than blocks of b bits, plaintext is divided into segments(a.k.a. "units of transmission") of s bits.
- ![](Asset/CFB.jpg)
4. Output Feedback (OFB)
- Similar in structure to CFB, except for 2 differences:    
  Output of encryption function is fed back to shift register.      
  OFB operates on full blocks, not on an s-bit subset.
- ![](Asset/OFB.jpg)

#### Pubilc-Key Cryptography
- Consider transformation pairs (E<sub>e</sub>, D<sub>d</sub>) where knowing E<sub>e</sub> it is infeasible, given c, to find an m such that E<sub>e</sub>(m) = c.
- ![](Asset/PUK.jpg)
- Applications: Encryption/Decryption, Key Exchange, Digital Signature
- public-key cryptanalysis: brute-force attacks, computing private key from public key, probable-message attack.

### Week 7
#### Number theory
- Terminology: relatively prime, quotient, remainder, congruent modulo, gcd
- Extended Euclid's Algorithm
- Modular arithmetics
- Euler Totient Function
- Chinese Remainder Theorem

#### RSA Algorithm
- $C = M^e \bmod n \\ 
   M = C^d \bmod n$
- ![](/Asset/RSA.jpg)

#### Asymmetric algorithms for secret key distribution
1. Distribution of symmetric keys with RSA
- Example: SSL protocol, but if the private key (d,n) gets compromised, then secret key can be recovered by an intruder from previously observed traffic.

### Week 8
#### Asymmetric algorithms for secret key distribution
1. Diffie-Hellman key exchange
- A primitive root s of a prime number p is a number whose powers generate 1,...,p-1.   
  $b = s^i \bmod p$, where 1 <= i < p   
  and i is called the discrete logarithm of b for base s, mod p.
- ![](/Asset/Diffie.jpg)
- It is very difficult to calculate discrete logarithms, and security depends on the difficulty of computing discrete logarithms.
- The Diffie-Hellman key exchange is vulnerable to man-in-the-middle attack because it does not authenticate the participants. But this vulnerability can be overcome with the use of digital signatures and public-key certificates to achieve mutual authentication between A and B.
- El Gamal variant of Diffie-Hellman key exchange and Massey-Omura scheme  
2. Message Integrity
- A hash function h(x) has the properties of compression and polynomial time computable, and h(x) is one-way (or pre-image resistant), hash value also called message digest or modification detection code.
- ![](/Asset/hash.jpg)
3. Message Authentication
- Message Authentication codes(MACs), a MAC algorithm is a family of hash function h<sub>k</sub> parameterized by a secret key k. h<sub>k</sub> must be computation-resistant: given zero or more MAC pairs , it is infeasible to compute a new input.    
  $c_1 = E_K (m_1 \oplus 0), c_i = E_K (c_i-1 \oplus m_i)$
- Digital signatures, M is set of messages that can be signed, S is set of elements called signatures, $S_A: M \rightarrow S$, is a signing transformation, $V_A: M \times S \rightarrow {true,false}$ is a verification transformation. This is called Digital Signature Algorithm (DSA).


### Week 9
#### Security Protocols
- Security protocols use cryptographic mechanisms to achieve security objectives. For example, Entity or message authenication, key establishment, ...
- The Needham-Schroeder Public Key Protocol (NSPK), 
  $\begin{array}{ll}A \rightarrow B: & \{NA, A\}_{K_{B}} \\B \rightarrow A: & \{NA, N B\}_{K_{A}} \\A \rightarrow B: & \{NB\}_{K_{B}}\end{array}$ 
- The Kerberos Protocol intended to have three components to guard a network's gate: authentication, accounting, and audit. It has some requirements: secure, reliable, transparent, scalable.
  1. A to KAS, m: A, TGS
  2. KAS to A, m: Time-limited session key(K<subA,TGS</sub>>) and an encrypted ticket AuthTicket.
  3. A to TGS, m: AuthTicket, authticator, B
  4. TGS to A, m: A new session key K<sub>AB</sub>, and a new ticket ServTicket
  5. A to B, m: ServTicket and a new authticator
  6. B to A(optional), m: authenticating service.


### Week 10
#### Authentication and passwords
1. Anything
- Cryptographic challenge-response protocols, this is done by providing a response to a time-variant challenge, where the response depends on both the entity's secret and the challenge.
- Increase the entropy, password ageing, passphrases, PINs(Personal indentification numbers), MFA(Multi-factor authentication), One-time passwords
2. Zero-konwledge Proofs
- Fiat-Shamir Identification Protocol,      
  ![](/Asset/fait.jpg)
- Feige-Fiat-Shamir Protocol, Guillou-Quisquater Protocol
3. Social Engineering
- Important user, Third-party Authorization, Tech Support
- Computer-based social engineering: mail attachments, website, popup windows, fake wireless network.
- Phishing, SMiShing, Vishing.
