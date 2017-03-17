by mumu

1. Why use Go?.
  - Go allows you to concentrate on distributed systems problems
    - good support for concurrency
    - good support for RPC
    - garbage-collected (no use after freeing problems)
    - type safe
  - We like programming in Go
      - simple language to learn
      - a fashionable language when we redid the 6.824 labsType some Markdown on the left
      
2. Goroutines (thread)
  - Allow you to exploit concurrency
  - share memory, use pc, register, stack
  - more than cores
  - challenges: sharing data, coordination between threads, granularity of concurrency

3. Exercise  Done

4. RPC
  - easy-to-program network communication
  - failures: lost packet, broken network, slow server, crashed server
  - scheme: "at least once", "at most once" and "exactly once"
	- 1)"at least once" go wrong sometimes, except specific examples
	- 2)"at most once": server RPC code detects duplicate requests, and returns previous reply instead of re-running handler. (unique client ID)
    	- when is discard safe?——important question！
    	- crashes and re-starts?
	- 3)"exactly once" at-most-once plus unbounded retries plus fault-tolerant service
  - Go RPC is "at most once" open TCP connection
