# SMTP User Enumeration
quoted from [this site](https://pentestlab.blog/2012/11/20/smtp-user-enumeration/)

SMTP is a service that can be found in most infrastructure penestration tests. This service can help the penestration tester to perform username enumeration via the EXPN and VRFY commands if these commands have not been disabled by the system administrator. There are a number of ways which this enumeration through the SMTP can be achieved.

The role of the EXPN command is to reveal the actual address of users aliases and lists of email and VRFY which can confirm the existence of names of valid users.

The SMTP enumeration can be performed manually through utilities like telnet and netcat or automatically via
a variety of tools like metasploit, nmap and smtp-user-enum. The following 2 screenshots are showing how we can enumerate 
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTM5MTUzOTQ2LDIwMTQyMTA5MDNdfQ==
-->