sorted-stream-merger
====================

The sorted stream merger merges various sorted streams into one. 


Description:

1) online:  The merger processes the input from various stream piece-by-piece, more elements can be given from the input stream during the run time.

2) thread-safe: The merger is thread-safe, the interface of this merger follows re-actor mode, the input and output are handled with event in queue. There events in queue are then processed in a separate(could be given by user) workloop. The result will sent asynchronously.


3) sorted: All elements from all input stream must be able to be sorted according to one sort criterion. And the elements from one input stream must remain sorted. The new element must be strictly in order with other available elements from the same stream.


the order is measured in continuous range, it means the merger cannot decide whether there would be a new element before two different indices. So the last known element of every stream must be remained in the merging queue until 
     a) there is a new (sorted) element in the same stream;
     b) all streams have reached the index of this element. 


4) extensible: 
     3.1) A new stream can be adopted easily;
     3.2) Sort criterion can be defined by user;
     3.3) Workloop can be given by user;
     
