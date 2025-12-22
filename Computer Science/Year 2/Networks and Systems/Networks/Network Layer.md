 #nas 

# Routing Algorithms 

**Routing** is the process of discovering network paths 
- decide what to optimise 
- model network as graph 
- update routes for changes in topology

>[!important] Optimality Principle 
>If router $J$ is on the optimal path from $I$ to $K$, then the optimal path from $J$ to $K$ is on the same route 
- identify optimal path from source to dest 
- **sink tree**: optimal routes from all sources to given dest 
![[Screenshot 2025-12-22 at 14.47.21.png]]

Dijkstra's computes sink tree on graph
- each node labelled with distance from source node to best known path
- initially no paths known 
- each link assigned non-neg weight
- shortest path has lowest total weight 

Algorithm steps:
- start with sink, set dist at other nodes to infinity
- labels tentative $\circ$ or permanent $\bullet$, initially all tentative 
- pick lowest dist non-perm node, make perm 
- repeat from this node until all nodes perm
![[Screenshot 2025-12-22 at 14.52.10.png]]

# Distance Vector Routing 

Each node maintains table (vector of best dist to dest)
- table updated by exchanging info between nodes 
- tables have outgoing line and est distance (no. hops of propagation delay) entries 

Failures can cause DVR to count to infinity if node unreachable 

# Link State Routing 

1. Learn network address of neighbouring routers by sending HELLO packet, record name 
2. Set distance to each neighbour 
3. Construct packet telling all other routers learned info 
4. Send\receive packets from all other routers 
5. Compute shortest path using Dijkstra
![[Screenshot 2025-12-22 at 14.54.53.png]]

Challenge: getting packets to all routers 
- Solution: flooding 

Flooding is method to send packet to all network nodes 
- each node floods new packet on incoming link by sending on all other links 
- need to keep track of flooded packets to stop flood 

# Hierarchal Routing 

Reduces work of route computation, can result in slightly longer paths 
![[Screenshot 2025-12-22 at 14.56.33.png]]

# Broadcast Routing 

Broadcast sends packet to all nodes 

RPF (reverse path forwarding):
- arrived packets checked to see if they arrived from preferred link 
- preferred link: link that is normally used for sending packets towards broadcast source 

1st hop: $I$ sends packets to $F,H,J$ and $N$. 
- packets arrive on same link used to send to $I$

2nd hop: 8 packets are generated, two by each router. 
- 5 arrive on preferred link 