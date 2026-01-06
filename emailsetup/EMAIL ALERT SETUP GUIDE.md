EMAIL ALERT SETUP (GMAIL) — STEP BY STEP


Objective



Enable the project to automatically send email alerts when the ML-based Self-Healing module detects critical/faulty cells, without exposing credentials in code.



This is achieved using:



Gmail App Passwords



Environment Variables



Python SMTP



**1. Why App Passwords Are Required**



Google does NOT allow direct login using your Gmail password for scripts.



Instead, Google provides App Passwords:



Limited access



Revocable



Secure



Industry best practice



**2. Enable 2-Step Verification (Mandatory)**



Open:



https://myaccount.google.com/security





Under “Signing in to Google”



Enable 2-Step Verification



Complete verification using:



Phone / Authenticator app



Without this step, App Passwords will not appear.



**3. Generate Gmail App Password**



Go to:



https://myaccount.google.com/apppasswords





Select:



App: Mail



Device: Other (Custom)



Name it:



SON Self-Healing Alert





Click Generate



Copy the 16-character password

(example: abcd efgh ijkl mnop)



⚠️ IMPORTANT



This is NOT your Gmail password



Copy it once and store securely



**4. Store Credentials as Environment Variables**

Option A: Google Colab (Recommended for Presentation)



Run this once per session:



import os



os.environ\["EMAIL\_ADDRESS"] = "your\_email@gmail.com"

os.environ\["EMAIL\_PASSWORD"] = "your\_16\_char\_app\_password"





These values:



Are NOT visible in GitHub



Are erased when runtime resets



Option B: Local System (Windows)



Open Command Prompt and run:



setx EMAIL\_ADDRESS "your\_email@gmail.com"

setx EMAIL\_PASSWORD "your\_16\_char\_app\_password"





Restart terminal after this.



**5. Access Credentials in Python Code**



Your code should never hardcode credentials.



Correct way:



import os



EMAIL\_ADDRESS = os.getenv("EMAIL\_ADDRESS")

EMAIL\_PASSWORD = os.getenv("EMAIL\_PASSWORD")





If either value is None, email sending is skipped safely.



**6. How Email Is Triggered (Logic Flow)**



ML model runs (Isolation Forest)



Faulty cells are detected



Cells are classified as:



Normal



Warning



Critical



If Critical cells exist:



KPI summary is generated



Email content is formatted



SMTP connection opens



Email is sent



Connection closes



This simulates a real self-healing NOC alert.



**7. SMTP Configuration Used**

smtp.gmail.com

Port: 587

TLS: Enabled





This is Gmail’s official SMTP configuration.

