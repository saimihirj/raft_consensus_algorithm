# A Fault-Tolerant Distributed Key-Value store using Raft Consensus Algorithm

## Authors

- [Kalash Gollapinni](https://github.com/thegreatlobu)
- [Gaurav Jayaraj](https://github.com/GauravJayaraj)
- [Sai Mihir J](https://github.com/saimihirj)

## What is Raft consensus algorithm?
In a distributed system, data replication is needed for either fault-tolerance or latency optimization. Maintaining a consensus among all replications is crucial for the correctness and robustness of the distributed system. Various algorithms emerge to address this problem. Raft is an alternative designed to Paxos, aiming to be more understandable and to offer the same level of safety and robustness.

![alt text](https://media.geeksforgeeks.org/wp-content/uploads/multiple-server-labelled-raft-visual.png)

![alt text](https://miro.medium.com/max/1400/1*vl_yaJo-adBVgqhQPvA4Aw.png){:height="36px" width="36px"}

## Leader Election
* The election starts when the current leader fails/disconnects or at the beginning of the algorithm. A new term starts in the system with a random period for the new leader to be elected. If the election successes with a single new leader winning, the term carries on and the new leader takes over to coordinate the normal operations. Otherwise, the term expires to yield another round of the election.
* An election is started with one or more node assumes candidacy, which is the result of not receiving any communication from the leader over a certain amount of timeout. Timeout is randomized to minimize the impact of the split vote. Each server vote once per term, on a first-come-first-served basis. Candidate votes for itself and request voting to other nodes. If a candidate receives a request from another candidate with a higher term, it will update its term and vote positively to that request, otherwise, if the request is from a lower or equal term candidate, the received request will be discarded. When the majority votes for a candidate, that candidate wins the election.

![alt text](https://media.geeksforgeeks.org/wp-content/uploads/raft-leader-election.png){:height="36px" width="36px"}

![alt text](https://miro.medium.com/max/1400/1*-YtqCevFwWqXc3dlUbxMww.png){:height="36px" width="36px"}
