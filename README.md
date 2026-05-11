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

<img width="720" height="186" alt="image" src="https://github.com/user-attachments/assets/b4dc6282-9ddc-4ab8-85a0-9761edf7f971" />

Flag 4: An overlooked backup file in the webroot can be problematic if it reveals sensitive configuration details.

Using WordPress, we searched Google for the backup file path. We found the URL; entering it will download a file with the `.bak` extension. Simply use `cat` to view the result and you'll get the flag.

<img width="720" height="163" alt="image" src="https://github.com/user-attachments/assets/cf18a299-ece1-4b63-806a-01285706eda5" />

<img width="720" height="226" alt="image" src="https://github.com/user-attachments/assets/f45fa9dc-3652-4af9-b8f6-bb49983de53d" />

Flag 5: Certain files may reveal something interesting when mirrored.

We used httrack, the tool for duplicating websites. We used the default httrack command with the URL and saved the output to a directory.

httrack http://target.ine.local -O INE 

We navigated to the path where we saved the output and found many files and directories. This generated a long list, which we're not interested in, so we'll use grep to search for the flag throughout the directory. 

grep -i "FLAG5" -R target.ine.local/

<img width="720" height="93" alt="image" src="https://github.com/user-attachments/assets/86dc1d56-a8ba-4c72-82b6-51b2c47cce84" />


And that's how we found all the flags.
