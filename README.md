**Not more like ‘Hello Folks!’ but more like ‘Hello World!’**

# I'm Cybrpunked

This is my first writeup that im doing,
 And that too in Tryhackme! 

Its Called Lookup

![image](https://github.com/user-attachments/assets/ab207f5d-92cf-44d5-8ddd-a5ac93d09a7a)

Lets cut to the chase!

You will have to paste the IP & website name in the /etc/hosts initially...
after doing it you'll get this page:

![image](https://github.com/user-attachments/assets/4a0292f7-adf3-4b65-89f0-a46ae576f64c)


I tried admin:admin, but it didnt work.

so i tried using nmap if i could get something
~$ nmap <ip> -sV -T4- -p-

-sV : To know the SERVICE VERSION
-T4- : for the SPEED
-p- : To scan ALL PORTS

![image](https://github.com/user-attachments/assets/3514c0e8-2060-4707-82b7-a52f65cda053)


We got the output, and we got not so much information...

so next I tried Domain fuzzing. Unfortunately, no results.

Then I tried capturing the request in burpsuite

<picture>

NOTE: I have changed the password to FUZZ 

~$ ffuf -request log.brute -w /usr/share/wordlists/rockyou.txt -request-proto http -fs 62



~$ ffuf -request log.brute -w /usr/share/wordlists/seclists/usernames/xato-net-10-million-usernames.txt -request-proto http -fs 74



Okay... 

This looks good, lets try this out and see on our login page.

jose:password123

Lets use burp suite to see whats really happening:


Great. We can see in the response tab- login was successfull! And also we can see that the location is pointed towards “files.lookup.thm”

I go straight to /etc/hosts and add the “files.lookup.thm” to the IP address and save it. Refresh it.




