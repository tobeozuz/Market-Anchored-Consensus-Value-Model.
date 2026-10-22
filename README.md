# Market-Anchored-Consensus-Value-Model.
A pre-match betting model for football and basketball. It estimates each market’s chance from several independent signals, anchors that estimate to Pinnacle’s margin-free price, and recommends a bet only when the chance times the odds clears a set value margin.
The Market-Anchored Consensus Value Model scans every pre-match football and basketball game Pinnacle prices, once or twice a day. It covers 1X2, every Over/Under and Asian handicap line, and Double Chance. From Pinnacle’s specials it also covers GG/NG, 2nd-half Double Chance and NBA player props when Pinnacle offers them.

For each market it combines four signals:

Observed hit rates: both teams’ recent results and head-to-heads, from Sportradar’s stats feed, read cautiously because 10–20 games is a small sample.
A goals or points model: Poisson for football, a points model for basketball.
Pinnacle’s own price, with the bookmaker’s margin removed.
An AI review.

A market is only considered when the real results support it and at least two of the other three signals agree.

The combined chance is then capped close to Pinnacle’s fair chance. Pinnacle is a very accurate bookmaker, so a large disagreement with its price is more often a sampling error than a real edge. A bet is recommended only when the capped chance times the odds is at least 1 plus the set margin (MIN_EDGE). Each game gets at most one pick, from the market the data supports most strongly. Every leg is re-priced at Pinnacle’s current odds before a ticket is issued.

An optional statistical layer is included for checking the approach on past data:

a Dixon-Coles ridge-Poisson model for football, with recent games weighted more,
ridge pace and efficiency ratings for basketball,
Shin margin removal and fractional Kelly staking,
walk-forward backtesting with no lookahead.

What it is not
It doesn’t predict results with certainty or guarantee profit. Its value estimates are upper bounds. In simulation, real value appeared mainly when Pinnacle’s own price was wrong, and the claimed value overstated it. Whether it has a real edge has to be measured over time: how often its prices beat Pinnacle’s price at kick-off, and how its results compare with its predictions, market by market.
