# Cybersecurity_Analysis
"Cybersecurity Analysis in Oracle SQL" is a project designed to enhance digital security by utilizing the power of Oracle SQL. This project focuses on database-based security solutions and threat analysis, leveraging Oracle SQL's capabilities to safeguard critical data and identify potential vulnerabilities.
Certainly, here are some possible SQL queries related to your cybersecurity analysis project along with their corresponding answers:

1. Question: Retrieve a list of all cybersecurity incidents with their details, including the usernames of the users who reported them.


SELECT c.INCIDENT_ID, c.INCIDENT_DATE, c.INCIDENT_TYPE, c.DESCRIPTION, u.USERNAME
FROM CYBERSECURITY_INCIDENTS c
LEFT JOIN USERS u ON c.USER_ID = u.USER_ID;
2. Question: Find the total number of cybersecurity incidents of each type.


SELECT INCIDENT_TYPE, COUNT(*) AS INCIDENT_COUNT
FROM CYBERSECURITY_INCIDENTS
GROUP BY INCIDENT_TYPE;


3. Question: List all sources of cybersecurity incidents along with the number of incidents reported by each source.


SELECT s.SOURCE_NAME, COUNT(c.INCIDENT_ID) AS INCIDENT_COUNT
FROM INCIDENT_SOURCES s
LEFT JOIN CYBERSECURITY_INCIDENTS c ON s.SOURCE_ID = c.SOURCE_ID
GROUP BY s.SOURCE_NAME;
4. Question: Retrieve the details of resolved incidents, including the incident date, type, and the department responsible for the resolution.


SELECT r.RESOLUTION_DATE, i.INCIDENT_TYPE, d.DEPARTMENT_NAME
FROM Caseresolution r
INNER JOIN CYBERSECURITY_INCIDENTS i ON r.INCIDENT_ID = i.INCIDENT_ID
INNER JOIN DEPARTMENTS d ON r.DEPARTMENT_ID = d.DEPARTMENT_ID;

5. Question: Find the most common type of cybersecurity incident and its frequency.


SELECT INCIDENT_TYPE, COUNT(*) AS INCIDENT_COUNT
FROM CYBERSECURITY_INCIDENTS
GROUP BY INCIDENT_TYPE
ORDER BY INCIDENT_COUNT DESC
FETCH FIRST 1 ROW ONLY;


6. Question: Retrieve a list of users who have reported multiple cybersecurity incidents.


SELECT u.USERNAME, COUNT(c.USER_ID) AS INCIDENT_COUNT
FROM USERS u
JOIN CYBERSECURITY_INCIDENTS c ON u.USER_ID = c.USER_ID
GROUP BY u.USERNAME
HAVING COUNT(c.USER_ID) > 1;


These SQL queries provide insights and answers to various aspects of  cybersecurity analysis project, allowing  to extract valuable information from  database. 
