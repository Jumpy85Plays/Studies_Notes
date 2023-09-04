A sequence of steps that is:
- unambiguous
- executable
- terminating
Algorithm for deciding which car to buy, based on total costs:
  For each car, compute the total cost as follows:
	  annual fuel consumed = annual miles driven/fuel efficiency
	  annual fuel cost = price per gallon x annual fuel consumed
	  operating cost = 10 x annual fuel cost
	  total cost = purchase price + operating cost
 If total cost1 < total cost2
	  Choose car1
 Else
      Choose car2