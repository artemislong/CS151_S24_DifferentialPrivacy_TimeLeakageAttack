# CS151_Spring2024_DifferentialPrivacy_EducationProject
---

# Project Overview: Privacy-Preserving Analytics on Student Disciplinary Data

**Team Members:** Artem Dinh, Furkan Sarikaya, Tom Lu  
**Class:** CS151-03: Privacy, Security, and Data
**Instructor:** Professor Johes Bater

---

### 📄 Summary
This project analyzes student disciplinary data from New Mexico school districts (2010-11 to 2021-22). The data includes sensitive information such as student demographics, infraction types, and disciplinary actions. The goal is to implement differential privacy measures to protect individual privacy while gaining insights into disciplinary patterns, repeat offenses, racial disparities, and drug-related incidents. Additionally, we explore the implications of potential side-channel attacks on data privacy.

---

### 🌟 Objectives
1. **Protect Privacy**  
   Implement differential privacy mechanisms to safeguard student identities, addressing re-identification risks and mitigating the impact of side-channel attacks.
   
2. **Analyze for Insights**  
   Extract meaningful insights to inform policies, resource allocation, and student support strategies, balancing data utility with privacy.
   
3. **Evaluate Privacy-Utility Trade-offs**  
   Assess the impact of privacy protections on data accuracy to ensure both security and actionable insights.

4. **Address side-channel attack vulnerability**  
   Identify and sufficiently prevent information leakage from timing side-channel attack.
---

### 📊 Dataset Structure & Privacy Concerns
The dataset includes:
- Student demographics: race, gender, grade level.
- Incident details: types of infractions (e.g., drug, alcohol, hate crimes).
- Responses: disciplinary actions taken by schools.

**Privacy Risks**  
Key risks include re-identification and side-channel attacks, where attackers might infer sensitive information indirectly (e.g., through response timing or access patterns). To address these, the project applies differential privacy, particularly the K-ary randomized response mechanism, which adds controlled noise to sensitive data columns.

---

### 🔍 Analytical Methods & Key Findings
1. **Privacy Mechanism: K-ary Randomized Response**  
   Noise is added selectively to sensitive columns based on a configured probability (epsilon), which controls privacy levels according to the data’s sensitivity. Additional precautions were taken to reduce side-channel leakage.

2. **Query Results: Key Insights**  
   - **Repeat Offenses:** Approximately 37% of disciplinary incidents are from repeat offenders, suggesting that the current disciplinary measures may need revision.
   - **Grade-Level Patterns:** A spike in infractions occurs when students move from elementary (5th grade) to middle school (6th grade), indicating possible adjustment challenges.
   - **Racial Disparities:** Native Hawaiian students face a disproportionate rate of arrest, highlighting a potential racial bias in disciplinary practices.
   - **Drug-Related Infractions:** A substantial portion of serious incidents involves drugs, suggesting a need for focused prevention policies.

---

### ⚖️ Balancing Privacy & Utility
**Error Tolerance**  
The project set an acceptable mean absolute error of 5% to maintain data accuracy. Different privacy budgets were applied based on the data's intended use, allowing for adjustments in accuracy where higher precision is needed.

**Result**  
The privacy-preserving approach, with considerations for side-channel risks, maintained data utility within the set error tolerance, demonstrating that differential privacy mechanisms can effectively protect sensitive information without significant loss of data quality.

---

### 🔄 Recommendations
1. **Enhanced Support for Students**  
   High repeat offense rates indicate a need for supportive rather than purely punitive disciplinary approaches.

2. **Focused Policy for Middle School**  
   The increase in infractions among 6th graders suggests a need for targeted policies to ease the transition from elementary to middle school.

3. **Address Racial Disparities**  
   Disproportionate arrest rates for Native Hawaiian students highlight a need to review disciplinary policies for potential biases.

4. **Drug Prevention Initiatives**  
   Drug-related incidents should be addressed with preventive programs aimed at reducing their occurrence in schools.

---

### 📈 Future Improvements
- **Strengthening Side-Channel Protections**  
  Future work should explore additional mitigations to further reduce vulnerability to side-channel attacks, such as timing or access-pattern leaks.

- **Exploration of Alternative Privacy Libraries**  
  Investigate other privacy libraries like OpenDP or TensorFlow Privacy to explore more sophisticated privacy-preserving methods.

---

This project provides a blueprint for privacy-preserving analysis in sensitive data sectors, showcasing how to balance actionable insights with stringent privacy protections and defenses against side-channel vulnerabilities.

---

This project provides a blueprint for privacy-preserving analysis in sensitive data sectors, showcasing how to balance actionable insights with stringent privacy protections and defenses against side-channel vulnerabilities.
