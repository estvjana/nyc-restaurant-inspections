# NYC Restaurant Inspections

Team project analyzing NYC restaurant inspection results.

## Already have the dataset?

If you already downloaded the original dataset from our Google Drive, you only need the code from GitHub. You do not need to download the dataset again.

If you need the dataset, go to Releases, download the attached .csv.zip file, and unzip it. Download the original dataset from [our Google Drive folde https://drive.google.com/drive/folders/1OcqYpFfLVvVa2dJ3urjD3iT8cfazQj8n?usp=sharing.

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

Example folder structure:

    nyc-restaurant-inspections/
        analysis.ipynb
        data/
            restaurant_inspections.csv

The notebook filename above is an example.

## Run the code

Open the project folder in VS Code or Jupyter.

Our code should use this shared dataset path:

    import pandas as pd
    df = pd.read_csv("data/restaurant_inspections.csv")

Run notebooks from top to bottom using a Python kernel. Install any packages required by the code.

## Working together

- Use the same original dataset so our results are consistent.
- Save cleaned data separately from the original.
- Let the group know which file you are editing.
- Download the latest code before starting. ZIP downloads do not update automatically.
- For regular collaboration through VS Code, clone the repository, pull the latest changes, then commit and push your updates.
