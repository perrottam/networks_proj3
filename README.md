# networks_proj3

Milestone:
We wrote our code in Python so we started with the code given to us. At a high level we implemented functionality to both update our routing table and use it to forward packets in a simple context. For updating, we do three things. First, we save the update packet we recieved for potential future use. Then, we add this entry to our forwarding table (network ip, netmask, and peer id). When we receive a data packet, we check our routing table to see if it matches an entry we have stored. If it matches one, we send it through the peer port. Else, we send back message to the source indicating the action cannot be done.

Challenges:
We had to figure out when to subtract 1 from the port in order to send a packet to the destination.

Testing:
We ran ./sim milestone and made sure the tests passed.
