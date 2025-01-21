<h2> Security Incident Report </h2>

### Section 1: Network Protocols Involved ###
**Protocols Identified:**
 
  1) **_DNS (Domain Name System)_**: Used for resolving the domain names (yummyrecipesforme.com and greatrecipesforme.com) to their corresponding IP addresses.
  2) **_HTTP (Hypertext Transfer Protocol)_**: Used for communication between the browser and the web servers for both domains.
  3) **_TCP (Transmission Control Protocol)_**: Used to establish and maintain reliable connections between the client and servers for HTTP communication.

### Section 2: Documentation of the Incident ###

**Incident Summary:**

- The website `yummyrecipesforme.com` was compromised via a brute force attack on the administrative account. The attacker exploited the fact that the admin password was set to the default, allowing them to gain access to the website's admin panel.
- Once access was obtained, the attacker modified the website's source code to include a JavaScript function prompting visitors to download a malicious executable file.
- Customers who downloaded and executed the file were redirected to a fake website, greatrecipesforme.com, which contained additional malware.
- The malicious code and redirection were discovered after multiple customer complaints about abnormal behavior on their personal computers and website redirection.

**Timeline and Details:**

1)  **_DNS Request_**: The browser sent a DNS query for `yummyrecipesforme.com`, which resolved to the IP address `203.0.113.22`.
2)  **_HTTP Connection_**: The browser established a connection to the server and initiated an HTTP GET request to load the webpage.
3)   **_Malware Download_**: The embedded JavaScript forced the browser to download an executable file disguised as a browser update.
4)  **_DNS Redirect_**: After executing the file, the browser sent a DNS query for greatrecipesforme.com, which resolved to the IP address `192.0.2.17`.
5)  **_Redirection_** : The browser connected to `greatrecipesforme.com` and was redirected to the fake malicious site.

**Evidence Sources:**

**_Tcpdump Logs_**: Show DNS and HTTP traffic during the incident, including the malware download and redirection.
**_Source Code Review_**: Confirms malicious JavaScript was embedded in the website.
**_Customer Reports_**: Indicate slow system performance and redirection after executing the file.

### Section 3: Recommendation for Preventing Brute Force Attacks ###

**Recommended Security Measure:**

1) Enforce Two-Factor Authentication (2FA):

 Why It’s Effective:
- 2FA requires an additional layer of authentication, such as a one-time passcode sent to a verified email or mobile device, in addition to the password. Even if the attacker guesses or obtains the password, they will not be able to complete the login process without the second factor.
- This significantly reduces the likelihood of unauthorized access, as brute force attacks alone would not be sufficient to bypass the security measure.
Additional Best Practices:

2) Enforce strong password policies requiring a mix of uppercase, lowercase, numbers, and special characters.
 
- Limit the number of login attempts and implement account lockout after multiple failed attempts.
- Regularly monitor login attempts for unusual patterns and alert administrators of suspicious activities.

This incident highlights the importance of proactive security measures, such as 2FA and strong password policies, to safeguard administrative accounts and prevent similar attacks in the future.
