# Setup Instructions

This page provides detailed instructions for setting up the development environment for the Signals and Systems Jupyter Book.

## Prerequisites

Before setting up the environment, ensure you have the following installed:

- **Python 3.12** or higher
- **Git** for version control
- **Conda** or **Miniconda** (recommended)

## Installation Methods

### Method 1: Using Conda (Recommended)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/cristofer/signals_and_systems_UFU.git
   cd signals_and_systems_UFU
   ```

2. **Create and activate the conda environment:**
   ```bash
   conda env create -f environment.yml
   conda activate signals
   ```

3. **Verify installation:**
   ```bash
   python --version
   jupyter --version
   ```

### Method 2: Using pip

1. **Clone the repository:**
   ```bash
   git clone https://github.com/cristofer/signals_and_systems_UFU.git
   cd signals_and_systems_UFU/book
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Building the Book

### Local Development

1. **Build the book:**
   ```bash
   cd book
   jupyter-book build .
   ```

2. **View the book locally:**
   ```bash
   jupyter-book serve ./_build/html
   ```

3. **Clean build artifacts:**
   ```bash
   jupyter-book clean .
   ```

### Interactive Development

1. **Start JupyterLab:**
   ```bash
   jupyter lab
   ```

2. **Open individual notebooks** from the `chapters/` directory

3. **Run code cells** to see interactive visualizations

## Troubleshooting

### Common Issues

1. **Build errors:**
   - Ensure all dependencies are installed
   - Check Python version compatibility
   - Verify file paths in `_toc.yml`

2. **Missing plots:**
   - Ensure matplotlib backend is properly configured
   - Check for missing data files

3. **Import errors:**
   - Verify Python path and package installation
   - Check for missing dependencies

### Getting Help

- Check the [Jupyter Book documentation](https://jupyterbook.org/)
- Open an issue on GitHub
- Contact the course instructors

## Development Workflow

1. **Make changes** to markdown files or notebooks
2. **Test locally** by building the book
3. **Commit changes** to git
4. **Push to GitHub** to trigger automatic deployment

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Additional Resources

- [Jupyter Book Documentation](https://jupyterbook.org/)
- [MyST Markdown Guide](https://myst-parser.readthedocs.io/)
- [Sphinx Documentation](https://www.sphinx-doc.org/)
- [Python Scientific Computing](https://scipy.org/)

---

*For questions or support, please open an issue or contact the course instructors.*
