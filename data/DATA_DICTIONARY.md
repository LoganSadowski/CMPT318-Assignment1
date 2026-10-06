# Data dictionary — synthetic teaching data

All data are constructed instructional inputs, not empirical results or measured product performance. Do not change the CSVs for the required tasks. All financial amounts are CAD; probabilities are stored as proportions between 0 and 1.

## strategy_parameters.csv (3 rows)
`strategy`: current, prevention, recovery. `p_incident`: probability of one material incident in one year. `response_min`, `response_mode`, `response_max`: triangular response-cost parameters (CAD). `outage_p50`, `outage_p90`: population duration percentiles (days). `annual_control_cost`: incremental annual control cost (CAD), paid even without an incident. Current existing-control costs are treated as a common sunk baseline, so the current incremental cost is zero.

## calibration_records.csv (10 rows)
`exercise`: exercise identifier. `observed_hours`: observed synthetic restoration duration (hours). `E1_lower`, `E1_upper`, `E2_lower`, `E2_upper`: each estimator's previously stated 90% interval bounds in hours. Count the endpoints as included. These practice records are not a sample for estimating the ransomware duration distribution in days.

## case_settings.csv (one row)
`annual_budget_cad`: maximum annual control cost. `incident_loss_threshold_cad`: loss amount used for strict exceedance. `annual_exceedance_limit`: allowed annual probability above that amount. `downtime_cost_cad_per_day`: cost per outage day. `secondary_cost_cad`: incremental data-exposure response cost. `secondary_probability`: its marginal probability conditional on an incident. `stress_long_outage_probability`: probability above the given population 90th percentile (0.10). `stress_secondary_probability_high`: assumed conditional secondary-response probability for such long outages in the stress model (0.80).

The notebook simulates possible outcomes from these input assumptions. It does not generate or overwrite input CSV files. Graders use this same unmodified data folder when executing the student's single submitted notebook.
