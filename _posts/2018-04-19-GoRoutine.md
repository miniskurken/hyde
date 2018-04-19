---
layout: post
title: Goroutine here and goroutine there
---

I've been so into learning the real use of goroutines for this project, I've noticed that the cost of creating them is relative low! However if the time it costs to create a goroutine and the channel it will talk to exceeds the time it takes to make the calculations the goroutine will do. There is no purpose to use them! 

For instance i was playing around with them doing matrix calculations of a positions neighbors.

>EXAMPLE: 3x3 Matrix  
[{0 0} {0 1} {0 2}]  
[{1 0} {1 1} {1 2}]  
[{2 0} {2 1} {2 2}]  
Given this matrix i've tried to run the calculations of each position concurrent with the help of goroutines however that cost is time-costly than running all the calculations in a linear fashion.

>ANSWER:  
[  
[{0 0} {0 1} {1 0} {1 1}]  
[{0 0} {0 1} {0 2} {1 0} {1 1} {1 2}]  
[{0 1} {0 2} {1 1} {1 2}]  
[{0 0} {0 1} {1 0} {1 1} {2 0} {2 1}]  
[{0 0} {0 1} {0 2} {1 0} {1 1} {1 2} {2 0} {2 1} {2 2}]  
[{0 1} {0 2} {1 1} {1 2} {2 1} {2 2}]  
[{1 0} {1 1} {2 0} {2 1}]  
[{1 0} {1 1} {1 2} {2 0} {2 1} {2 2}]  
[{1 1} {1 2} {2 1} {2 2}]  
]  
So the next thing i'll try is to run a goroutine for each row of the matrix and calculate the entire rows neighbors instead hoping that would give us a more efficient calculation time. And also giving us a better performance during the calculations.

I just thought this was something interesting I really did not think of once i read about concurrency. More "threads" is not always the best way to go!