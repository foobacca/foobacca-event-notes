Measuring the Price of Anarchy
==============================

- Izabela Komenda

In Critical Care Unit Interactions

- Two hospitals
- number of admissions dependent on current bed occupancy
- delayed discharges if no pressure on CCU beds

so used game theory - prisoner's dilemma example

- queueing game between 2 hospitals
- each hospital aims to get utliisation rate below 80%
- show equations, and diagram of Markov model
- there is an option to divert a patient from your hospital to the other hospital, but not risk free

results

- look similar to prisoner's dilemma: if both hospitals act in their own interests, patient throughput is reduced significantly
- "price of anarchy" is ratio of optimal throughput, vs self interest
- play with price changes when target and demand inputs are varied
- try out different models, with demand management, different rules about rejections

complexity was going through the roof, rewrote with python and parallelised it, and took 1 week on supercomputer (rather than 4 months!)
