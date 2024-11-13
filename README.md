
# Project Overview: Privacy-Preserving Analytics on Student Disciplinary Data with Side-Channel Protection Mechanism

**Team Members:** Artem Dinh, Furkan Sarikaya, Tom Lu  
**Class:** CS151-03: Privacy, Security, and Data   
**Instructor:** Professor Johes Bater

---

### 📄 Summary

This project applies differential privacy techniques to student disciplinary data from New Mexico school districts (2010-11 to 2021-22), containing sensitive information on demographics, infractions, and disciplinary actions. Our primary goal is to secure individual privacy while facilitating safe data analytics. We incorporate side-channel attack prevention to mitigate information leakage from timing variations.

---

### 🌟 Objectives

1. **Implement Differential Privacy**  
   Protect student identities using differential privacy, particularly the K-ary randomized response mechanism, to add controlled noise to sensitive columns.
   
2. **Prevent Side-Channel Leakage**  
   Identify and mitigate timing-based side-channel attacks that could leak sensitive information through variations in execution time.

3. **Evaluate Privacy-Utility Trade-Offs**  
   Balance data utility with privacy protections to ensure data remains actionable for analytics.

---

### 📊 Dataset Structure & Privacy Concerns

The dataset includes:
- **Demographics**: race, gender, grade level.
- **Incident Details**: types of infractions (e.g., drug, alcohol, hate crimes).
- **Disciplinary Actions**: responses taken by the schools.

**Privacy Risks**  
Re-identification and side-channel risks are prominent. Side-channel attacks could exploit timing differences in the data processing pipeline, potentially inferring sensitive information based on the response time of queries.

---

### 🔍 Differential Privacy Implementation: K-ary Randomized Response

**Privacy Mechanism: K-ary Randomized Response**  
To protect sensitive data columns, we used the K-ary randomized response mechanism. By adding controlled noise, we ensure that individual data points are obfuscated to prevent direct identification. We vary the noise based on an adaptive `epsilon` value, which is adjusted based on the size of each group (e.g., school district) to provide stronger privacy for smaller groups.

- **Epsilon Values**: Privacy levels are controlled through an `epsilon` parameter that adjusts the probability of flipping values based on group size. Lower values indicate stronger privacy for sensitive, smaller groups, while larger groups have slightly relaxed privacy budgets for better utility.

- **Noising Approach**: For each sensitive column, values are flipped randomly based on an epsilon-dependent probability, adding privacy while preserving some level of utility for each column.

![image](https://github.com/user-attachments/assets/a985107f-13cd-4889-a1b2-8a1f3e475f5d)
![image](https://github.com/user-attachments/assets/2d519966-300e-4280-bd73-dbe2da1adcce)

---
### ⚖️ Balancing Privacy & Utility

We evaluated the privacy-utility trade-offs by applying different configurations of epsilon values, with larger privacy budgets (higher epsilon values) allowing for more data utility at the cost of slightly reduced privacy. We measured the runtime impacts of these configurations with and without side-channel protections.

---

### 🔐 Side-Channel Attack Vulnerability & Prevention

**Understanding Time Leakage Attack**  
A side-channel attack in this context leverages timing discrepancies to deduce sensitive information about whether or not a data value was altered. When using randomized response mechanisms, even small timing variations during value flips could reveal insights, particularly if attackers can access repeated observations of the system.

**Initial Vulnerability**  
In our initial function, `flip_value`, the value of `x` was either retained or replaced with another random value based on a flip probability. If `x` was not flipped, the function simply returned it directly, taking slightly less time than if `x` had been replaced. These timing differences introduced a risk of side-channel leakage by potentially allowing attackers to deduce whether or not a value was flipped.

**Time Leakage Protection Mechanism**  
To prevent side-channel leaks, we modified the function as follows:
- **Consistent Execution Path**: In the updated function `flip_value_SideChannel`, even if the value is not flipped, the function still selects an alternative random value from the domain and discards it, before returning `x`. This added operation ensures that every call to the function takes approximately the same amount of time.
- **Equalized Timing**: By maintaining a consistent execution path regardless of the flip decision, we eliminate the timing discrepancies that could have allowed attackers to infer whether values were flipped or retained.

---

### 📈 Side-Channel Protection Results

Our runtime analysis compared the timing impact of configurations with and without side-channel protection:
- **Secure Configuration**: The side-channel-protected version (`flip_value_SideChannel`) showed consistent runtimes across all operations, mitigating the potential for timing-based inference attacks.
- **Performance Metrics**: Our tests, with mean and standard deviation calculations, confirmed that the protected function eliminates timing discrepancies, achieving secure execution without significant runtime overhead.

![image](https://github.com/user-attachments/assets/3c188124-9982-47ee-a0ce-1a90f8899d48)

---

### 🔄 Recommendations for Future Work

1. **Strengthen Side-Channel Protections**  
   Future enhancements could explore additional timing equalization techniques to further reduce vulnerability to side-channel attacks.

2. **Alternative Privacy Libraries**  
   Testing libraries such as OpenDP or TensorFlow Privacy could reveal more sophisticated privacy-preserving methods that integrate seamlessly with machine learning models or provide additional defense mechanisms against side-channel risks.

---

This project demonstrates how differential privacy and side-channel protections can be integrated into sensitive data analytics to balance actionable insights with stringent privacy standards.

---


![image](https://github.com/user-attachments/assets/6d360ca1-b0a4-4073-9305-f6b3dd294100)

![image](https://github.com/user-attachments/assets/634dc3b4-9317-4e36-95c7-5f86351e73c6)
