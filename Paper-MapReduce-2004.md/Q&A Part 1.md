Write down questions and answers we have before reading paper implementation. Basically try to come up with a idea what if we are about to build such a system
## @fmars
- [ ] how to store the output of mapper
      - in mapper host locally
      - in some intermediate distributed storage 
      - in corresponding reducer
- [ ] how to design the partition algorithm, or hash function the output of mapper to reduce to make it load balance. Can it dynamically shift load?
- [ ] can a reducer starts before the mapper finishing?
      - the nature of reducer, such as counter, doesn't require the whole knowledge of input data before starting computation

## @mumu
- [ ] your questions go here




