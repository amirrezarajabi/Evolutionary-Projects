# Snail jumper

It uses ANN and genetic algorithm in a snail jumper game. It starts with 300 players and they converge and learn to do better in the next generations.

![Snail Jumber](SnailJumper.png)

## **Evolutionary Process**
There are 3 steps to go from one generation to another generation:

### **Selecting Parents**
I implement this on `next_population_selection` function and we have 5 options for selecting parenets
*   **Q-tournament**: In tournament selection a certain number Q of individuals are drawn at random
from the current population. These individuals carry out a tournament, which is
won by the individual with the highest fitness

*   **top-k**: best-known selection

*   **roulette-wheel**:is certainly among the best-known selection methods. It
takes the (absolute) fitness of each individual and computes their relative fitness. This value is then interpreted as the probability with which the corresponding individual may be selected

*   **roulette-wheel-mapped**: It is a variant of roulette-wheel selection by mapping probabilty.

*   **stochastic universal sampling(SUS)**: It can be seen as a variant of roulette-wheel selection. It uses a roulette wheel with as many markers as there are
individuals in the population. These markers are located at equal distances around
the roulette wheel. Instead of turning the roulette wheel once for each individual to
be selected (as in standard roulette-wheel selection), the roulette wheel is turned only once and each marker gives rise to one selected individual

### **Generating new population**
I implement this on `generate_new_population` function. In this step we have to create children from selected parents. Making children from parents has 2 steps:
*   **crossover**: In this step, we creating children from two parents and there are 2 methods:
    *   **cal-crossover**: In this method we use weighted averaging between 2 parents NN weights
    *   **two-points**: In this method we split each NN weithts to 3 parts and swap middle part for each parent and making children.
*   **mutate**: after creating children in crossover we have to mutate them and for mutatuin I add gaussian noise to children.
### Choosing between parents and children for next generation
I used `next_population_selection` same as first step.

## Run
        python3 game.py