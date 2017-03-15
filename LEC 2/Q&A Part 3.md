by mumu


I still have a lot questions about Go, maybe it is my own problem
——it is not easy for me to learn a new programming language. 
The part of Concurrency is too difficult. It's kind of difficult for 
me to understand goroutines and channels. Also the part of Methods
and interfaces.

Q: I don't know how to modify the Crawl function to fetch URLs in 
parallel. 

A: I start Lec2 and read crawler.go (Concurrent crawler with Mutex 
and WaitGroup part). They use sync.WaitGroup. It has three methods: 
Add()，Done() and Wait(). The main goroutine calls Add to set the 
number of goroutines to wait for. Then each of the goroutines runs 
and calls Done when finished.
The answer is：

	var done sync.WaitGroup
	for _, u := range urls {
		done.Add(1)
		go func(u string) {
			defer done.Done()
			Crawl(u, fetcher, c)
		}(u) // Without the u argument there is a race
	}
	done.Wait()

Q: Why use channels？(I just know communication)

A: Two goals: communication and synchronization.
Unbuffered channels combine communication—the exchange of a value—with 
synchronization—guaranteeing that two calculations (goroutines) are in
a known state.
Receivers always block until there is data to receive. If the channel 
is unbuffered, the sender blocks until the receiver has received the 
value. 

Q: What is the different between defer done.Done() and done.Done() at 
the end of this goroutine?

A: defer done.Done() is finished at any return in this goroutine.
If returned before done.Done() at the end, done will not -1.
