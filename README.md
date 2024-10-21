# CS50 Python: Martingale in Roulette
#### Video Demo:  <a href="https://www.youtube.com/watch?v=8lFj8Z1G3z8" target="_blank">Video Final Project CS50</a>
#### Description:
My projects simulates playing Roulette with the Martingale system. 
It consists of the functions:
<ol>
<li>`main()`</li>
<li>`roulette(i, b, m)  # i = init, b = bet, m = money`</li>
<li>`doubling(b, m, i)`</li>
<li>`number()`</li>
<li>`even(z)`</li>
<li>`proba(d, i)`</li>
</ol>
which now will be explained:

- The `main-function` asks the user to enter his bet entry which he is to double every round he loses and the total amount of `money` he has - in this README 
we assume `bet = 5`, `money = 3000`$. Furthermore we need an initial bet-value `init` to set back to each time he wins. These values are passed as parameters
for `doubling(b, m, i)` to calculate the number of doubling his amount allows. 

- `proba(d, i)` takes the return values of `doubling` which consist of a tuple, i.e. `d[0]` = number of doubling and `d[1]` = user's loss 
and calculates the ordinal number of rounds expected to result in a loss - e.g., see above, `bet = 5`, `money = 3000` allows for 9*  doubling with a loss of 2555$. 
So he loses (19/37) ** 9 = 0.00248 which makes for about every 400 rounds.
The EV is -1.36$ per round. 

- The interesting thing is now function `roulette` which takes `bet`, `money` and `init`, remember, his first `bet = 5`, and returns the number of rounds
he can play via `while`-loop - `while money > bet` - as long as this is the case he can double - and returns the number of rounds, 
the number the croupier rolled (via `randint(0, 36)`) his `bet` and `money`. We run this 50 times in a for-loop to see how many rounds it takes him to lose. We detect a 
significant high amount of outliers - expected 403, detected 13 and so on - so we investigate this further by opening an empty list and adding an `if-clause` to our for-loop where we fill our list with every number of rounds < 100 - cf. the return tuple od `doubling`, number of rounds is `r[0]` from our return tuple of `roulette(i, b, m)`. Now we run the code and watch the length of our list that contains all significant deviations of our expected probabilities we got from `proba`-function.

- We are now able to conclude that Martingale is definitely not a promising system and this project's aim is to not only providing us with the mathematics but also empiricism.
