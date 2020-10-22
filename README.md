# networks_proj3

High Level Approach

Since we were using Python, we started with the router template code provided to us. We then sequentially followed the steps outlined in the project assignment. First, we needed to be able to route the incoming packets for updating, forwarding and dumping the data. At this point we assumed all data messages were valid and legal. When we got a Data forward message, we iterate over our routing table and all routes who match based on longest net mask prefix (where n is the number of consecutive 1s starting the netmask) are chosen. A No Route message is sent back to the sender if no route was found given our algorithm. For cases where we have multiple matching routes, we use logic to filter the routes down. This includes highest pref, self-origin, shortest AS Path, origin EGP > IGP > UNK, enforcing peer relationships, etc. Next, revoke was implemented where we remove all dead entries from the routing table and call our helper to handle spreading this revoke update to all the correct neighbors based on peer relationships. The final major step was to implement coalesce and route aggregation using CIDR, where at every point our routing table changes we coalesce any routes adjacent to each other.

Challenges Faced

There were a few subtle challenges here and there, mostly regarding understanding the logic for working with the IP addresses in our forwarding table. For example, one challenge was that we were dropping data packets since they got forwarded to the wrong destination routers. This was solved by using debug mode to figure out exactly which messages with src, dest were getting dropped and where they were getting dropped.

Testing

Using debug mode and various print statements within our functions helped a lot with the testing and debugging process. This way we could ensure our forwarding table was getting updated correctly and using correct addresses, etc. We began by ensuring the level 1 tests passed, then level 2, etc up until level 6.
