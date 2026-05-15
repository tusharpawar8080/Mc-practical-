Experiment 1: Walsh Code Based CDMA System using Python

This experiment demonstrates the working of Code Division Multiple Access (CDMA) using Walsh Codes.
Multiple users transmit data simultaneously over the same channel, and the receiver recovers the desired user's data using orthogonal Walsh codes.


---

1. Complete Python Program

import numpy as np

# Walsh Codes
c1 = [1, 1, 1, 1]
c2 = [1, -1, 1, -1]
c3 = [1, 1, -1, -1]
c4 = [1, -1, -1, 1]

rc = []

print("===== CDMA using Walsh Codes =====")

# Input data bits
print("Enter the data bits (+1 or -1):")

d1 = int(input("Enter D1: "))
d2 = int(input("Enter D2: "))
d3 = int(input("Enter D3: "))
d4 = int(input("Enter D4: "))

# Multiply data bits with Walsh codes
r1 = np.multiply(c1, d1)
r2 = np.multiply(c2, d2)
r3 = np.multiply(c3, d3)
r4 = np.multiply(c4, d4)

print("\nEncoded Signals:")
print("R1 =", r1)
print("R2 =", r2)
print("R3 =", r3)
print("R4 =", r4)

# Combine all signals
resultant_channel = r1 + r2 + r3 + r4

print("\nResultant Channel Signal:")
print(resultant_channel)

# Select receiver station
channel = int(input("\nEnter station to listen "
                    "(C1=1, C2=2, C3=3, C4=4): "))

# Assign receiver code
if channel == 1:
    rc = c1
elif channel == 2:
    rc = c2
elif channel == 3:
    rc = c3
elif channel == 4:
    rc = c4
else:
    print("Invalid Channel")
    exit()

print("\nReceiver Code:", rc)

# Inner product operation
inner_product = np.multiply(resultant_channel, rc)

print("\nInner Product:")
print(inner_product)

# Recover transmitted bit
res1 = sum(inner_product)
data = res1 / len(inner_product)

print("\nRecovered Data Bit:", data)


---

2. Aim of Experiment

To implement a CDMA communication system using Walsh codes and recover the transmitted data bits at the receiver side using orthogonal coding.


---

3. Theory

What is CDMA?

CDMA (Code Division Multiple Access) is a multiple access technique in which:

Multiple users share the same communication channel simultaneously.

Each user is assigned a unique code.

Data is spread using that unique code.

Receiver extracts the required signal using the same code.



---

4. Walsh Codes

Walsh codes are:

Orthogonal binary sequences

Used in CDMA systems

Cross-correlation between different codes is zero


Given Walsh Codes:

C1 = [1,1,1,1]

C2 = [1,-1,1,-1]

C3 = [1,1,-1,-1]

C4 = [1,-1,-1,1]

These are orthogonal because:

C1 \cdot C2 = 0

C1 \cdot C3 = 0

etc.


---

5. Working of Program

Step 1: Input Data Bits

User enters data bits:

d1, d2, d3, d4

Allowed values:

+1 → binary 1

-1 → binary 0



---

Step 2: Encoding

Each data bit is multiplied by its Walsh code.

Example:

If:

D1 = 1

Then:

R1 = D1 \times C1

If:

D2 = -1

Then:

R2 = -1 \times C2


---

Step 3: Channel Combination

All encoded signals are added:

R = R1 + R2 + R3 + R4

This forms the resultant channel signal.


---

Step 4: Receiver Selection

Receiver chooses the desired code.

Example:

rc = c2


---

Step 5: Decoding

Receiver multiplies resultant signal with receiver code:

Inner\ Product = R \times rc

Then sums the values:

Recovered\ Data = \frac{\sum InnerProduct}{N}

where:

 = length of code



---

6. Example

Suppose:

D1 = 1



D3 = 1



Encoded signals:

R1 = [1,1,1,1]

R2 = [-1,1,-1,1]

R3 = [1,1,-1,-1]

R4 = [-1,1,1,-1]

Resultant:

[0,4,0,-2]

If receiver selects C2:

Recovered bit becomes:

-1


---

7. Output Explanation

Encoded Signals

Shows spread spectrum signal for each user.


---

Resultant Channel

Combined transmission signal from all users.


---

Inner Product

Correlation operation between received signal and receiver code.


---

Recovered Data Bit

Final decoded bit of selected user.


---

8. Possible Modifications / Improvements

1. Use Dynamic Walsh Codes

Instead of fixed 4-bit codes:

Generate Walsh matrix dynamically

Allow more users


Example:

from scipy.linalg import hadamard


---

2. Support Binary Inputs

Accept:

0 and 1 instead of ±1


Conversion:

if bit == 0:
    bit = -1


---

3. Add Noise

Simulate noisy communication channel:

noise = np.random.normal(0,1,4)
resultant_channel += noise


---

4. Graphical Representation

Plot transmitted signals:

import matplotlib.pyplot as plt


---

5. Error Detection

Add BER (Bit Error Rate) calculation.


---

6. Multiple Bit Transmission

Transmit sequences instead of single bits.

Example:

d1 = [1,-1,1]


---

7. GUI Based Project

Use:

Tkinter

PyQt


for better visualization.


---

9. Advantages of CDMA

High security

Better bandwidth utilization

Multiple users simultaneously

Reduced interference

Resistance to noise



---

10. Disadvantages

Complex receiver design

Synchronization required

Near-far problem

Complex code generation



---

11. Applications of CDMA

Mobile communication

GPS systems

Satellite communication

Military communication

3G networks



---

12. Viva / Oral Questions

Basic Questions

1. What is CDMA?


2. What are Walsh codes?


3. Why are Walsh codes orthogonal?


4. What is spreading in CDMA?


5. What is despreading?




---

Program Related Questions

6. Why do we use +1 and -1 instead of 0 and 1?


7. What is the purpose of np.multiply()?


8. Why are signals added together?


9. What is inner product?


10. Why divide by length of code?




---

Conceptual Questions

11. What happens if codes are not orthogonal?


12. What is multiple access?


13. Difference between FDMA, TDMA, and CDMA?


14. What is cross-correlation?


15. Why is CDMA secure?




---

Advanced Questions

16. What is the near-far problem?


17. How does CDMA resist interference?


18. What is spreading gain?


19. Explain Hadamard matrix.


20. How can you increase number of users?




---

13. Expected Viva Answers

Q. Why are Walsh codes used?

Walsh codes are orthogonal, so signals from different users do not interfere with each other.


---

Q. Why divide by code length?

To normalize the correlation result and recover the original transmitted bit.


---

Q. What happens if wrong code is selected?

Receiver cannot recover correct data because orthogonality property fails.


---

14. Conclusion

The experiment successfully demonstrates:

Encoding using Walsh codes

Simultaneous transmission of multiple users

Recovery of desired signal using orthogonal codes


Thus, the basic principle of CDMA communication is verified successfully.
