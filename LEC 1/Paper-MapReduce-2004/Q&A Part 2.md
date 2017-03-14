*write down questions and answers we have before reading lecture material. Basically point out the interesting topics we want to discuss, and the elegant design we noticed.*

@fmars


Basic questions need to consider in a **Distributed Computation System**
- **Fault tolerance**
   1. A single host's failure is unlike, e.g. master node
   2. A worker host faiulre is inevitable
   3. Checkpoint is way to recover from failure 
- **Straggler**: the execution of entire system depends on the last completed one
   1. Redundant execution
- **Load balance**
   1. Partition function
   2. Pre scan
- **Locality optimization**
   1. Network bandwith is a sparce resource
   2. We need to take advantage of locality to reduce network usage
- **Monitoring and debugging tools**
   1. A system needs to provide monitoring functionalities to allow debugging
   2. A system needs to export major counter to understand system performance

Things learnt
- The right choice depends on the environment
- Restricting the programming model makes it easy to parallelize and distribute computations and to make fault tolerance

Questions
- How can a reducer start its job before all mapper tasks finished?
