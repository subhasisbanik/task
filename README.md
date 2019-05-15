Requirements:
1. Please create a method to prevent anyone other than the purchaser from redeeming the commercial paper. 

2. Submit any corrections needed to make paperNet work practically in multiple organizations. Also, set the functional requirements and non-functional requirements, etc. that are the premise of the correction. 

3. In order to use Kafka / zookeeper in the Orderer, please tell us specifically what modifications are required. 

4. In order to use Raft in the Orderer, please tell us specifically what modifications are required. 

Solution(in correspondence to requirements):
1. A method has been created in papercontract.js and associatively put in the flow

2. For functional testing we would need to set up a popular testing framewoek supported by Node.js like Mocha/Chai and carry out unit testing.
 For Non functional requirements we would need to check for memory leaks in the application (if any) and also run a perfomance benchmark using popular benchmarking software.

3. We need to change parameters in file : hyperledger/fabric-samples/config/orderer.yaml
Here we need to modify parameters in the section Kafka.
The Kafka cluster needs to have atleast 4 nodes so as to resist fault. In case of zookeeper it needs to be in the term of odd numbers like 3,5,7 so as to resist network memory split due to failure. However, more than 7 zookeper nodes is considered bad design as it clutters the network.

4. We need to change parameters in file : hyperledger/fabric-samples/config/orderer.yaml
Here we need to update parameters primarily in Cluster and Consensus so as to accomodate the Raft configuration with TLS.
