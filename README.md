## Interactive Dashboard

[Explore the NBA Offensive Gravity Dashboard on Tableau Public](https://public.tableau.com/app/profile/alexandre.tounkara3088/viz/NBA_Gravity_V6_Publishing_FINALE/Dashboard1)

Explore 252 player rankings and the relationship between 3-point
attempts per 36 minutes and Offensive Gravity Score.
Search for a player to highlight them across both charts.



# NBA Offensive Gravity

## Why I Built This

The idea behind this project came from a question I kept thinking about while watching basketball: **how can you measure the effect a player has on a defense even when they don't have the ball?**

Players like Steph Curry can change the way a defense plays just by being on the floor. Defenders stay attached to them farther from the basket, help defense changes, and that can create opportunities for teammates. That idea is usually described as offensive "gravity."

The problem is that gravity isn't something that shows up directly in a normal box score.

For this project, I wanted to see if I could use publicly available NBA statistics to build my own estimate of offensive gravity.

The result is a model that gives qualified NBA players from the 2024-25 season an **Offensive Gravity Score from 0-100**.

## How It Works

I started with traditional and advanced player statistics from the 2024-25 NBA season and focused on different ways a player can put pressure on a defense.

I grouped the statistics into four main areas:

- **Perimeter scoring** - shooting and scoring pressure from outside
- **Playmaking** - creating opportunities for teammates
- **Interior pressure** - attacking and scoring closer to the basket
- **Overall offensive impact** - advanced statistics that help capture a player's broader offensive contribution

Because these statistics are measured on very different scales, I standardized the features before combining them.

I then weighted the different components and converted the final result into a 0-100 scale to make the rankings easier to interpret.

## Making Sure the Model Wasn't Just Producing Random Rankings

One of the biggest things I wanted to know was how much my own choices were affecting the results.

The initial weights are ultimately assumptions I made when designing the model, so I didn't want to treat them as automatically correct.

I tested different weighting combinations and compared how much the player rankings changed using **Spearman rank correlation**.

I also used **PCA (Principal Component Analysis)** as another way of combining the underlying information without relying entirely on my original weights.

Finally, I compared the results with established NBA metrics such as **VORP and BPM** to see how my model related to existing measures of player impact.

## Tools I Used

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Jupyter Notebook
- Tableau

## What's in This Repository

The Jupyter notebook contains the full process from cleaning and combining the datasets through feature engineering, building the gravity score, testing the model, and analyzing the final rankings.

I've also included the two 2024-25 NBA datasets used by the notebook so the analysis can be reproduced.

## What This Model Can't Measure

One thing I learned while working on this project is that **box-score data can only take this idea so far**.

Actual offensive gravity involves things like defender positioning, how closely someone is guarded, off-ball movement, defensive rotations, and how defenses react to individual players in real time.

Those things aren't directly captured by the data I'm using.

So I don't consider this score a literal measurement of offensive gravity. It's better thought of as a **statistical proxy** built from characteristics that I think contribute to a player's ability to pressure a defense.

With access to player-tracking or spatial data, I'd like to eventually compare this model against actual defensive positioning and see where it holds up and where it doesn't.

## What's Next

There are a few directions I'd like to take the project next:

- Add player-tracking or spatial data if I can find an accessible source
- Test the model across multiple NBA seasons
- Continue experimenting with how the components are weighted
- Account more directly for differences in player roles and positions
- Expand the Tableau side of the project so the results are easier to explore
