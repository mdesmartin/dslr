## DSLR – Data Science × Logistic Regression

This project focuses on building a **logistic regression classifier** to predict Hogwarts Houses from student data. Implemented as a **team project**, it demonstrates proficiency in **data analysis, visualization, preprocessing, feature selection, and machine learning workflows**, while highlighting collaboration, code design, and problem-solving skills.

---

### Installation

To set up the project and install all dependencies, run:

```zsh
$ make install
```

You should see:

```
Dependencies installed successfully!
To activate the virtual environment, run:
source config/.venv_dslr/bin/activate
```

Activate the environment:

```zsh
$ source config/.venv_dslr/bin/activate
```

```
(.venv_dslr) $
```

---

### Running the Programs

All programs are located in the `src/` folder. You can run them with Python 3:

```zsh
python3 src/describe.py
```

For detailed usage information:

```zsh
python3 src/describe.py --help
```

---

### Programs Overview

#### Data Analysis

- **`describe.py` [file] [--advanced]**  
  - **Arguments:**
    - `file` (optional): Path to the CSV file (default: `datasets/dataset_train.csv`)  
  - **Options:**
    - `-h`, `--help`: Show help message  
    - `-a`, `--advanced`: Include advanced statistics (missing values, unique counts, IQR)  
  - **Purpose:** Generate a comprehensive statistical summary of numerical features in the dataset.

#### Data Visualization

- **`histogram.py` [file]**  
  - **Purpose:** Creates histograms for each numerical feature grouped by Hogwarts House, showing grade distributions.

- **`scatter_plot.py` [file]**  
  - **Purpose:** Creates scatter plots to visualize correlations between selected features (e.g., Defense Against the Dark Arts vs Astronomy).

- **`pair_plot.py` [file]**  
  - **Purpose:** Generates a pair plot matrix to visualize relationships between features, with points colored by House.

#### Machine Learning

- **`logreg_train.py` [file]**  
  - **Purpose:** Trains a one-versus-all logistic regression model to classify students into Hogwarts Houses.  
  - **Features used:** Potions, Charms, Transfiguration, Astronomy, Divination, Ancient Runes, Muggle Studies  
  - **Output:** Saves trained model weights to `weights.txt`.

- **`logreg_predict.py` [file]**  
  - **Purpose:** Uses the trained model to predict House assignments for new students.  
  - **Output:** Saves predictions to `houses.csv` and prints results in the terminal.

---

### Example Usage

```zsh
# Explore dataset statistics
python3 src/describe.py datasets/dataset_train.csv

# Visualize grade distributions
python3 src/histogram.py datasets/dataset_train.csv

# Explore feature correlations
python3 src/scatter_plot.py datasets/dataset_train.csv

# Generate pair plots for multiple features
python3 src/pair_plot.py datasets/dataset_train.csv

# Train logistic regression model
python3 src/logreg_train.py datasets/dataset_train.csv

# Predict Hogwarts Houses for test dataset
python3 src/logreg_predict.py datasets/dataset_test.csv
```

---

### Model Details

The logistic regression model uses **one-versus-all classification**:

- 4 binary classifiers (one per House)  
- Each classifier predicts if a student belongs to that House or not  
- Features standardized using z-score normalization  
- Sigmoid activation function with binary cross-entropy loss  
- Gradient descent optimization with up to 10,000 iterations and early stopping

---

### Output Files

- **`weights.txt`**: Contains trained model weights for each House  
- **`houses.csv`**: Predictions for the test dataset in the required format
