# Dynamic Application Security Testing (DAST) Project

## Objective

This project focused on performing **Dynamic Application Security Testing (DAST)** on a simulated web application environment for ABC Corp. The primary goal was to identify and understand runtime security vulnerabilities using **OWASP ZAP** in headless mode on **Kali Linux**. This hands-on lab reinforced skills in automated web application scanning, tool configuration, and interpreting vulnerability reports.

### Skills Learned

- Practical experience in configuring and operating OWASP ZAP in headless mode.
- Understanding of dynamic scanning techniques and runtime vulnerability detection.
- Familiarity with the structure and interpretation of DAST scan reports (XML format).
- Improved command-line proficiency in a Kali Linux environment.
- Strengthened workflow for identifying and remediating web application security issues.

### Tools Used

- **OWASP ZAP** for automated dynamic security scanning.
- **Kali Linux** as the operating environment.
- **Java**, **Python3**, and **Git** for tool installation and system configuration.
- **ABC Corp Web Application** (simulated environment) as the scanning target.

## Steps

### 1. **Set Up Kali Linux Environment**
   - Updated packages and installed required dependencies (`Java`, `Python3`, `Git`)


*Ref 1: update and upgrade packages*

<img width="294" height="182" alt="1 updating packages" src="https://github.com/user-attachments/assets/721e017b-4d2e-4dc7-8658-b844744b1401" />

<img width="309" height="86" alt="2 updating packages" src="https://github.com/user-attachments/assets/3762d546-3b74-4813-8c3b-e49d798e9193" />

*Ref 2: Installing Java and confirming version is newer than 17 for OWASP ZAP to run*

<img width="487" height="67" alt="3 installing jdk (java)" src="https://github.com/user-attachments/assets/05c96fb6-2794-4f08-af63-369b05e7f960" />

<img width="660" height="80" alt="4 confirming java version newer than 17" src="https://github.com/user-attachments/assets/54469da8-fcf3-4e5b-ae88-d4fb3713fed3" />

*Ref 3: Installing Git*

<img width="359" height="46" alt="5 installing git" src="https://github.com/user-attachments/assets/e5bb7e59-f5e2-4ff4-a0e3-707c9172a291" />

*Ref 4: Installing Python*

<img width="470" height="64" alt="6 installing python" src="https://github.com/user-attachments/assets/13f2865b-88d0-4f02-a248-0bc78f5463d0" />

*Ref 5: Creating a directory for ZAP reports*

<img width="567" height="40" alt="7 create a directory for test reports" src="https://github.com/user-attachments/assets/a9ee6a42-3d47-4980-a980-54fc8a8ad67c" />


### 2. **Deployed Target Application**
   - Downloaded and launched the simulated ABC Corp web application locally on Kali Linux.
   

*Ref 6: Downloading the web app from Git*

<img width="734" height="136" alt="8 downloading the web app to run tests on" src="https://github.com/user-attachments/assets/947695ae-5020-4fce-969e-952a9e55bf06" />

*Ref 7: Installing required python libraries for web app*

<img width="910" height="497" alt="9 installing required libraries for web app" src="https://github.com/user-attachments/assets/59f09bcf-1efb-4860-967a-63479eafc145" />

*Ref 8: Running the web app in the background with both standard output and standard error being output to a file*

<img width="519" height="64" alt="10 running web app" src="https://github.com/user-attachments/assets/4b31876e-94ce-456a-8b11-c1c3873c7065" />

*Ref 9: Confirming web app is running with http 200 OK response*

<img width="666" height="178" alt="11 confirming web app is running" src="https://github.com/user-attachments/assets/b9bcdd42-42fc-483b-a00c-8c11436de9c4" />


### 3. **Installed and Configured OWASP ZAP**
   - Downloaded and set up OWASP ZAP.
   - Configured it to run in headless mode for automated scanning.

*Ref 10: Downloading OWASP ZAP*

<img width="870" height="71" alt="12 downloading OWASP ZAP" src="https://github.com/user-attachments/assets/de2558e2-89ef-44f8-95d8-d20c2195468f" />

*Ref 11: Extracting compressed files in verbose mode*

<img width="489" height="78" alt="13 extracting compressed files" src="https://github.com/user-attachments/assets/3d68982f-ba4f-450e-acd6-35ad7a2dc8e6" />

*Ref 12: Verifying ZAP runs on Kali*

<img width="825" height="216" alt="14 verifying ZAP runs on kali" src="https://github.com/user-attachments/assets/50bf7355-3792-4beb-8539-776a3469b89f" />


### 4. **Performed DAST Scan**
   - Executed the scan using OWASP ZAP against the running web application.
   - Verified coverage of endpoints and monitored scan progress.
  
*Ref 13: Running ZAP Scan on web application with the following arguments*
   - *./zap.sh -cmd* - to run ZAP in command line mode
   - *-quickprogress* - to provide condensed output for the progress of the scan
   - *-quickurl* - to do a quick scan of the target url (in our case, our loopback address at port 64512)
   - *-quickout* - to output the results to a report in the reports directory created earlier

<img width="889" height="68" alt="15 Running ZAP on web application" src="https://github.com/user-attachments/assets/e4ad0faf-a74c-4a51-8d19-0e7a6e36c8a6" />



### 5. **Generated and Reviewed Report**
   - Exported the scan results in **XML** format.
   - Analyzed findings to identify common web vulnerabilities like XSS, SQL Injection, and broken authentication.

*Ref 14: Reading ZAP report in command line*

 <img width="713" height="74" alt="16 reading ZAP report on application" src="https://github.com/user-attachments/assets/5cd184e0-2d29-4cc0-b711-8f8492b865bc" />

 *Ref 15: Analyzing report alerts generated by ZAP*
   - *(shown below)*
     - Five instances of CSP Header not set
   - *(not shown below)*
     - Three instances of Missing Anti-clickjacking Header
     - Five instances of leaked version information via HTTP Response Header
     - Three instances of X-Content-Type-Options Header Missing
     - Five instance of Information Disclosure - Suspicious Comments

<img width="671" height="143" alt="17 CSP Header not set" src="https://github.com/user-attachments/assets/abbcc313-8a6e-4426-9ebe-966cd39a0d31" />

<img width="1309" height="87" alt="18 five instances of csp header" src="https://github.com/user-attachments/assets/3cad4925-b9f3-4b7b-bfef-f4218e3e05f2" />


## Notes

This project was completed in a simulated lab environment. No external or unauthorized systems were scanned. This work was done strictly for educational purposes.
