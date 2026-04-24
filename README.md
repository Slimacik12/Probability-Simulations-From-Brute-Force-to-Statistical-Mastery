# Probability Simulations: From Brute Force to Statistical Mastery

This project explores the intersection of theoretical probability, computational simulations, and risk analysis. It moves beyond simple averages to investigate the full distribution of random events.

---

## 1. Dice Probability

Calculating the sum of multiple dice can be done via **Brute Force**, but this method fails as the number of dice increases. Instead, we use **Discrete Convolution** to calculate exact probabilities with extreme efficiency.

### The Analytical Approach vs. Efficiency
While a nested loop (Brute Force) has an exponential time complexity $O(s^n)$, Convolution allows us to determine the distribution in near-linear time. This is especially powerful when dealing with **weighted (unfair) dice**.

## 2. The Coupon Collector Problem

The **Coupon Collector Problem** is a classic paradox that highlights the difference between "intuition" and "statistical reality." It asks: *How many trials are needed to collect all n unique items?*

### The Harmonic Progression
Each time you collect a new face, the probability of finding the next unique face decreases. This creates a series of waiting times:
* Waiting for the 1st face: $P = 6/6, E = 1$ roll.
* Waiting for the 2nd face: $P = 5/6, E = 1.2$ rolls.
* ...
* Waiting for the 6th face: $P = 1/6, E = 6$ rolls.

The sum of these expectations forms a **Harmonic Series**:

$$E[T] = n \cdot H_n = n \sum_{i=1}^{n} \frac{1}{i}$$

### 2.1 Distribution Asymmetry (Positive Skewness)
The simulation confirms that the required number of rolls is not Normally distributed. Instead, it exhibits a significant **positive skew**.

* **Mode vs. Mean:** The most frequent outcome (Mode) is lower than the Mean. The Mean ($\approx 14.7$ for 6 sides) is pulled upward by infrequent, extreme tail events.
* **Asymptotic Behavior:** This distribution is a sum of independent geometric random variables. As $n$ increases, the distribution asymptotically approaches a **Gumbel distribution**, characterized by its heavy right tail.

### 2.2 Quantifying Tail Risk
In risk management, the average outcome is often secondary to **Tail Risk**—the probability of extreme deviations from the mean.
* **Empirical Expectation:** $E[X] \approx 14.7$ rolls.
* **Tail Probability:** As shown in the simulation results, $P(X > 25) \approx 6.18\%$. These **Tail Events** represent the risk of "statistical bad luck" that point estimates fail to capture.


## 3. Dice Games & Game Theory

The **Expected Value** is the long-term average outcome of a random variable. In the context of a dice game, it represents the average amount a player wins or loses per game.

### The Mathematical Formula
For a discrete random variable $X$ (the payout), the Expected Value $E[X]$ is calculated as:

$$E[X] = \sum_{i=1}^{n} P(x_i) \cdot x_i$$

Where:
* $P(x_i)$ is the probability of a specific sum occurring.
* $x_i$ is the payout associated with that sum.

### Practical Application
By using convolution to map all possible outcomes and their exact probabilities, we can rigorously model the profitability of any game. For a game where you win **$5** on a sum of 7 or 11 and lose **$1** otherwise, the calculated Expected Value is **$0.33**, indicating a long-term advantage for the player.
