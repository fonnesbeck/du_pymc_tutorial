# Getting Started with PyMC v5

## Data Umbrella Tutorial Syllabus

### Course Description
This one-hour tutorial introduces new users to version 5 of PyMC, a powerful Python library for probabilistic programming and Bayesian statistical modeling. Participants will learn the fundamentals of PyMC, best practices for installation and setup, and gain hands-on experience building their first Bayesian model.

### Learning Objectives
By the end of this tutorial, participants will:
- Understand what PyMC is and when to use it
- Know how to properly install and configure PyMC
- Understand the difference between probabilistic programming and Bayesian inference
- Be able to build and diagnose a simple Bayesian model
- Know where to find resources for continued learning

### Prerequisites
- Basic Python programming knowledge
- Familiarity with NumPy and basic statistics

### Tutorial Outline

#### 1. Introduction to PyMC and Bayesian Modeling
- What is PyMC? (Statistics + Probabilistic Thinking + Python)
- Why Bayesian modeling vs traditional approaches
- Real-world applications across industries
- Understanding uncertainty quantification

#### 2. Installation and Environment Setup
- Recommended installation with conda-forge
- Fresh environment setup for beginners
- Pixi for modern package management
- Sampling backends and computational libraries
- Testing your installation
- Troubleshooting common issues and performance optimization

#### 3. PyMC Fundamentals
- Bayes' theorem and the computational challenge
- MCMC to the rescue (NUTS sampling)
- The model container and context managers
- Random variables and distributions
- Observed data and likelihood specification
- Data handling best practices and common pitfalls
- PyMC ❤️ ArviZ integration

#### 4. Building Your First Model: Bioassay Example
- The bioassay problem: dose-response modeling
- Building the logistic regression model
- Common modeling errors to avoid
- Prior predictive checks
- Sampling the posterior with MCMC
- Trace plots and convergence checking
- Posterior distributions and parameter relationships
- Model summary and diagnostics
- Posterior predictive checks
- Making predictions for new data

#### 5. Common Pitfalls and Solutions
- Convergence diagnostics (R-hat, ESS, divergences)
- Understanding and fixing divergences
- Diagnosing sampling problems ("Bad initial energy")
- Performance optimization strategies
- Prior specification problems and debugging workflow
- Conceptual clarifications (MAP deprecation, PyMC3 vs PyMC)

#### 6. The PyMC Ecosystem and Resources
- ArviZ for visualization and diagnostics
- Bambi for high-level modeling
- PyMC-Extras for cutting-edge methods
- Finding and using PyMC example notebooks
- Community resources and getting help
- Contributing to the project

#### 7. Future Directions
- Inference improvements (variational inference, Pathfinder, normalizing flows)
- User experience priorities (automation, installation, warm starts)
- Computational backends and hardware detection
- Community and development process improvements

