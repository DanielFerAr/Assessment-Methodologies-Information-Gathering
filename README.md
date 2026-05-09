# Assessment-Methodologies-Information-Gathering
INE CTF resolution preparing for the eJPT

A website is available at http://target.ine.local. Perform reconnaissance and capture the following flags.

Flag 1: Which search engines to use and which not to use.

By analyzing FLAG1, it can be inferred that the answer is located in the `robots.txt` file. This file is used to define which website paths can be accessed by search engines. To view it, simply append `/robots.txt` after the IP address or URL in the browser.

<img width="720" height="309" alt="image" src="https://github.com/user-attachments/assets/7c68b122-88dc-4f98-b02b-be8f77f2ec48" />

Flag 2: What website is running on the target device and what is its version?

In Flag 2, the `nmap -sCV -A -O target.ine.local` scan is performed, carrying out a scan of open ports, active services and their versions, executing basic reconnaissance and enumeration scripts, detecting the host operating system, and gathering additional information such as network routes (traceroute), with the purpose of obtaining as much information as possible about the target machine.

<img width="720" height="268" alt="image" src="https://github.com/user-attachments/assets/a2cfb8cf-75bd-4386-a165-e7e660dcfbe8" />

Flag 3: Explore the directories that might reveal where the files are stored.

For flag 3, a basic directory scan is performed using the dirb tool, checking every file and directory.

<img width="720" height="587" alt="image" src="https://github.com/user-attachments/assets/f9623b78-fed8-409a-8b44-b205dc2a7d89" />

By meticulously examining the scan results, dirb provides us with paths that you cannot access, but can still list.

<img width="720" height="394" alt="image" src="https://github.com/user-attachments/assets/0b78c1c1-bc6d-45e1-87a6-3a099b5c2a29" />

The third flag can be found on one of these routes.

http://target.ine.local/wp-content/uploads/

