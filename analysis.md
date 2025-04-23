# Patient Cohort Analysis Report

## Analysis Approach
We used Polars for high-performance data processing. The input CSV file was converted to a Parquet file to take advantage of efficient I/O. A lazy evaluation pipeline was built using `scan_parquet()` and `.pipe()` to allow for readable and modular transformations. We filtered out BMI values outside the normal physiological range (<10 or >60) and categorized patients into BMI ranges.

## Use of Polars for Efficiency
- **Lazy Evaluation:** Enabled by `scan_parquet()`, this delays execution until necessary.
- **Streaming Execution:** `.collect(streaming=True)` processes large datasets without loading them entirely into memory.
- **Parquet Conversion:** Speeds up disk I/O and is more efficient than CSV, especially for repeated runs.

## Patterns and Insights
- Patients categorized as **Obese** had the highest average glucose levels.
- The **Normal** BMI group had the largest number of patients.
- Age distribution varied slightly across BMI ranges, with higher BMI ranges tending to have slightly older patients on average.

This approach ensured scalable, fast processing of patient data with clear cohort-based insights.
