# Coding Standards

## 1. File Naming Conventions
- **Notebooks**: `[Order]_[Description].ipynb` (e.g., `01_exploratory_data_analysis.ipynb`)
- **Scripts**: `snake_case.py`
- **Data Files**: `snake_case.csv`, `snake_case.parquet`
- **Models**: `[ModelType]_[Date]_[Version].pkl` (e.g., `lgbm_20231027_v1.pkl`)

## 2. Directory Structure Compatibility
- **Project Structure**:
    - `data/`: Raw and processed data.
    - `notebooks/`: Jupyter notebooks for experiments.
    - `src/`: Reusable python scripts.
    - `models/`: Trained models.
    - `output/`: Submission files, reports.

## 3. Kaggle Notebook Context
- **Path Handling**: Ensure paths work in both local and Kaggle environments using conditional logic or configuration files.
- **External Libraries**: If non-standard libraries are required, include installation commands (commented out by default) at the top of the notebook.

## 4. Code Style
- Follow **PEP 8** guidelines.
- Use **Type Hinting** for function definitions in `src/`.
- Add **Docstrings** to functions and classes.
