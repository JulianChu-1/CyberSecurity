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
   - Generalize Caesar cipher by allowing an arbitrary (任意的) substitution.
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

### Week 4
#### Steganography and Composite ciphers
   - Conceal the existence of the message. For example, Arrangement of words or letters, Invisible ink, Pin punctures.
   - Watermarking and DRM (Digital Rights Management)
   - Product ciphers chain substitution-transposition combinations. One example is Rotor machines used in WW2. Used a series of cylinders, each giving one substitution, which rotated and changed after each letter was encrypted.

#### Feistel cipher
   - ![](Asset/Feistel.jpg)
   - Small block size (e.g., n = 4): equivalent to a classical cipher and thus easily attackable. However, large block size: not practical implementation and performance. So, Feistel's suggestion is **invertible product cipher**.
   - **Product cipher**: Execution of 2 or more simple ciphers in sequence so that the result is cryptographically stronger. Alternates substitutions and permutations.
   - **S-Boxes and P-Boxes**, a proposal by Shannon to develop a product cipher that alternates confuse and diffusion functions. S-Boxes "confuse" input bits; P-Boxes "diffuse" bits across S-box inpus.
   - ![](Asset/FeistelEncryption.jpg)
   - A substitution is performed on LE<sub>i</sub> by applying a **round function** F to RE<sub>i</sub> and then XORing output with LE<sub>i</sub>.F has same general structure for each round is parameterized by round subkey K<sub>i</sub>. Then a permutation is performed: interchange of two halves of data.
   - 

### Week 5
1. DES De

