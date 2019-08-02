# roulette-game
Overview: The goal of this project is to create a fair way to explore content. Normalizing and equalizing the randomness to be freely random, rather than recommenders that focus primarily on clicks, popularity and profiles.

## Randomization
Approaches:
- Normalization: We need the random numbers to be capped and return values that fit the total number or objects we have stored to potentially call.
- Categories: We may want to toggle certain categories on / off, or rather specify a command to filter only some of the objects.
- We want to ensure a system that is equally random. Meaning that the randomness doesn't have a bias in the returned result(s)
- To that end we would like a natural random method for rolling numbers.
- Further, to still be equal in that respect we would like to ensure that the returned result hasn't come up again until all the other results have appeared once.
- To achieve this, I'm thinking a context flag and switch function could check to see if this result has been seen. If it has then we should increment by 1 until we return an object which hasn't been seen. 
- However, again, to achieve randomness, we should have another flag to check to see if we have incremented or decremented last time, so that we alternate to sometimes decrement instead.

BONUS:
- In the event that a unique value is simply missed (user error, rolled by another user, latency) we don't want them to have to wait for 9,999 rolls to occur before that 10,000th result appears.
- To achieve this, we will have another flag to consider what series are being actively claimed. So if objects share a similar author for instance, then we will ignore the increment/decrement switch to skip over that random roll in the future.
- Perhaps another way around this to aid authors who may have only 1 or 2 entries and not benefit from that series bonus, we will set the case to ignore results not to be truly equally, but rather a.) a maximum # of times it is allowed to appear or b.) allow it to appear 3, 10 or n times before ignoring that object until other values must be rolled again.
- Limit rolls to only 12 or 24 per hour. After rolling more, you can listen as a radio-playlist, but not claim objects as your own.

## Claims
- After implementing randomness, we want to have the logic for what to do with that object that is returned. In our case, that is to allow a time period after the item is returned where we can claim the object and add it to our collection.
- The first person to react to the item (click the button) is able to claim it as "theirs". Others then, would be able to like the item and increase its rating. 
- Likes and Equally Random: As something becomes more popular, we would like to have a way to randomly roll popular and unpopular (unrated) items from the set of objects available.


BONUS:
- Claims should be limited, to only one per 2 hours. 
- If you own the item in your collection, you can call that individual item and experience the full content any time (perhaps as your own personal playlist of owned objects as well?).
- Patrons and purchasing. Adding support to purchase the content or support an artist and gain access to the items as if they were in your collection. Will be limited only to participating artists.
- Each time the item appears as a roll, whoever is the first person to claim is able to add it to their collection as well.
- Playlist mode: stream content without the ability to rate it, by popularity.
- Filter playlist by magnitudes of popularity (rating 0-10 likes, 10-100, 100-1000, etc)

## Exploration
- Allow for the creation of tags by object owners. 
- Once those items were available on multiple servers / games, we could allow for a rule that once 10 people tag the same thing, the tag is globally visible on the object when rolled.
- Adding tags to an individual profile, to focus the roulette on objects that seem similar to the individual preference.


### Sources for starting points
True RNG
- https://gist.github.com/joepie91/7105003c3b26e65efcea63f3db82dfba
- https://www.npmjs.com/package/true-random
