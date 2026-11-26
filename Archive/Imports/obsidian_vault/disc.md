---
type: note
topic: school
---

Non-functional requirements:
1. API calls to ancillary services should be processed within 10 seconds of reception 
2. Biometric log-in should take less than 20 seconds 
3. Modifying a customer's account should have a <0.1% failure rate 
4. System should be able to endure 10% of records being changed at a time
5. System should be able to store data on SSDs and HDDs 

Functional requirements:
1. The system will prompt for user information when opening an account 
2. The system will require biometric log-in for staff to perform account transfers 
3. The system will email clients about account changes 
4. The system will require biometric authentication and client approval through an email link when closing an account 
5. The system will allow cashing of checks 