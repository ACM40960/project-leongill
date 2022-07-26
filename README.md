<p align="left"><img width=50% src="https://github.com/ACM40960/project-leongill/blob/main/README.GIF"></p>


# Installing the Package
To install the package, first download R 4.2.0 at the following address and follow the prompts to complete the installation:
```text
https://cran.r-project.org/src/base/R-4/
```
Next, download the R-Studio IDE and follow the promts to complete the installation:

```text
https://www.rstudio.com/products/rstudio/download/#download
```

You now have a fully functioning R IDE. 

## Preparing your laptop





Next, intall the relevent packages by pasting the following lines of text into the R console and hitting `enter`:
```R
install.packages("hash")
install.packages("operators")
install.packages("devtools")
```

The first two packages are used in the functions of my package while the latter package is used to download the package from github. Download my package directly from GitHub by pasting the following lines into your console:
```R
library(devtools)
install_github("ACM40960/project-leongill/PACKAGENAMEHERE")
```

With the package installed, you can now download the Blackjack.RMD file from the project GitHub page which acts as a complete exhibit of the packages functionality. The first cell loads in the packages which you previously installed making their functions usable to you. 

The first function of interest is strategy. This function takes as argument `number_of_decks`, `number_of_simulations`, `include_double_down ` and `include_surrender`. `number_of_decks` is the number of decks in the game for which you want to obtain a strategy. `number_of_simulations` is the number of Monte Carlo simulations used on each position to approximate the win rate for sticking on that position. The reamining arguments are whether to include a particular rule in the analysis of the data where the default is that surrender and double down are not permitted. For example, 2 deck blackjack with $10^3$ simulations per position with doubling down allowed and surrendering prohibited is obtained by:

```R
strat = strategy(number_of_decks = 1, number_of_simulations = 10^3, include_double_down  = T)
```

The output is a hashmap where each key is a position, a combination of player hand a dealer visible card. The associated value is the move which maximizes player return given the inputted rule set. Values of 0,1,2,3 and 4 correspond to stick, hit, double down, surrender, split respectively.

The second main function is `play_games()` which simulates games using an chosen startegy. `number_of_decks` is again the number of decks in the game in which you want to employ the strategy. `count` is the number of simulated games used to evaluate the strategy. The strategy is then inputted in two parts. `index` is a list of all possible positions. `optimal` is a list of the associated moves. From the output of `strategy`, the `index` list is obtained by the `names()` function while the `optimal` list is obtained by the `values()` function.

```R
return_per_game = play_games(count = 10^6,  index = names(strat), optimal = values(strat))
```

The output of `play_games()` is the return per game achieved over the `count` games. 

