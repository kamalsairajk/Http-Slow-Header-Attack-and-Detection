# Http-Slow-Header-Attack-and-Detection
A Slowloris attack occurs in 4 steps:
1.	The attacker first opens multiple connections to the targeted server by sending multiple partial HTTP request headers.
2.	The target opens a thread for each incoming request, with the intent of closing the thread once the connection is completed. In order to be efficient, if a connection takes too long, the server will timeout the exceedingly long connection, freeing the thread up for the next request.
3.	To prevent the target from timing out the connections, the attacker periodically sends partial request headers to the target in order to keep the request alive. 
4.	The targeted server is never able to release any of the open partial connections while waiting for the termination of the request. Once all available threads are in use, the server will be unable to respond to additional requests made from regular traffic, resulting in denial-of-service.

STEPS FOR MITIGATION OF SLOW LORIS ATTACK
1.	Packets received by the server can be accessed using tcpdump, which stores these packets into pcap files
2.	Pcap files are analyzed using scapy. Malicious clients generally have low success rate (successful GET requests/total requests) and they have high number of unsuccessful packets as compared to regular clients over a period of time.
3.	For regular packets, complete requests were sent from regular client with ip spoofing showing 25 clients.
4.	Plotting graphs.
5.	From the above graphs, it is evident that the client with IP 192.168.137.204 is the malicious client and it can be blacklisted
