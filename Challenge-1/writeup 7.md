Challenge description:
A company suspects that someone logged into their internal portal without authorization. The only evidence provided is a captured network traffic file (.pcap).Although the login page of the portal is still active, the attacker’s actions must be found out by analyzing the captured packets. The flag is hidden within the system and can only be obtained by understanding what happened during the login process.
The task is to analyze the network traffic, uncover the stolen credentials, and use this information to log into the system and retrieve the hidden flag.

Hint: Not all packets are meaningless data — some reveal more information than they should.

My approach:
The only evidence available is the network capture file. So I started by studying what a network capture file is. Then analyzed the given file. At first the packet file looked unreadable, but some packets contained normal text such as `HTTP/1.1`, `GET`, and `POST`. Using this I found that this is HTTP traffic and that it is the ineraction between the client and the server. 
On further analysis of the file, I found out the following:
1)The username and password used by the attacker to login (username=isitadmin&password=iamtheadmin). 
2)The login was successful and the attacker was directed to the welcome page (HTTP/1.1 302 FOUND
  Location: /welcome?user=isitadmin) 302 means redirect to a page.
3)After the login, the client sent a GET request to the welcome page and included the username ((GET /welcome?user=isitadmin HTTP/1.1). The server trusted this parameter(HTTP/1.1 200 OK), which resulted in the flag being displayed (FLAG{analyzing_is_imp}).

This is how I analyzed the network traffic, uncover the stolen credentials (username and password) and retrieved the hidden flag.

Tools used:
Google
ChatGPT

Final flag:
FLAG{analyzing_is_imp}
