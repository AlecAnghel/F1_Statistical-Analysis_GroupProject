# Formula One Performance Analysis

A DATASCI 151 group project exploring historical Formula One race data with Python.

The project combines driver, lap-time, race, qualifying, and results tables to examine relationships between qualifying position, finishing position, driver age, and lap times. The focus is on data cleaning, joins, grouped analysis, and clear visual explanations.

## Start here

- [Final project notebook](Group7_FinalProject.ipynb): the combined analysis with code and saved outputs.
- [HTML report](Group7_FinalProject_HTMLformatted.html): download and open in a browser to read the formatted report without running Python.
- [Alec's notebook](alec_notebook.ipynb): the individual exploration of lap times, driver nationality, and age.

## Questions explored

- How is qualifying position related to final race position and points?
- How do average recorded lap times differ across driver nationality groups?
- How do average lap times vary with driver age in this dataset?

These are descriptive comparisons. They do not isolate driver ability or establish that age or nationality causes performance differences.

## Analysis workflow

1. Load the five main CSV tables from `f1_data`.
2. Handle missing driver values, parse dates, and convert lap times from milliseconds to seconds.
3. Join lap times to driver information using `driverId`, then add race dates using `raceId`.
4. Join qualifying and race results on both `raceId` and `driverId`.
5. Build summary tables, charts, and a correlation comparison.

The saved notebook shows 528,785 lap records and 9,395 matched qualifying/results records. It reports a qualifying-position versus finishing-position correlation of **0.57**, rounded to two decimals.

## Run locally

You will need Python 3, Git, and Jupyter Notebook. The CSV files used by the final notebook are included.

```bash
git clone https://github.com/AlecAnghel/F1_Statistical-Analysis_GroupProject.git
cd F1_Statistical-Analysis_GroupProject
python -m pip install pandas numpy matplotlib notebook
jupyter notebook Group7_FinalProject.ipynb
```

Run the cells from top to bottom with the repository root as the working directory. The final notebook uses relative `f1_data/...` paths. Some individual work notebooks use Windows-style paths and may need local adjustments.

Package versions are not pinned in this repository.

## Technical and design choices

- **Separate source tables:** Preserve the dataset's structure and make each join explicit.
- **Inner joins:** Keep observations with matching records in the tables being compared.
- **Readable units and labels:** Lap times are shown in seconds, and position columns are renamed to distinguish qualifying from race results.
- **Grouped summaries:** Make large tables easier to explore before plotting.
- **Simple charts:** Bar, line, and scatter plots keep the relationship being examined visible.
- **Notebook and HTML formats:** Support both running the analysis and reading the finished report.

## Assumptions and limitations

- The lap-time analysis keeps laps below 120 seconds. This is a broad filter, not a reliable way to identify every pit stop, safety-car lap, or interruption.
- The nationality summary includes groups with more than 10,000 retained laps. It does not control for circuit, weather, era, car, or team.
- The age analysis groups drivers into whole years and keeps ages 18 through 45. Different drivers and race conditions can affect the averages.
- Many laps come from the same drivers and races, so observations are not independent.
- The results should not be read as a ranking of nationalities or proof of a universal peak-performance age.
- Saved outputs are included, but there is no automated test suite or pinned environment.

## Team and contribution context

This is shared coursework by Alec Anghel, Stanley Yoo, Elsa Mathew-Lewis, and Kimberly Yang. The final notebook combines the group work. `alec_notebook.ipynb` contains Alec's lap-time, nationality, and age exploration; the repository also keeps individual notebooks from other team members.

## Data source

The repository's [source note](f1_data/1-source.txt) links to [Formula One Racing: A Comprehensive Data Analysis on Kaggle](https://www.kaggle.com/datasets/thedevastator/formula-one-racing-a-comprehensive-data-analysis/).

The notebook uses `drivers.csv`, `lap_times.csv`, `races.csv`, `qualifying.csv`, and `results.csv`. Additional F1 tables are also kept in `f1_data`.
