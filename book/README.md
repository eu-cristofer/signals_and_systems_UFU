# Signals and Systems - Jupyter Book

This repository contains an interactive Jupyter Book for the Signals and Systems course at Universidade Federal de Uberlândia (UFU).

## 📚 About This Book

This interactive textbook covers fundamental concepts in signals and systems, including:

- Signal classification and properties
- System analysis in time and frequency domains
- Fourier, Laplace, and Z-transforms
- Sampling theory and digital signal processing
- Filter design techniques
- Real-world applications

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip (Python package installer)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/cristofer/signals_and_systems_UFU.git
   cd signals_and_systems_UFU
   ```

2. **Install dependencies:**
   ```bash
   cd book
   pip install -r requirements.txt
   ```

3. **Build the book:**
   ```bash
   jupyter-book build .
   ```

4. **View the book:**
   ```bash
   jupyter-book serve ./_build/html
   ```

The book will be available at `http://localhost:8000`

## 📖 Reading the Book

### Online Version
The book is published online at: [https://cristofer.github.io/signals_and_systems_UFU/](https://cristofer.github.io/signals_and_systems_UFU/)

### Local Development
For local development and interactive content:

1. **Start JupyterLab:**
   ```bash
   jupyter lab
   ```

2. **Open individual notebooks** from the `chapters/` directory

3. **Run code cells** to see interactive visualizations and examples

## 🛠️ Development

### Project Structure

```
book/
├── _config.yml              # Jupyter Book configuration
├── _toc.yml                 # Table of contents
├── intro.md                 # Introduction page
├── chapters/                # Chapter content
│   ├── 01_introduction/     # Chapter 1: Introduction
│   ├── 02_time_domain/      # Chapter 2: Time Domain Analysis
│   ├── 03_frequency_domain/ # Chapter 3: Frequency Domain
│   ├── 04_laplace/          # Chapter 4: Laplace Transform
│   ├── 05_z_transform/      # Chapter 5: Z-Transform
│   ├── 06_sampling/         # Chapter 6: Sampling
│   ├── 07_filters/          # Chapter 7: Filter Design
│   └── 08_applications/     # Chapter 8: Applications
├── appendices/              # Appendices and references
├── requirements.txt         # Python dependencies
├── setup.md                # Setup instructions
└── README.md               # This file
```

### Adding Content

1. **New chapters:** Add to `_toc.yml` and create directory in `chapters/`
2. **New sections:** Add markdown files in appropriate chapter directory
3. **Interactive content:** Use Jupyter notebooks (`.ipynb`) or markdown with code cells

### Code Style

- Use Python 3.8+ features
- Follow PEP 8 style guidelines
- Include docstrings for functions
- Add comments for complex mathematical concepts

### Building and Testing

```bash
# Build the book
jupyter-book build .

# Clean build artifacts
jupyter-book clean .

# Test specific pages
jupyter-book build . --builder linkcheck
```

## 📝 Contributing

We welcome contributions! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Guidelines

- Follow the existing structure and style
- Include interactive examples where possible
- Test all code cells before submitting
- Update the table of contents if adding new content

## 🎯 Learning Objectives

After completing this book, students will be able to:

- [ ] Classify signals and systems according to their properties
- [ ] Analyze linear time-invariant (LTI) systems using various mathematical tools
- [ ] Apply frequency domain techniques for signal analysis and system design
- [ ] Design basic filters for signal processing applications
- [ ] Understand sampling theory and its implications in digital signal processing
- [ ] Use computational tools (Python/MATLAB) for signal analysis and visualization

## 📚 Additional Resources

### Textbooks
- Oppenheim, A. V., & Willsky, A. S. (1997). *Signals and Systems*
- Lathi, B. P. (2009). *Linear Systems and Signals*
- Haykin, S., & Van Veen, B. (2003). *Signals and Systems*

### Online Resources
- [MIT OpenCourseWare - Signals and Systems](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-003-signals-and-systems-fall-2011/)
- [Python Signal Processing](https://scipy.org/docs/scipy/reference/signal.html)
- [MATLAB Signal Processing Toolbox](https://www.mathworks.com/products/signal.html)

### Software
- **Python:** NumPy, SciPy, Matplotlib, Jupyter
- **MATLAB:** Signal Processing Toolbox, Control System Toolbox
- **Other:** GNU Octave, Scilab

## 🐛 Troubleshooting

### Common Issues

1. **Build errors:** Check that all dependencies are installed
2. **Missing plots:** Ensure matplotlib backend is properly configured
3. **Import errors:** Verify Python path and package installation

### Getting Help

- Check the [Jupyter Book documentation](https://jupyterbook.org/)
- Open an issue on GitHub
- Contact the course instructors

## 📄 License

This work is licensed under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Universidade Federal de Uberlândia (UFU)
- Students and faculty who provided feedback
- Open source community for excellent tools and libraries

---

**Happy Learning! 🚀**

*For questions or support, please open an issue or contact the course instructors.*
