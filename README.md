# roulette-game

## Randomization
Approaches:
- We want to ensure a system that is equally random. Meaning that the randomness doesn't have a bias in the returned result(s)
- To that end we would like a natural random method for rolling numbers.
- Further, to still be equal in that respect we would like to ensure that the returned result hasn't come up again until all the other results have appeared once.
- To achieve this, I'm thinking a context flag and switch function could check to see if this result has been seen. If it has then we should increment by 1 until we return an object which hasn't been seen. 
- However, again, to achieve randomness, we should have another flag to check to see if we have incremented or decremented last time, so that we alternate to sometimes decrement instead.

BONUS:
- In the event that a unique value is simply missed (user error, rolled by another user, latency) we don't want them to have to wait for 9,999 rolls to occur before that 10,000th result appears.
- To achieve this, we will have another flag to consider what series are being actively claimed. So if objects share a similar author for instance, then we will ignore the increment/decrement switch to skip over that random roll in the future.
- Perhaps another way around this to aid authors who may have only 1 or 2 entries and not benefit from that series bonus, we will set the case to ignore results not to be truly equally, but rather a.) a maximum # of times it is allowed to appear or b.) allow it to appear 3, 10 or n times before ignoring that object until other values must be rolled again.


## Claims
- After implementing randomness, we want to have the logic for what to do with that object that is returned.
