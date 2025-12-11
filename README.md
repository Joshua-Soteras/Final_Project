# Sudoku Evolutionary Algorithm

**CS 5660 Artificial Intelligence - Final Project**
*December 10, 2025*

**Team Members:**
- Sanskar Thapa
- Joshua Soteras
- Erwin McNaughton
- Brian Pham
- Neel Khunt

## Project Overview

This project implements and benchmarks an **Evolutionary Algorithm (EA)** to solve Sudoku puzzles, comparing its performance against traditional backtracking methods. The system uses the DEAP (Distributed Evolutionary Algorithms in Python) framework to optimize Sudoku solutions by minimizing constraint violations.

### Key Features
- **Genetic Algorithm Solver** with custom operators optimized for Sudoku constraints
- **Hybrid Approach** combining GA with local search (hill climbing)
- **Parameter Tuning System** using Grid Search, Random Sampling, and Latin Hypercube Sampling
- **Backtracking Benchmark** for performance comparison
- **Comprehensive Visualization** of fitness convergence, parameter sensitivity, and success rates

---

## Software Requirements

### Required Software
- **Python**: Version 3.8 or higher
- **Jupyter Notebook**: For running the `.ipynb` file

### Required Python Libraries
```
numpy
pandas
matplotlib
seaborn
scipy
deap
```

### Installation

1. **Install Python**
   Download and install Python from [python.org](https://www.python.org/downloads/) (ensure version 3.8+)

2. **Install Jupyter Notebook**
   ```bash
   pip install notebook
   ```

3. **Install Required Libraries**
   Run the following command to install all dependencies:
   ```bash
   pip install numpy pandas matplotlib seaborn scipy deap
   ```

   Or use the requirements file (if provided):
   ```bash
   pip install -r requirements.txt
   ```

---

## Environment Setup

### Step 1: Clone or Download the Repository
```bash
cd /path/to/your/workspace
git clone <repository-url>
cd Final_Project
```

### Step 2: Verify Python Installation
```bash
python --version
```
Expected output: `Python 3.8.x` or higher

### Step 3: Verify Dependencies
```bash
python -c "import numpy, pandas, matplotlib, seaborn, scipy, deap; print('All dependencies installed successfully!')"
```

### Step 4: Launch Jupyter Notebook
```bash
jupyter notebook
```

This will open a browser window showing the file explorer. Navigate to and open [sudokuEA.ipynb](sudokuEA.ipynb).

---

## Running the Project

### Option 1: Run All Cells (Recommended)
1. Open [sudokuEA.ipynb](sudokuEA.ipynb) in Jupyter Notebook
2. Click **"Kernel"** → **"Restart & Run All"**
3. Wait for execution to complete (may take 5-15 minutes depending on parameters)

### Option 2: Run Step-by-Step
Execute cells sequentially from top to bottom:

1. **Section 0: Setup** - Import libraries and define the Sudoku puzzle
2. **Section I: Backtracking Benchmark** - Run traditional solver
3. **Section II: EA Setup** - Configure DEAP framework, fitness function, and genetic operators
4. **Section III: Parameter Tuning** - Define tuning strategies (Grid, Random, LHS)
5. **Section IV: Experiment Execution** - Run GA with multiple parameter configurations
6. **Section V: Visualization** - Generate plots and analysis
7. **Section VI: Main Execution** - Execute full pipeline and display results

### Expected Outputs

The notebook will generate:
- **Console Output**: Progress logs, benchmark results, and summary statistics
- **Visualizations**:
  - Fitness distribution boxplots
  - Population size vs fitness scatter plots
  - Success rate bar charts
  - Convergence curves showing fitness improvement over generations
  - Parameter sensitivity heatmaps

---

## Configuration Parameters

You can adjust the following parameters in the `__main__` section of the notebook:

### Genetic Algorithm Parameters
```python
param_grid = {
    "NPOP": [100, 300, 500],      # Population size
    "PC": [0.5, 0.8],              # Crossover probability
    "PM": [0.2, 0.5],              # Mutation probability
    "k": [3, 5],                   # Tournament size
    "indpb": [0.05, 0.1, 0.2]      # Row mutation probability
}
```

### Experiment Settings
- `n_runs`: Number of runs per configuration (default: 5 for statistical significance)
- `n_gen`: Maximum number of generations (default: 500)

### Sudoku Puzzle
Modify the `PROBLEM_GRID` variable in the notebook to test different puzzles (use `0` for empty cells).

---

## Project Structure

```
Final_Project/
├── sudokuEA.ipynb          # Main Jupyter notebook
├── README.md               # This file
├── requirements.txt        # Python dependencies (optional)
└── Output_Images/          # Directory for saved visualizations
```

---

## Understanding the Output

### Benchmark Results
```
Backtracking Result: {
    "Method": "Backtracking",
    "Success": True,
    "Time": 0.00234s,
    "Evaluations": 123,
    "Best_Fitness": 0
}
```

### Best AI Configuration
```
Best AI Config: Method=Grid Search, Pop=500, PM=0.2, indpb=0.1
Best AI Fitness: Avg=2.3 (±1.5), Success Rate=80%
```

### Metrics Explained
- **Avg_Fitness**: Average constraint violations (0 = perfect solution)
- **Success_Rate**: Percentage of runs that found a complete solution
- **Avg_Time**: Average execution time in seconds
- **Avg_Evals**: Average number of fitness evaluations

---

## Troubleshooting

### Common Issues

1. **ModuleNotFoundError: No module named 'deap'**
   ```bash
   pip install deap
   ```

2. **Jupyter Notebook not found**
   ```bash
   pip install notebook
   ```

3. **Slow execution**
   - Reduce `n_gen` (e.g., from 500 to 100)
   - Reduce `n_runs` (e.g., from 5 to 2)
   - Reduce population sizes in `param_grid`

4. **Out of memory errors**
   - Reduce population size (`NPOP`)
   - Close other applications

---

## Algorithm Details

### Evolutionary Algorithm Components
1. **Representation**: Each individual is a 9×9 grid where rows are valid permutations of 1-9
2. **Fitness Function**: Counts constraint violations in columns and 3×3 blocks
3. **Selection**: Tournament selection
4. **Crossover**: Custom row-swap operator (preserves row constraints)
5. **Mutation**: Intra-row swap of mutable cells
6. **Elitism**: Best individual always survives
7. **Hybrid Local Search**: Hill climbing applied periodically to refine solutions

### Performance Optimization Features
- Early stopping when solution is found (fitness = 0)
- Elitism to preserve best solutions
- Custom operators that respect Sudoku constraints
- Hybrid local search for exploitation

---

## References

- **DEAP Documentation**: [https://deap.readthedocs.io/](https://deap.readthedocs.io/)
- **Sudoku Rules**: [https://en.wikipedia.org/wiki/Sudoku](https://en.wikipedia.org/wiki/Sudoku)

---

## License

This project is for educational purposes as part of CS 5660 coursework.

---

## Contact

For questions or issues, please contact any team member listed above.