# NYC Restaurant Inspections

Team project analyzing NYC restaurant inspection results.

## Already have the dataset?

If you already downloaded the original dataset from our Google Drive, you only need the code from GitHub. You do not need to download the dataset again.

If you need the original dataset, go to Releases, download the attached .csv.zip file, and unzip it. You can also download it from [our Google Drive folder](https://drive.google.com/drive/folders/1OcqYpFfLVvVa2dJ3urjD3iT8cfazQj8n?usp=sharing) (only people in our group can open it).

## Prepared dataset (use this one for the analysis)

After data preparation and structural cleaning (Tasks 1 to 11) we have a prepared dataset: 295,843 rows and 32 columns.

1. Go to Releases and open **Cleaned restaurant inspection dataset (structural cleaning)** (tag `prepared-data-v1`).
2. Download `restaurants_prepared.csv.zip` and unzip it.
3. Put `restaurants_prepared.csv` in the `data` folder, next to `restaurant_inspections.csv`.
4. Load it with the code in the last cell of `01_data_exploration.ipynb`. Do not use a plain `pd.read_csv`, because it loses the leading zeros of the identifier columns and turns the dates into text. Do not open and save the CSV in Excel, because Excel can also remove the leading zeros.

The `handoff` folder explains what changed:
- `flag_explanations.csv`: what each new column means and how many rows it marks.
- `column_mapping.csv`: the original and prepared columns and their types.
- `before_after_counts.csv`: the raw data compared with the prepared data.
- `duplicate_exclusion_log.csv`: the 169 duplicate rows that were removed.

## How to get the code

1. Go to the Code tab of this repository.
2. Click the green Code button.
3. Choose Download ZIP.
4. Unzip the downloaded project folder.
5. Open the folder in VS Code or Jupyter.

Code files will be added as the project progresses.

## Set up your dataset

1. Inside the project folder, create a folder called data.
2. Copy your original CSV into that folder.
3. Rename the copy to restaurant_inspections.csv.
4. Keep the original dataset unchanged.
5. Add the prepared dataset (see "Prepared dataset" above) to the same folder.

Example folder structure:

    nyc-restaurant-inspections/
        01_data_exploration.ipynb
        data/
            restaurant_inspections.csv
            restaurants_prepared.csv
        handoff/

## Run the code

Open the project folder in VS Code or Jupyter.

Our code should use these shared dataset paths:

    import pandas as pd
    df = pd.read_csv("data/restaurant_inspections.csv")   # original dataset

For the prepared dataset, use the load code in the last cell of `01_data_exploration.ipynb`.

Run notebooks from top to bottom using a Python kernel. Install any packages required by the code.

## Working together

- Use the same original dataset so our results are consistent.
- Save cleaned data separately from the original.
- Let the group know which file you are editing.
- Download the latest code before starting. ZIP downloads do not update automatically.
- For regular collaboration through VS Code, clone the repository, pull the latest changes, then commit and push your updates.
