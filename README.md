# Detection of Structural Breaks in Variance Using the ICSS Algorithm

This project implements the Iterated Cumulative Sums of Squares (ICSS) algorithm
of Inclán & Tiao (1994) from scratch in SAS/IML and applies it to the monthly
USD/RUB exchange rate over the period 1995–2026.

## Objective

To detect multiple structural breaks in the unconditional variance of a financial
time series using the ICSS algorithm, and to interpret the identified variance
regimes in light of macroeconomic and geopolitical events.

## Methodology

**Algorithm:** ICSS (Inclán & Tiao, 1994)
- Centered cumulative sum of squares statistic (Dk)
- Two-phase iterative procedure: candidate search (Phase A) + refinement (Phase B)
- Critical value: 1.358 at the 5% level (Brownian bridge asymptotic distribution)

**Pre-processing:**
- Log-returns computation
- ADF stationarity test
- ARMA(1,1) pre-filtering to address autocorrelation before applying ICSS

**Main SAS procedures:**
- `PROC IML` — algorithm implementation and simulation
- `PROC ARIMA` — pre-filtering
- `PROC SGPLOT` — diagnostic visualizations

## Data

- **Simulated data:** T = 600 observations with three known variance regimes
  (σ² = 1, 3, 1) and true breaks at t = 200 and t = 400, used to validate the
  implementation
- **Real data:** Monthly USD/RUB exchange rates from Investing.com,
  January 1995 – March 2026 (377 observations)

## Results

Four structural breaks detected at observations 8, 51, 257, and 333, corresponding
to January 1995, January 1999, January 2016, and January 2022 — each aligned with
a major geopolitical or macroeconomic shock in Russian financial history (post-Soviet
transition, 1998 sovereign default, Crimea annexation/oil shock, Ukraine invasion).

## Repository Content
ICSS.pdf                        Full report (theory, methodology, results)
Code_1_2_ICSS.sas               ICSS validation on simulated data
ROUBLE_RUSSE_ICSS.sas           Empirical application on USD/RUB exchange rate
USD_RUB_Historical_Data.csv     Raw monthly USD/RUB data (Investing.com)

## Notes

- Some scripts include local file paths; update them to match your environment.
- The full theoretical background, algorithm pseudo-code, and detailed results
  are available in `ICSS.pdf`.
- The empirical code reuses the same algorithmic structure as the simulation
  code, with the addition of the ARMA(1,1) pre-filtering step.


## References

- Inclán, C. & Tiao, G.C. (1994). *Use of cumulative sums of squares for
  retrospective detection of changes of variance.* JASA.
- Lamoureux, C.G. & Lastrapes, W.D. (1990). *Persistence in variance,
  structural change, and the GARCH model.* JBES.
- Sansó, A., Aragó, V. & Carrion-i-Silvestre, J.L. (2004). *Testing for
  changes in the unconditional variance of financial time series.*
