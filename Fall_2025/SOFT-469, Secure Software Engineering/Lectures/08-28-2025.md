![[M01A_Introduction.pdf]]

Software is often the last line of defense against attacks and too often fails. Defending against attacks requires PPT (people, process and technology) with software representing a fraction of technology and being bound to the rest of PPT

Security isn't hardware, software, policies or procedures - it's a condition. Freedom from risk or danger (safety) and freedom from doubt, anxiety, or fear (confidence)

CIA TRIAD
- <mark style="background: #ADCCFFA6;">Confidentiality</mark>: Preserving authorized restrictions on information access and disclosure, including means for protecting personal privacy and proprietary information -> <mark style="background: #BBFABBA6;">Only authorized entities can access/disclose information</mark>
- <mark style="background: #ADCCFFA6;">Integrity</mark>: Guarding against improper information modification or destruction, and includes ensuring information non-repudiation and authenticity -> <mark style="background: #BBFABBA6;">Only authorized entities can modify/delete information</mark>
- <mark style="background: #ADCCFFA6;">Availability</mark>: Ensuring timely and reliable access to and use of  -> <mark style="background: #BBFABBA6;">Information/systems are available when needed</mark>

2024 CWE Top 25 most dangerous software weaknesses:
1. Improper Neutralization of Input During Web Page Generation ('Cross-site Scripting’)
2. Out-of-bounds Write
3. Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection’)
4. Cross-Site Request Forgery (CSRF)
5. Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')
6. Out-of-bounds Read
7. Improper Neutralization of Special Elements used in an OS Command ('OS Command Injection’)
8. Use After Free
9. Missing Authorization
10. Unrestricted Upload of File with Dangerous Type
11. Improper Control of Generation of Code ('Code Injection')
12. Improper Input Validation
13. Improper Neutralization of Special Elements used in a Command ('Command Injection’)
14. Improper Authentication
15. Improper Privilege Management
16. Deserialization of Untrusted Data
17. Exposure of Sensitive Information to an Unauthorized Actor
18. Incorrect Authorization
19. Server-Side Request Forgery (SSRF)
20. Improper Restriction of Operations within the Bounds of a Memory Buffer
21. NULL Pointer Dereference
22. Use of Hard-coded Credentials
23. Integer Overflow or Wraparound
24. Uncontrolled Resource Consumption
25. Missing Authentication for Critical Function

![[Pasted image 20250828102942.png]]

To respond/reduce risk, Avoid things representing unacceptable risk, Transfer some risk to third parties, Mitigate risk with technical and non-technical controls (PPT), and Accept/Manage the residual risk