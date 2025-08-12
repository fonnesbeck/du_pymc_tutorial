---
theme: neversink
title: Getting Started with PyMC
info: |
  ## Getting Started with PyMC
  Data Umbrella Tutorial

  A 1-hour introduction to probabilistic programming and Bayesian modeling with PyMC.
author: Christopher Fonnesbeck
organization: PyMC Labs
class: text-center
highlighter: shiki
drawings:
  persist: false
transition: slide-left
mdc: true
fonts:
  sans: Roboto
  mono: Fira Code
colorSchema: auto
themeConfig:
  primary: "#146b8c"
  secondary: "#44FFD2"
  accent: "#FFE66D"
  background: "#161C2C"
  text: "#F3EFF5"
---

<div class="flex justify-center mb-6">
  <img src="/PyMC.png" alt="PyMC" class="h-20">
</div>

# Getting Started with PyMC

by **Christopher Fonnesbeck** • *PyMC Labs*

:: note ::

\* Data Umbrella Tutorial

<!--
Today we'll cover:
- What PyMC is and why you should use it
- How to install and set up PyMC
- The fundamentals of probabilistic programming
- Building your first Bayesian model with real data
- Diagnosing and interpreting results
- Common pitfalls and how to avoid them
- The broader PyMC ecosystem

-->

---
layout: top-title
color: sky-light
align: c
---

:: title ::

# 🎯 What We'll Learn Today

:: content ::

<div class="grid grid-cols-2 gap-8 mt-6">
  <div>
    <div class="text-4xl mb-3">🧠</div>
    <div class="text-xl mb-2">Bayesian Thinking</div>
    <div class="text-sm text-gray-600">Understanding uncertainty and probabilistic models</div>
  </div>
  <div>
    <div class="text-4xl mb-3">🔧</div>
    <div class="text-xl mb-2">Hands-on Modeling</div>
    <div class="text-sm text-gray-600">Building, diagnosing, and analyzing statistical models</div>
  </div>
  <div>
    <div class="text-4xl mb-3">🌐</div>
    <div class="text-xl mb-2">Ecosystem Overview</div>
    <div class="text-sm text-gray-600">Tools, resources, and community connections</div>
  </div>
  <div>
    <div class="text-4xl mb-3">🚀</div>
    <div class="text-xl mb-2">Best Practices</div>
    <div class="text-sm text-gray-600">Avoiding common pitfalls</div>
  </div>
</div>

<!--
The four key areas we'll focus on:

1. Bayesian Thinking: Understanding how to think in terms of uncertainty, priors, and updating beliefs with data.

2. Practical Skills: You'll learn to write PyMC code, run MCMC samplers, and interpret results.

3. Data Analysis: We'll work with actual datasets and solve real problems, not just toy examples.

4. Best Practices: I'll share common mistakes I see in the field and how to avoid them.

This isn't just about learning PyMC syntax - it's about becoming a better data scientist who can handle uncertainty properly.
-->

---
layout: top-title
color: emerald-light
align: c
---

:: title ::

# What is PyMC?

:: content ::

<div class="text-center">
  <div class="text-6xl mb-8 mt-8">
    📊 + 🧠 + 🐍 = PyMC
  </div>

  <div class="text-2xl text-gray-600">
    Statistics + Probabilistic Thinking + Python
  </div>
</div>

<!--
PyMC is where Python meets probabilistic programming.

It's fundamentally different from traditional statistical packages:
- Instead of point estimates, we work with distributions
- Instead of p-values, we get credible intervals
- Instead of assuming our models are correct, we quantify our uncertainty

PyMC makes Bayesian modeling accessible by providing:
- Intuitive model specification using Python syntax
- Automatic differentiation for efficient computation
- State-of-the-art MCMC algorithms (especially NUTS)
- Seamless integration with the Python data science ecosystem
- Excellent visualization tools through ArviZ

Think of it as a way to build models that explicitly handle uncertainty at every step.
-->

---
layout: two-cols-title
columns: is-6
align: c-lt-lt
color: sky-light
---

:: title ::

# Why Bayesian Modeling?

:: left ::

## 📈 Traditional Approach

- Point estimates
- p-values
- Confidence intervals
- Null hypothesis testing

:: right ::

## 🎯 Bayesian Approach

- Full distributions
- Probability statements
- Credible intervals
- Direct inference

<!--
The Bayesian approach is fundamentally more intuitive and informative:

Traditional Statistics:
- Gives you point estimates with error bars
- p-values are confusing (what's the probability that the null hypothesis is true? NOT what p-values tell you!)
- Confidence intervals have a weird interpretation: "If we repeated this study 100 times, 95% of the confidence intervals would contain the true value"
- Focuses on rejecting null hypotheses rather than quantifying effects (p-values)

Bayesian Statistics:
- Gives you the full distribution of possible parameter values
- You can make direct probability statements: "There's a 95% chance the effect is between X and Y"
- Credible intervals have the intuitive interpretation you want
- You can incorporate prior knowledge naturally
- You get uncertainty quantification for free

The Bayesian approach answers the questions you actually want to ask about your data.
-->

---
layout: top-title
color: indigo-light
align: c
---

:: title ::

# Real-World Applications

:: content ::

<div class="grid grid-cols-3 gap-6 mt-4">
  <div class="text-center">
    <div class="text-3xl mb-2 text-blue-400">🏥</div>
    <div class="text-lg font-semibold">Healthcare</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-green-400">💰</div>
    <div class="text-lg font-semibold">Finance</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-purple-400">🧬</div>
    <div class="text-lg font-semibold">Biology & Genomics</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-orange-400">📱</div>
    <div class="text-lg font-semibold">Technology</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-cyan-400">🌌</div>
    <div class="text-lg font-semibold">Physics & Astronomy</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-indigo-400">🧠</div>
    <div class="text-lg font-semibold">Social Sciences</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-red-400">⚾</div>
    <div class="text-lg font-semibold">Sports Analytics</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-teal-400">🌍</div>
    <div class="text-lg font-semibold">Ecology & Climate</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2 text-yellow-400">⚡</div>
    <div class="text-lg font-semibold">Energy & Utilities</div>
  </div>
</div>

<div class="mt-6 text-center text-lg text-gray-600">
  PyMC is used wherever uncertainty quantification matters
</div>

<!--
PyMC is used across virtually every industry and scientific field because uncertainty is everywhere:

Healthcare:
- Clinical trials need to account for patient variability
- Drug dosing must be personalized based on patient characteristics
- Epidemiological models help track disease spread with uncertainty
- Diagnostic tests have false positive/negative rates that need proper handling
- Survival analysis for treatment effectiveness

Finance:
- Risk models must quantify uncertainty in potential losses
- Portfolio optimization needs to account for parameter uncertainty
- Credit scoring benefits from hierarchical models for different populations
- Market forecasting explicitly acknowledges we don't know the future
- Fraud detection with adaptive thresholds

Biology & Genomics:
- Gene expression analysis with biological variability
- Population genetics and evolutionary dynamics
- Protein structure prediction with uncertainty
- Personalized medicine based on genomic data
- Systems biology modeling of complex pathways

Technology:
- A/B testing with proper statistical inference
- Recommendation systems that adapt to user preferences
- Anomaly detection that adapts to changing baselines
- User behavior models that capture individual differences
- Natural language processing uncertainty

Physics & Astronomy:
- Particle physics data analysis at CERN
- Cosmological parameter estimation
- Exoplanet detection from noisy telescope data
- Quantum system calibration
- Material science property prediction

Psychology & Social Sciences:
- Cognitive modeling of human behavior
- Social network analysis and influence
- Educational assessment with item response theory
- Political polling and election forecasting
- Economic behavior modeling

Sports Analytics:
- Player performance modeling and evaluation
- Game outcome prediction and betting odds
- Team strategy optimization under uncertainty
- Injury risk assessment and prevention
- Fan engagement and attendance forecasting

Ecology & Climate:
- Climate change modeling and projections
- Species distribution and biodiversity assessment
- Ecosystem dynamics and food webs
- Conservation planning under uncertainty
- Environmental impact assessment

Energy & Utilities:
- Load forecasting for power grids
- Renewable energy production prediction
- Asset reliability and maintenance scheduling
- Oil & gas exploration uncertainty
- Smart grid optimization

The common thread: all these applications involve uncertainty that needs to be properly quantified and propagated. PyMC provides the tools to handle this uncertainty rigorously.
-->


---
layout: section
color: blue-light
---

# 📦 Installation & Setup

Let's get you up and running!

<!--
Before we dive into modeling, let's make sure everyone has PyMC properly installed and configured.

There are a few different ways to install PyMC, and the choice depends on your setup and needs. I'll show you the recommended approaches and help you troubleshoot common issues.

Don't worry if you run into problems - PyMC has some complex dependencies, and installation issues are common. We'll work through them together.
-->

---
layout: top-title
align: c
---

:: title ::

# 🚀 Recommended Installation

:: content ::

<div class="text-4xl mb-6 font-mono">
  conda install -c conda-forge pymc
</div>

<div class="text-lg text-gray-500 mb-6">
  (conda-forge is the official recommended method)
</div>

<div class="text-lg">
  ✅ Best dependency management<br>
  ✅ Includes ArviZ automatically<br>
  ✅ Most stable installation
</div>

<!--
The PyMC team officially recommends conda-forge for installation:

```bash
# Create a new environment (recommended)
conda create -c conda-forge -n pymc_env "pymc>=5"
conda activate pymc_env
```

Or install in existing environment:
```bash
conda install -c conda-forge pymc
```

Why conda-forge is recommended:
- Better handling of complex numerical dependencies (BLAS, LAPACK)
- Pre-compiled binaries avoid compilation issues
- Consistent versions across the numerical Python stack
- Official PyMC recommendation per documentation

For advanced users who need cutting-edge features:
```bash
# Development installation in existing conda env
pip install -e .  # Only for contributors
```

Never use regular conda channel - always use conda-forge.
-->

---
layout: top-title
align: c
---

:: title ::

# 🆕 Fresh Environment Setup

:: content ::

<div class="text-4xl mb-6 font-mono">
  conda create -c conda-forge -n pymc_env "pymc>=5"
</div>

<div class="text-4xl mb-6 font-mono">
  conda activate pymc_env
</div>

<div class="text-lg text-gray-500 mb-6">
  (Recommended for beginners and clean installations)
</div>

<div class="text-lg">
  ✅ Isolated from other packages<br>
  ✅ Consistent dependency versions<br>
  ✅ Easy to recreate if needed<br>
  ✅ Python 3.10+ automatically included
</div>

<!--
Creating a dedicated environment is the safest approach:

Why a fresh environment?
- Avoids conflicts with existing packages
- Ensures consistent versions across the numerical stack
- Easy to delete and recreate if something goes wrong
- Isolation prevents breaking other projects

The command breakdown:
```bash
# Create new environment with PyMC 5+
conda create -c conda-forge -n pymc_env "pymc>=5"

# Activate the environment
conda activate pymc_env
```

Additional packages you might want:
```bash
# For Jupyter notebooks
conda install -c conda-forge jupyter

# For performance (optional)
conda install -c conda-forge nutpie

# For GPU acceleration (optional)
conda install -c conda-forge numpyro
```

Environment management tips:
- Use descriptive names: pymc_project, bayesian_analysis, etc.
- Document your environment: conda env export > environment.yml
- Share with others: conda env create -f environment.yml
- Clean up unused environments: conda env remove -n old_env_name

This approach prevents the majority of installation issues beginners encounter.
-->

---
layout: top-title
align: c
---

:: title ::

# 🧚 Pixi Installation

:: content ::

<div class="text-4xl mb-6 font-mono">
  pixi init my-pymc-project
</div>

<div class="text-4xl mb-6 font-mono">
  pixi add pymc
</div>

<div class="text-lg text-gray-500 mb-6">
  (Modern cross-platform package management)
</div>

<div class="text-lg">
  ✅ Reproducible environments<br>
  ✅ Lock files for exact versions<br>
  ✅ Cross-platform compatibility<br>
  ✅ Fast dependency resolution
</div>

<!--
Pixi is a modern package manager that's gaining popularity:

What is Pixi?
- Cross-platform package manager built in Rust
- Uses conda-forge packages but with better dependency resolution
- Creates reproducible environments with lock files
- Faster than traditional conda for many operations

Installation commands:
```bash
# Initialize new project
pixi init my-pymc-project
cd my-pymc-project

# Add PyMC and dependencies
pixi add pymc

# Optional: Add development dependencies
pixi add jupyter notebook --feature dev

# Run commands in the environment
pixi run python script.py
pixi run jupyter lab
```

Why choose Pixi?
- Lock files ensure exact reproducibility
- Faster dependency resolution than conda
- Better cross-platform support (Windows, macOS, Linux)
- Modern tooling with clear error messages
- Integrates well with CI/CD pipelines

Project structure:
- pixi.toml: project configuration and dependencies
- pixi.lock: exact versions for reproducibility
- .pixi/: environment directory (auto-generated)

When to use Pixi:
- New projects where reproducibility is critical
- Collaborative projects with multiple developers
- CI/CD environments
- When you want faster package management

Pixi is especially good for data science projects that need to be shared and reproduced exactly.
-->

---
layout: top-title-two-cols
color: blue-light
align: c-lt-lt
columns: is-6
---

:: title ::

# Sampling Backends & Libraries

:: left ::

<div class="bg-green-100 p-6 rounded-lg mb-6">
  <div class="text-xl font-bold text-green-800 mb-2">🔧 PyTensor (Default)</div>
  <div class="text-green-700 text-sm">
    • CPU-based, most stable<br>
    • Works everywhere<br>
    • All PyMC features supported
  </div>
</div>

<div class="bg-blue-100 p-6 rounded-lg">
  <div class="text-xl font-bold text-blue-800 mb-2">⚡ JAX + NumPyro</div>
  <div class="text-blue-700 text-sm">
    • GPU/TPU/CPU acceleration<br>
    • <code>conda install numpyro</code><br>
    • JIT compilation, some limitations
  </div>
</div>

:: right ::

<div class="bg-purple-100 p-6 rounded-lg mb-6">
  <div class="text-xl font-bold text-purple-800 mb-2">🚀 Nutpie</div>
  <div class="text-purple-700 text-sm">
    • Rust + Numba performance<br>
    • <code>conda install -c conda-forge nutpie</code><br>
    • Fast CPU NUTS, GPU with JAX
  </div>
</div>

<div class="bg-orange-100 p-6 rounded-lg">
  <div class="text-xl font-bold text-orange-800 mb-2">⚫ BlackJAX</div>
  <div class="text-orange-700 text-sm">
    • JAX-based samplers<br>
    • <code>conda install blackjax</code><br>
    • Advanced MCMC methods
  </div>
</div>

<!--
PyMC supports multiple computational backends and sampling libraries:

1. PyTensor Backend (Default):
   - CPU-based using NumPy/SciPy
   - Most stable and battle-tested
   - Works on any system with Python
   - All PyMC features fully supported
   - Best choice for learning and most applications

2. JAX Backend with NumPyro:
   - GPU, TPU, and CPU acceleration
   - Install: conda install numpyro
   - 5-10x faster for large models
   - JIT compilation for speed
   - Limitations: missing data handling, boolean masks, discrete variables, some PyTensor operations

3. Nutpie (Fast sampling):
   - Rust-based NUTS implementation with Numba
   - Install: conda install -c conda-forge nutpie
   - Fast CPU sampling, GPU support via JAX backend
   - Faster than default PyTensor for many models

4. BlackJAX (Advanced JAX samplers):
   - JAX-based sampling library
   - Install: conda install blackjax
   - SMC, sgMCMC, NUTS, VI
   - Useful for research and specialized sampling

For this tutorial, we'll use the default PyTensor backend since it works reliably for everyone and handles all our examples perfectly.

You can explore faster backends later when working with larger, more complex models.
-->

---
layout: top-title
align: c
---

:: title ::

# ✅ Test Your Installation

:: content ::

```python
import pymc as pm
print(f"PyMC version: {pm.__version__}")

import arviz as az
print(f"ArviZ version: {az.__version__}")

# Quick test
x = pm.Normal.dist(mu=0, sigma=1)
print(f"Test sample: {pm.draw(x, draws=3)}")
```

  🎉 If this runs, you're ready!

<div v-click class="mt-6">
<p class="text-lg mb-2 text-gray-600">Expected Output:</p>

```text
PyMC version: 5.25.0
ArviZ version: 0.22.0
Test sample: [ 0.75921629  1.11139729 -0.32886635]
```
</div>

<!--
Let's verify your installation works correctly.

First, check versions:
- PyMC version should be 5.x.x (we need version 5)
- ArviZ version should be 0.15+ for best compatibility

Then run a quick test to make sure the basic functionality works:
- Create a simple Normal distribution
- Draw some samples from it
- If you see an array of random numbers, everything is working!

Common issues and solutions:

If you get import errors:
- Try: pip install --upgrade pymc arviz
- Or: conda update pymc arviz

If you get compilation errors:
- On Windows: install Microsoft Visual C++ Build Tools
- On Mac: install Xcode command line tools (xcode-select --install)
- On Linux: install build-essential package

If sampling is very slow:
- This is normal for the first run (compilation overhead)
- Subsequent runs should be much faster
-->


---
layout: top-title
color: orange-light
align: c
---

:: title ::

# 🔧 Troubleshooting Common Issues

:: content ::

<Admonition type="warning" title="Most Common Issue">
The g++ compiler warning on Windows causes 10-100x performance degradation! Install `m2w64-toolchain` to fix this.
</Admonition>

<div class="grid grid-cols-2 gap-8 mt-6">
  <div class="bg-red-50 p-6 rounded-lg">
    <div class="text-red-700 font-bold mb-3 text-lg">💥 Import Errors</div>
    <div class="text-base text-red-600">
      pip install --upgrade pymc arviz<br>
      conda update -c conda-forge pymc
    </div>
  </div>
  <div class="bg-yellow-50 p-6 rounded-lg">
    <div class="text-yellow-700 font-bold mb-3 text-lg">⚠️ g++ Compiler Warning</div>
    <div class="text-base text-yellow-600">
      <strong>Windows users:</strong><br>
      conda install m2w64-toolchain<br>
      Fixes severe performance degradation
    </div>
  </div>
  <div class="bg-blue-50 p-6 rounded-lg">
    <div class="text-blue-700 font-bold mb-3 text-lg">🖥️ Platform-Specific</div>
    <div class="text-base text-blue-600">
      <strong>Mac M1/M2:</strong> Use conda-forge only<br>
      <strong>Linux:</strong> Generally smooth<br>
      <strong>Colab:</strong> May need runtime restart
    </div>
  </div>
  <div class="bg-green-50 p-6 rounded-lg">
    <div class="text-green-700 font-bold mb-3 text-lg">🚨 PyMC Versioning</div>
    <div class="text-base text-green-600">
      PyMC3 was renamed to PyMC at v4<br>
      Most v3 code works with minor edits, but use latest docs
    </div>
  </div>
</div>
---
layout: top-title
color: orange-light
align: c
---

:: title ::

# ⚡ Performance: BLAS Backends

:: content ::

- If you see: "Using NumPy C-API based implementation" your BLAS is slow
- Intel/AMD: prefer MKL builds via conda-forge (numpy, scipy)
- Apple Silicon: use conda-forge OpenBLAS/Accelerate (avoid MKL)

```bash
conda install -c conda-forge "numpy>=2" "scipy>=1.12"
```

<!--
BLAS choice strongly affects linear algebra speed.
- The warning indicates NumPy is not using an optimized BLAS
- On Intel, MKL builds from conda-forge are fast/stable
- On Apple Silicon, use conda-forge (OpenBLAS/Accelerate) rather than MKL
Also consider nutpie or JAX backends for additional speedups.
-->


<!--
Installation issues are the most common beginner pain points - here's what actually works:

Windows g++ Compiler Warning:
- Single most frequent issue: "WARNING (pytensor.configdefaults): g++ not available"
- Causes severe performance degradation (10-100x slower)
- Solution: conda install m2w64-toolchain in your PyMC environment
- This is a PyMC-specific issue, not general Python

Platform-Specific Issues:
- Mac M1/M2: BLAS library conflicts, avoid MKL packages, use conda-forge exclusively
- Linux: Generally smoothest installation experience
- Google Colab: Pre-installed packages conflict, may need runtime restart after pip install

Universal Best Practice:
- Always create dedicated environment: conda create -c conda-forge -n pymc_env "pymc>=5" python=3.10
- PyMC's complex dependency chain requires conda-forge for reliable installation
- pip installations frequently fail with BLAS or Unicode issues

Import/Version Errors:
- Try: conda update -c conda-forge pymc arviz
- If persistent: create fresh environment
- Never use regular conda channel - always conda-forge

Getting Help:
- discourse.pymc.io is extremely beginner-friendly
- Include full error messages and environment info
- Most installation issues have been solved before
-->

---
layout: section
color: emerald-light
---

# 🧠 PyMC Fundamentals

The building blocks of Bayesian models

<!--
Now that we have PyMC installed, let's understand how it works.

PyMC has a few core concepts that are essential to understand:
- Model containers that hold everything together
- Random variables that represent unknown quantities
- Distributions that encode our assumptions
- Observed data that updates our beliefs

We'll start simple and build up complexity gradually. By the end of this section, you'll understand how PyMC thinks about statistical models.
-->

---
layout: top-title
color: amber-light
align: c
---

:: title ::

# Bayes' Theorem

:: content ::

$$
\Huge
\underbrace{P(\theta \mid \text{data})}_{\color{teal}{\small \text{Posterior}}} =
\frac{\overbrace{P(\text{data} \mid \theta)}^{\color{teal}{\small \text{Likelihood}}}\;\overbrace{P(\theta)}^{\color{teal}{\small \text{Prior}}}}{\underbrace{P(\text{data})}_{\color{teal}{\small \text{Evidence / Marginal\;Likelihood}}}}
$$



---
layout: top-title
color: amber-light
align: c
---

:: title ::

# The Computational Challenge

:: content ::

$$
\Huge
P(\text{data}) = \int P(\text{data}\mid\theta)\,P(\theta)\,d\theta
$$

<div class="text-7xl mt-8 text-center">😭</div>

<!-- Notes:
- The denominator is the marginal likelihood (evidence)
- High-dimensional parameter spaces make the integral intractable for real models
- No closed-form in general; brute-force numerical integration is infeasible
- Inspired by basic_bayes_slides styling (visual-first, minimal on-screen text)
-->

---
layout: top-title
color: amber-light
align: c
---

:: title ::

# MCMC to the Rescue

:: content ::

$$
\Huge
P(\theta\mid\text{data}) \propto P(\text{data}\mid\theta)\,P(\theta)
$$

<img src="/hmc.gif" class="w-full max-w-3xl mx-auto mt-8" style="max-height: 46vh; object-fit: contain;">

<!-- Notes:
- MCMC samples from the posterior without computing P(data)
- Posterior expectations, intervals, predictions computed from samples
- PyMC’s NUTS is efficient for complex models
- Keep on-screen text minimal; focus on the proportionality equation and animation
-->
---
layout: top-title
color: amber-light
align: c
---

:: title ::

# The Model Container

:: content ::

<div class="text-center mb-8">
  <div class="text-6xl mb-8">
    📦
  </div>
</div>

```python
with pm.Model() as model:
    # All random variables go here
    mu = pm.Normal("mu", mu=0, sigma=10)

    # PyMC tracks relationships automatically
    x = pm.Normal("x", mu=mu, sigma=1, observed=data)
```

<!--
The Model container is PyMC's way of organizing your statistical model.

Key points:
- Uses Python's `with` statement (context manager)
- Everything defined inside becomes part of the model
- PyMC automatically tracks variable relationships
- Variables must have unique names (strings)
- The model builds a computational graph behind the scenes

Think of it like a recipe:
- The model is your cookbook
- Each variable is an ingredient
- PyMC figures out how to combine everything

You can have multiple models in the same script, each with their own variables and parameters.

The model context is where the magic happens - PyMC builds a directed acyclic graph (DAG) that represents all the probabilistic relationships in your model.
-->

---
layout: top-title-two-cols
align: c-lt-lt
columns: is-6
---

:: title ::

# Random Variables & Distributions

:: left ::

```python
with pm.Model() as model:
    # Unobserved (parameters to estimate)
    mu = pm.Normal("mu", mu=0, sigma=10)
    sigma = pm.HalfNormal("sigma", sigma=1)

    # Deterministic transformations
    scaled_mu = pm.Deterministic("scaled_mu", mu * 2)

    # Observed (your data)
    y = pm.Normal("y", mu=mu, sigma=sigma, observed=data)
```

:: right ::

```python
# Visualize the model structure
pm.model_to_graphviz(model)
```

<div class="mt-4">
  <img src="/model_graph.png" alt="Model Graph" class="mx-auto" style="max-height: 55vh; width: auto;">
</div>


<!--
This slide demonstrates both the code structure and visual representation of PyMC models:

Left Side - Proper Model Context:
- All random variables must be defined within a `with pm.Model() as model:` context
- This allows PyMC to track variable relationships and build the computational graph
- The context manager ensures proper model organization and automatic dependency tracking

PyMC has three main types of variables:

1. Unobserved Random Variables (Parameters):
   - These are what you want to estimate
   - Have prior distributions that encode your beliefs
   - Example: mu ~ Normal(0, 10) says we think mu is around 0, but could be as far as ±20 with reasonable probability

2. Deterministic Variables:
   - Functions of other variables
   - No additional randomness
   - Useful for transformations and derived quantities
   - Example: scaled_mu = mu * 2

3. Observed Variables (Data):
   - Your actual data
   - Fixed during inference
   - Connected to parameters through the likelihood
   - Example: y ~ Normal(mu, sigma) where y is your observed data

Right Side - Graphical Model Visualization:
- pm.model_to_graphviz(model) creates a directed acyclic graph (DAG)
- Shows the probabilistic relationships between variables
- Helps visualize model structure and dependencies
- Useful for model validation and communication

The key insight: you're building a generative model. You're saying "this is how I think the data was generated" and then inverting that process to learn about the parameters.
-->

---
layout: top-title
color: purple-light
align: c
---

:: title ::

# Distribution Zoo 🦁

:: content ::

<img src="/plots/distributions/distribution_zoo.png" class="mx-auto" style="max-height: 55vh; width: auto; object-fit: contain;">

<!--
PyMC provides a comprehensive set of probability distributions:

Continuous Distributions:
- Normal: The workhorse, symmetric, unbounded

- Beta: For probabilities and proportions (0 to 1)
- Exponential: For positive values, waiting times
- Gamma: Positive values with more flexibility than exponential
- Student-t: Like normal but with heavier tails
- Many more: Uniform, LogNormal, Cauchy, etc.

Discrete Distributions:
- Poisson: Count data, events per time period
- Binomial: Success/failure with fixed number of trials
- Categorical: Multiple discrete outcomes
- Bernoulli: Single success/failure trial

Choosing distributions:
- Match the support to your data (positive, bounded, etc.)
- Consider the shape you expect
- Start simple (Normal is often a good default)
- Use domain knowledge when available

Each distribution has parameters that control its shape and location. Understanding these parameters is key to building good models.
-->

---
layout: top-title-two-cols
color: light
align: c-lt-lt
columns: is-6
---
:: title ::

# Observed Data

:: left ::

```python
# Your actual data
data = np.array([1.2, 2.3, 1.8, 2.9, 3.1])

with pm.Model() as model:
    mu = pm.Normal("mu", mu=0, sigma=10)
    sigma = pm.HalfNormal("sigma", sigma=1)
    observations = pm.Normal("obs", mu=mu,
                           sigma=sigma, observed=data)
```

:: right ::

## Key Points

- 🎯 `observed=data` makes it a likelihood
- 📊 Data shape must match distribution
- 🔗 Links parameters to your actual data
- ⚡ This is where Bayes' theorem happens!

<!--
The `observed` argument is where your data meets your model:

What happens with observed=data:
- Tells PyMC these values are fixed and known
- Creates the likelihood function automatically
- Links your parameters (mu, sigma) to your actual observations
- This is where Bayes' theorem gets applied

Important considerations:
- Data shape must match what the distribution expects
- Missing data (NaN) is handled automatically
- You can have multiple observed variables
- The observed variable name is just for reference

Behind the scenes:
- PyMC computes log P(data | parameters) for each MCMC sample
- Combined with priors P(parameters), this gives you the posterior
- The observed data never changes during sampling
- Only the parameters (mu, sigma) are updated

This is the heart of Bayesian inference: updating our beliefs about parameters based on observed data.
-->

---
layout: top-title-two-cols
color: red-light
align: c-lt-lt
columns: is-6
---

:: title ::

# 📊 Data Handling Pitfalls

:: left ::

### Common Mistakes


- ❌ Pandas operations inside model context
  - PyMC operates on tensors, not DataFrames
- ✅ Prepare data first
  - Do pandas ops outside the model, then use `.values`
- 🔁 Updatable data
  - Use `pm.Data()` objects for data that will change
- 🧩 Missing data
  - Prefer tensor operations like `pt.where()` over boolean masks

:: right ::

```python
# ❌ Wrong: pandas operations inside model
with pm.Model():
    means = df.groupby('category').mean()  # This fails!

# ✅ Correct: prepare data first
means = df.groupby('category').mean().values
with pm.Model():
    data = pm.Data("data", means)
```

<!--
Data preparation errors reflect fundamental misunderstandings about PyMC's computational model:

The Core Problem:
- PyMC operates on symbolic tensors, not pandas DataFrames
- Most pervasive mistake: using pandas operations inside model context
- df.groupby('category').mean() inside with pm.Model() fails
- PyMC needs fixed numpy arrays or tensor operations

The Solution Pattern:
1. Complete ALL pandas operations outside the model context
2. Convert results to numpy arrays (.values)
3. Use pm.Data() for data that needs updating
4. Enter the model context only with prepared tensors

Missing Data Handling:
- JAX/NumPyro backends don't support boolean masks
- Use pt.where() for conditional operations (works with all backends)
- Or explicitly model missing values as latent variables
- Avoid numpy-style masking operations

Categorical Variables:
- Don't one-hot encode everything for PyMC
- Use pd.factorize() for index-based encoding
- Combine with coordinate systems for meaningful labels
- More efficient and scales better for hierarchical models

Best Practice Workflow:
data_prep.py -> clean pandas operations
model.py -> pure PyMC tensor operations
This separation prevents most data handling errors.
-->

---
layout: top-title-two-cols
align: c-lt-lt
columns: is-6
---

:: title ::

# ArviZ: Diagnostics & Visualization

<div class="text-center mb-6">
  <a href="https://github.com/arviz-devs/arviz" target="_blank" class="text-blue-400 hover:text-blue-300 text-lg font-mono">
    📦 github.com/arviz-devs/arviz
  </a>
</div>

:: left ::

<div class="space-y-4">
  <div>
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_forest.png" class="w-full mx-auto" style="max-height: 25vh; object-fit: contain;">
  </div>
  <div>
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_parallel.png" class="w-full mx-auto" style="max-height: 25vh; object-fit: contain;">
  </div>
</div>

:: right ::

<div class="space-y-4">
  <div>
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_forest_ridge.png" class="w-full mx-auto" style="max-height: 25vh; object-fit: contain;">
  </div>
  <div>
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_joint.png" class="w-full mx-auto" style="max-height: 25vh; object-fit: contain;">
  </div>
</div>

<!--
ArviZ is the standard tool for Bayesian visualization and diagnostics:

Key Plot Types:

Trace Plots:
- Monitor MCMC convergence
- Identify mixing problems
- Essential for any Bayesian analysis

Forest Plots:
- Compare parameter estimates across models
- Show credible intervals clearly
- Great for hierarchical models with many parameters

Posterior Plots:
- Visualize parameter distributions
- Show credible intervals and point estimates
- Easy to interpret and share

Model Checking:
- Posterior predictive checks
- LOO-CV for model comparison
- Energy plots for NUTS diagnostics
- Rank plots for convergence assessment

Why ArviZ?
- Publication-quality plots out of the box
- Consistent API across different samplers (PyMC, Stan, etc.)
- Extensive customization options
- Integrates seamlessly with PyMC
- Active development and great documentation

The forest plot shown illustrates parameter estimates with uncertainty - much more informative than traditional point estimates + error bars.
-->


---
layout: top-title-two-cols
align: c-lt-lt
columns: is-6
---

:: title ::

# PyMC ❤️ ArviZ Integration
<div class="text-center text-base text-gray-400 mt-1">Seamless Bayesian Workflow</div>

:: left ::

<div class="text-2xl mb-4">🎨 PyMC</div>
<ul class="text-lg space-y-2">
  <div class="flex flex-col items-center">
    <div class="mt-2 text-sm text-gray-500">Model building + sampling</div>
    <img src="/pymc_sampling.gif" class="w-full max-w-md rounded-lg shadow" style="max-height: 45vh; object-fit: contain;">
  </div>
</ul>

:: right ::

<div class="text-2xl mb-4">📊 ArviZ</div>
<ul class="text-lg space-y-2">
  <div class="flex flex-col items-center">
    <div class="mt-2 text-sm text-gray-500">Visualization, diagnostics, model comparison</div>
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_trace_vlines.png" class="w-full max-w-md rounded-lg shadow" style="max-height: 45vh; object-fit: contain;">
    <img src="https://python.arviz.org/en/stable/_images/mpl_plot_ppc_cumulative.png" class="w-full max-w-md rounded-lg shadow" style="max-height: 45vh; object-fit: contain;">
  </div>
</ul>


<!--
PyMC and ArviZ work together seamlessly:

PyMC handles:
- Defining your statistical model
- Running MCMC sampling (NUTS algorithm)
- Prior and posterior predictive sampling
- Model comparison metrics (LOO, WAIC)

ArviZ provides:
- Publication-quality plots
- Comprehensive diagnostics
- Model checking tools
- Summary statistics and tables

The connection is through InferenceData:
- A standardized format for Bayesian analysis results
- Contains posterior samples, prior samples, observed data, etc.
- Works with PyMC, Stan, TensorFlow Probability, and more
- Makes your analysis reproducible and shareable

Typical workflow:
1. Define model in PyMC
2. Sample with pm.sample() → InferenceData object
3. Visualize and diagnose with ArviZ
4. Iterate and improve your model

This separation of concerns lets each tool focus on what it does best.
-->

---
layout: section
color: amber-light
---

# 🏗️ Building Your First Model

From data to insights with real examples

<!--
Now comes the fun part - building and fitting actual Bayesian models!

We'll work through a complete example from start to finish:
- Understand the problem and data
- Specify a Bayesian model
- Check our priors make sense
- Sample from the posterior
- Diagnose potential issues
- Interpret results
- Make predictions

This isn't a toy example - we'll use real data and go through all the steps you'd follow in practice.
-->

---
layout: top-title
align: c
---

:: title ::

# 🧪 The Bioassay Problem

:: content ::

<div class="grid grid-cols-2 gap-8 mt-6">
  <div>
    <div class="text-2xl mb-2">The Question</div>
    <div class="text-lg">How does drug dose affect mortality in lab animals?</div>
  </div>
  <div>
    <div class="text-2xl mb-2">The Data</div>
    <div class="text-lg mt-3 space-y-1">
      <div><strong>Dose:</strong> <code>[-0.86, -0.3, -0.05, 0.73]</code></div>
      <div><strong>Animals:</strong> <code>[5, 5, 5, 5]</code></div>
      <div><strong>Deaths:</strong> <code>[0, 1, 3, 5]</code></div>
    </div>
  </div>
</div>

<div class="mt-6 text-center text-lg text-gray-600">Classic dose-response modeling problem</div>

<!--
This is a classic problem in toxicology and pharmacology:

The Setup:
- We have 4 different dose levels (on log scale, centered)
- 5 animals tested at each dose
- We count how many animals died at each dose
- Goal: model the dose-response relationship

Why this matters:
# The data
# Standardize predictors for robust sampling
dose_raw = np.array([-0.86, -0.3, -0.05, 0.73])
dose = (dose_raw - dose_raw.mean()) / dose_raw.std()

- Understand drug safety and efficacy
- Determine safe dosage ranges
- Predict effects at untested doses
- Quantify uncertainty in our predictions

The Data:
- Dose -0.86: 0 out of 5 animals died (0% mortality)
- Dose -0.3: 1 out of 5 animals died (20% mortality)
- Dose -0.05: 3 out of 5 animals died (60% mortality)
- Dose 0.73: 5 out of 5 animals died (100% mortality)

Clear dose-response relationship, but we want to model this probabilistically to:
- Get uncertainty estimates
- Make predictions for new doses
- Understand the shape of the dose-response curve
-->

---
layout: top-title
align: c
---

:: title ::

# Building the Model

:: content ::

```python
# The data
dose = np.array([-0.86, -0.3, -0.05, 0.73])
n_animals = np.array([5, 5, 5, 5])
n_deaths = np.array([0, 1, 3, 5])

with pm.Model() as bioassay_model:
    # Updatable input
    dose = pm.Data('dose', dose)

    # Priors for intercept and slope
    alpha = pm.Normal('alpha', mu=0, sigma=2.5)
    beta = pm.Normal('beta', mu=0, sigma=2.5)

    # Logistic regression model
    theta = pm.invlogit(alpha + beta * dose)

    # Binomial likelihood
    deaths = pm.Binomial('deaths', n=n_animals, p=theta, observed=n_deaths)
```

<!--
Let's build this step by step:

The Data:
- dose: log-transformed and centered doses
- n_animals: number of animals at each dose (5 each)
- n_deaths: observed deaths at each dose

The Model Structure:

1. Priors:
   - alpha: intercept (log-odds at dose=0)
   - beta: slope (how log-odds change with dose)
   - Normal(0, 2.5) is weakly informative - allows wide range but prevents extreme values

2. Linear Predictor:
   - alpha + beta * dose gives log-odds of death
   - This is the standard logistic regression setup

3. Inverse Logit Transformation:
   - Converts log-odds to probabilities (0 to 1 range)
   - theta[i] = probability of death at dose[i]

4. Likelihood:
   - Binomial distribution: n_deaths ~ Binomial(n_animals, theta)
   - This says: at each dose, deaths follow a binomial distribution
   - Like flipping n_animals coins, each with probability theta of "death"

This is a generalized linear model (GLM) with logit link - a Bayesian version of logistic regression.
-->

---
layout: top-title-two-cols
color: red-light
align: c-lt-lt
columns: is-6
---

:: title ::

# ⚠️ Common Modeling Errors

:: left ::

### Frequent Issues

- 🔢 Shape mismatches
  - ValueError: Input dimension mis-match
  - Matrix vs element-wise operations
  - Specify shapes explicitly
- 📊 Broadcasting issues
  - Mixing <code>shape</code> and <code>dims</code>
  - Inconsistent coordinate systems
  - Check tensor shapes explicitly

:: right ::

```python
# ❌ Wrong: element-wise when you want matrix multiplication
mu = X * beta

# ✅ Correct: explicit matrix operations
beta = pm.Normal('beta', mu=0, sd=1, shape=(n_features,))
mu = pm.math.dot(X, beta)
```

<!--
Shape mismatches are the most common modeling error after installation:

Matrix Multiplication Confusion:
- Beginners confuse * (element-wise) with matrix multiplication
- ValueError: Input dimension mis-match is the telltale sign
- Always be explicit: use pm.math.dot() for matrix operations
- Specify shapes explicitly: shape=(n_features,) not just scalar

Broadcasting Problems:
- PyMC has strict broadcasting rules unlike NumPy
- Don't mix shape and dims parameters inconsistently
- Understand positional broadcasting vs named dimensions
- When in doubt, check tensor shapes with .eval()

Best Practices:
- Always specify shapes for coefficient vectors: shape=(n_features,)
- Use pm.math functions instead of numpy equivalents inside models
- Test with simple data first to catch shape errors early
- Be explicit about broadcasting operations

The pattern: beta with shape=(n_features,) and pm.math.dot(X, beta) works reliably for linear models.
-->

---
layout: top-title
align: c
---

:: title ::

# Prior Predictive Check

:: content ::

<img src="/plots/bioassay/prior_predictive.png" class="w-full max-w-4xl mx-auto" style="max-height: 65vh; object-fit: contain;">

<!--
Before fitting the model, let's check if our priors make sense:

What we're looking at:
- Each line shows a possible dose-response curve under our priors
- X-axis: dose (log scale)
- Y-axis: probability of death (0 to 1)

What we want to see:
- Curves that cover reasonable ranges
- Mostly monotonic relationships (higher dose → higher death probability)
- No extreme or impossible behaviors

What we observe:
- Good variety of curves from gentle to steep
- Most are monotonically increasing (good!)
- Some flat or slightly decreasing curves (that's okay - priors should be somewhat agnostic)
- Probability ranges from 0 to 1 as expected

This looks reasonable! Our priors allow for a wide range of dose-response relationships without being too restrictive.

If we saw problems (e.g., all curves were flat, or probabilities went outside [0,1]), we'd need to adjust our priors.

Prior predictive checks are crucial - they catch modeling mistakes before you waste time on sampling.
-->

---
layout: top-title
align: c
---

:: title ::

# Sampling the Posterior

:: content ::

```python
with bioassay_model:
    trace = pm.sample()
```

<div class="text-2xl mt-4 text-center">
  ⚡ MCMC sampling is (mostly) automatic! ⚡
</div>

<div v-click class="mt-6">
<p class="text-lg mb-2 text-gray-600">Terminal Output:</p>

```text
Auto-assigning NUTS sampler...
Initializing NUTS using jitter+adapt_diag...
Multiprocess sampling (4 chains in 4 jobs)
NUTS: [alpha, beta]

Sampling 4 chains for 1_000 tune and 2_000 draw iterations (4_000 tuning and 8_000 posterior samples) took 12 seconds.
The number of effective samples is smaller than 400 for some parameters.
```

<div class="mt-4 text-lg">
<strong>PyMC automatically:</strong>
<div class="grid grid-cols-2 gap-4 mt-2">
  <div>✓ Chose NUTS sampler</div>
  <div>✓ Tuned sampler hyperparameters</div>
  <div>✓ Ran 4 parallel chains</div>
  <div>✓ Monitored for sampling issues</div>
</div>
</div>

</div>

<!--
Time to fit the model using MCMC sampling:

What pm.sample() does:
- Automatically selects NUTS (No-U-Turn Sampler) - state of the art
- Runs a tuning phase to find good step sizes and mass matrix
- Samples from the posterior using 4 parallel chains
- Monitors convergence diagnostics
- Returns an InferenceData object with all results

Parameters explained:
- 2000: number of posterior samples per chain (after tuning)
- tune=1000: number of tuning/warmup samples (discarded)
- chains=4: number of parallel chains (helps detect convergence issues)
- random_seed=42: for reproducibility

What happens during sampling:
1. Tuning phase (1000 steps): NUTS learns about the posterior geometry
2. Sampling phase (2000 × 4 = 8000 total samples): collect posterior samples
3. Convergence checks: R-hat, effective sample size, divergences

Modern MCMC is remarkably robust:
- NUTS automatically adapts to the posterior shape
- Parallel chains help identify problems
- Comprehensive diagnostics catch most issues
- Most models "just work" without manual tuning

This is a huge advance over older MCMC methods that required lots of manual tuning.
-->

---
layout: top-title
align: c
---

:: title ::

# Trace Plots: Checking Convergence

:: content ::

```python
az.plot_trace(trace, var_names=['alpha', 'beta'])
```

<img src="/plots/bioassay/trace_plot.png" class="w-full max-w-3xl mx-auto" style="max-height: 50vh; object-fit: contain;">

<!--
Trace plots are your first check for sampling problems:

What we're looking at:
- Left panels: posterior distributions (what we care about)
- Right panels: trace plots showing parameter values over MCMC iterations

What we want to see:
- "Fuzzy caterpillars" - traces should look like random noise
- All chains (different colors) should overlap and explore the same space
- No obvious trends, patterns, or getting stuck
- Smooth, unimodal posterior distributions

What we observe:
- Both alpha and beta show excellent mixing
- All 4 chains are exploring the same regions
- No signs of convergence problems
- Posterior distributions look smooth and reasonable

Signs of problems to watch for:
- Chains that don't overlap (convergence failure)
- Trends in the traces (not stationary)
- Chains getting stuck in one region
- Very different behavior between chains

Our traces look great! This suggests our MCMC sampling worked well and we can trust our posterior estimates.
-->

---
layout: top-title
align: c
---

:: title ::

# Posterior Distributions

:: content ::

```python
az.plot_posterior(trace, var_names=['alpha', 'beta'])
```

<img src="/plots/bioassay/posterior_plot.png" class="w-full max-w-4xl mx-auto" style="max-height: 65vh; object-fit: contain;">

<!--
Now let's look at what we learned about the parameters:

Alpha (Intercept):
- Mean around 0.24
- Represents log-odds of death at dose = 0 (center of dose range)
- Exp(0.24) / (1 + exp(0.24)) ≈ 56% probability of death at average dose
- Uncertainty: 95% credible interval roughly [-1, 1.4]

Beta (Slope):
- Mean around 4.03
- Represents how log-odds change per unit increase in dose
- Strong positive relationship: higher dose → higher death probability
- This is a steep dose-response curve
- Uncertainty: 95% credible interval roughly [1.5, 6.9]

Key insights:
- There's definitely a dose-response relationship (beta > 0 with high confidence)
- But there's still uncertainty about the exact slope
- At the lowest dose, death probability is low but not zero
- At the highest dose, death probability is very high

Compare to classical statistics:
- Instead of point estimates + standard errors, we get full distributions
- Instead of p-values, we can make direct probability statements
- "There's a 97.5% chance beta is greater than 1.5" - much more intuitive!
-->

---
layout: top-title
align: c
---

:: title ::

# Parameter Relationships

:: content ::

```python
az.plot_pair(trace, var_names=['alpha', 'beta'], kind='scatter')
```

<img src="/plots/bioassay/pair_plot.png" class="w-full max-w-3xl mx-auto" style="max-height: 50vh; object-fit: contain;">

<!--
The pair plot shows how parameters relate to each other:

What we're looking at:
- Scatter plot of alpha vs beta posterior samples
- Each point represents one MCMC draw
- Contours show the joint posterior density

What we observe:
- Slight negative correlation between alpha and beta
- This makes sense: if the intercept is higher, the slope can be lower to fit the same data
- The correlation isn't too strong (good for inference)
- Joint distribution looks well-behaved (elliptical, unimodal)

Why parameter correlations matter:
- Strong correlations can slow MCMC sampling
- Indicate potential identifiability issues
- Affect prediction uncertainty
- Can suggest model reparameterizations

In our case:
- Correlation is mild and not problematic
- Both parameters are well-identified by the data
- The relationship makes biological sense

This is another sign that our model and sampling worked well. Strong correlations or weird shapes here would suggest problems.
-->

---
layout: top-title
align: c
---

:: title ::

# Model Summary

:: content ::

```python
az.summary(trace, var_names=['alpha', 'beta'])
```

| Parameter | mean  | sd    | hdi_3% | hdi_97% | mcse_mean | mcse_sd | ess_bulk | ess_tail | r_hat |
|-----------|-------|-------|--------|---------|-----------|---------|----------|----------|-------|
| alpha     | 0.241 | 0.634 | -0.985 | 1.430   | 0.010     | 0.008   | 4266.0   | 4089.0   | 1.0   |
| beta      | 4.034 | 1.447 | 1.532  | 6.869   | 0.022     | 0.018   | 5094.0   | 4724.0   | 1.0   |

<div class="mt-6 text-center">
  <div class="text-2xl">🎯 Excellent diagnostics!</div>
</div>

<!--
The summary table gives us key information about our posterior and sampling:

Key Statistics:
- mean: posterior mean (point estimate)
- sd: posterior standard deviation (uncertainty)
- hdi_3%, hdi_97%: 94% highest density interval (credible interval)

Diagnostics:
- mcse_mean, mcse_sd: Monte Carlo standard error (should be small)
- ess_bulk, ess_tail: effective sample size (want > 400, ideally > 1000)
- r_hat: potential scale reduction factor (want < 1.01, ideally 1.00)

Our Results:
- Both parameters well-estimated with reasonable uncertainty
- HDI intervals don't include extreme values
- Excellent effective sample sizes (4000+)
- Perfect R-hat values (1.0)
- Low Monte Carlo error

What this means:
- Our MCMC sampling was very efficient
- We have enough samples for reliable inference
- No convergence issues detected
- We can trust our posterior estimates

This is what good Bayesian inference looks like - clean diagnostics and interpretable results.
-->

---
layout: top-title
align: c
---

:: title ::

# Posterior Predictive Check

:: content ::

```python
with bioassay_model:
    posterior_predictive = pm.sample_posterior_predictive(trace)
```

<img src="/plots/bioassay/posterior_predictive.png" class="w-full max-w-3xl mx-auto" style="max-height: 50vh; object-fit: contain;">

<!--
The posterior predictive check validates our model against reality:

What we're looking at:
- Red points: observed data (actual death rates at each dose)
- Blue lines: predicted dose-response curves from posterior samples
- Yellow line: mean prediction across all posterior samples

What we want to see:
- Model predictions that capture the observed data
- Reasonable uncertainty bands around predictions
- No systematic deviations between model and data

What we observe:
- Model captures the dose-response trend very well
- Observed data points fall within the prediction envelope
- Smooth S-shaped curve characteristic of logistic regression
- Appropriate uncertainty - wider where we have less data

Model validation:
- At dose -0.86: model predicts low death probability (✓ matches 0/5 deaths)
- At dose 0.73: model predicts high death probability (✓ matches 5/5 deaths)
- Intermediate doses show reasonable predictions

This suggests our model is a good fit to the data and can be trusted for making predictions at new dose levels.

If we saw systematic deviations, we'd need to consider:
- Different link functions
- Non-linear dose effects
- Individual animal variability (hierarchical modeling)
-->


---

# Making Predictions

```python
# Predict mortality at new doses
new_doses = np.array([-1.0, 0.0, 1.0])

with bioassay_model:
    pm.set_data({'dose': new_doses})
    posterior_pred = pm.sample_posterior_predictive(trace)

# Get prediction intervals
pred_mortality = posterior_pred.posterior_predictive['deaths']
```

::: v-click
<div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-start mt-4">
  <div>
    <img src="/plots/bioassay/predictions.png" class="w-full max-w-3xl mx-auto" style="max-height: 55vh; object-fit: contain;">
  </div>
  <div>

```text
Dose  p(death) mean [94% HDI]
-1.00 0.045 [0.001, 0.196]
+0.00 0.554 [0.283, 0.816]
+1.00 0.962 [0.801, 1.000]

Expected deaths out of 5 [94% HDI]
-1.00 0.22 [0.01, 0.98]
+0.00 2.77 [1.41, 4.08]
+1.00 4.81 [4.00, 5.00]
```

  </div>
</div>
:::


---
layout: section
color: red-light
---

# ⚠️ Common Pitfalls & Solutions

Avoiding the traps that catch beginners

<!--
Even with modern tools like PyMC, Bayesian modeling can go wrong. Let me share the most common issues I see and how to fix them.

These aren't theoretical problems - these are real issues that will happen to you as you build more complex models. Learning to recognize and fix them is crucial for successful Bayesian analysis.

We'll cover:
- Convergence failures and how to diagnose them
- Divergences and what they mean for your results
- Performance issues and optimization strategies
- Prior specification problems
- Model checking failures
-->

---
layout: top-title
align: c
---

:: title ::

# Convergence Diagnostics

:: content ::

<div class="grid grid-cols-2 gap-6 mt-4">
  <div class="text-center">
    <div class="text-3xl mb-2">📈</div>
    <div class="text-xl mb-1">R-hat < 1.01</div>
    <div class="text-sm text-gray-600">Chains have converged</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2">📊</div>
    <div class="text-xl mb-1">ESS > 400</div>
    <div class="text-sm text-gray-600">Enough effective samples</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2">⚠️</div>
    <div class="text-xl mb-1">No/Few Divergences</div>
    <div class="text-sm text-gray-600">No numerical issues</div>
  </div>
  <div class="text-center">
    <div class="text-3xl mb-2">🔗</div>
    <div class="text-xl mb-1">Good Mixing</div>
    <div class="text-sm text-gray-600">"Fuzzy caterpillars" in chains</div>
  </div>
</div>


---
layout: top-title
align: c
---

:: title ::

# The Dreaded Divergences 💥

:: content ::

<div class="bg-red-50 p-6 rounded-lg mt-4">
  <div class="text-red-800 text-xl mb-3">
    "There were 547 divergences after tuning..."
  </div>

  <div class="text-red-700">
    <div class="text-lg mb-3">What this means:</div>
    <ul class="text-sm space-y-1">
      <li>🚨 NUTS sampler had numerical problems</li>
      <li>📊 Your results may be biased</li>
      <li>🔍 Something is wrong with your model</li>
      <li>⚡ Don't trust the posterior estimates</li>
    </ul>
  </div>
</div>

<!--
Divergences are the most common and concerning diagnostic issue:

What are divergences?
- NUTS uses Hamiltonian dynamics to propose moves
- Divergences occur when the numerical integration becomes unstable
- Usually happens in regions of high curvature or complex geometry
- The sampler "diverges" from the true trajectory

Why they're dangerous:
- Biased sampling: divergences often occur in important regions of the posterior
- Your posterior samples may not represent the true posterior
- Credible intervals may be too narrow
- Point estimates may be wrong

What causes divergences?
- Poorly specified priors (too wide or too narrow)
- Complex model geometry (funnels, multi-modality)
- Highly correlated parameters
- Numerical precision issues
- Model misspecification

The good news: divergences are usually fixable with the right approach. We'll see how in the next slides.
-->

---
layout: top-title-two-cols
color: red-light
align: c-lt-lt
columns: is-6
---

:: title ::

# Diagnosing Sampling Problems

:: left ::

### 🚨 "Bad Initial Energy"

```python
# First: diagnose the problem
with model:
    model.check_test_point()
# Common fixes:
pm.sample(init='adapt_diag')
pm.sample(init='jitter+adapt_diag')

# Or find reasonable starting point
with model:
    start = pm.find_MAP()  # Use sparingly
    trace = pm.sample(start=start)
```

:: right ::

### ⚡ Divergence Solutions

```python
# Step 1: More conservative sampling
pm.sample(target_accept=0.95, tune=2000)

# Step 2: Model reparameterization
# Non-centered for hierarchical models
theta_raw = pm.Normal('theta_raw', 0, 1)
theta = pm.Deterministic('theta',
                        mu + tau * theta_raw)

# Step 3: Check prior constraints
sigma = pm.HalfNormal('sigma', 1)  # not Normal
```

<!--
"Bad initial energy" and divergence errors are the top sampling issues beginners face:

"Bad Initial Energy" Diagnosis:
- Cryptic error message but straightforward diagnosis process
- Run model.check_test_point() to identify which variables have infinite log-probability
- Usually caused by inappropriate priors (Normal for positive parameters)
- Or initialization in impossible regions of parameter space

Practical Fixes:
- init='adapt_diag': better initialization using diagonal mass matrix
- init='jitter+adapt_diag': adds random jitter to starting values
- pm.find_MAP(): finds mode to start from (use sparingly, discouraged for modern practice)
- Check and fix prior specifications first

Divergence Solutions (Hierarchical):
- "There were X divergences after tuning" is common with hierarchical models
- Knee-jerk reaction: increase target_accept (0.9 to 0.99 often helps)
- Real solution: non-centered parameterization for hierarchical structures
- theta_raw ~ Normal(0,1) then theta = mu + tau * theta_raw
- Separates location (mu) and scale (tau) effects, easier geometry

Systematic Approach:
1. Check model.check_test_point() for infinite values
2. Fix prior constraints (HalfNormal for positive parameters)
3. Try conservative sampling (target_accept=0.95, tune=2000)
4. Reparameterize hierarchical components if needed
5. Only then consider more advanced techniques

Most "Bad initial energy" errors trace to wrong prior constraints - fix those first.
-->

---
layout: top-title-two-cols
align: c-lt-lt
columns: is-6
---

:: title ::

# Performance Optimization

:: left ::

### Tips

- 🚀 JAX backend: 5–10x speedups on many models
- 📊 Vectorize: avoid loops; use tensor ops
- 🎯 Start simple: add complexity gradually
- ⚡ Standardize predictors (zero mean, unit variance)

:: right ::

```python
# Switch to JAX backend for speed
import pymc as pm
pm.set_backend('jax')

# Or install numpyro for even more speed
pip install numpyro
```

<!--
If your models are running slowly, here are the main optimization strategies:

JAX Backend:
- Can provide 5-10x speed improvements
- GPU support for very large models
- JIT compilation optimizes repeated operations
- Install: pip install numpyro
- Switch: pm.set_backend('jax')
- Not all PyMC features supported yet

Vectorization:
- Avoid explicit loops in your model
- Use tensor operations instead
- Let PyMC/NumPy handle the broadcasting
- Example: instead of for loop over observations, use vector operations

Model Simplification:
- Start with the simplest model that could work
- Add complexity only when needed
- More parameters = slower sampling
- Sometimes a simpler model is actually better

Other optimizations:
- Standardize your predictors (zero mean, unit variance)
- Use informative priors when possible
- Consider model approximations (variational inference)
- Profile your code to find bottlenecks

Remember: premature optimization is the root of all evil. Get your model working correctly first, then optimize if needed.
-->

---
layout: top-title
---

:: title ::

# Prior Specification Problems

:: content ::

<div class="grid grid-cols-2 gap-8 mt-6">
  <div class="bg-red-50 p-6 rounded-lg">
    <div class="text-red-700 font-bold mb-3 text-lg">❌ Wrong Constraints</div>
    <div class="text-base text-red-600 font-mono">
      # Allows negative values!<br>
      sigma = pm.Normal('sigma', 0, 5)
    </div>
    <div class="text-base text-red-600 mt-3">
      → "Bad initial energy" errors<br>
      → Zero-valued likelihoods
    </div>
  </div>
  <div class="bg-green-50 p-6 rounded-lg">
    <div class="text-green-700 font-bold mb-3 text-lg">✅ Proper Constraints</div>
    <div class="text-base text-green-600 font-mono">
      # Ensures positive values<br>
      sigma = pm.HalfNormal('sigma', 5)
    </div>
    <div class="text-base text-green-600 mt-3">
      → Stable sampling<br>
      → Reasonable constraint
    </div>
  </div>
</div>

<div class="mt-6 bg-blue-50 p-6 rounded-lg">
  <div class="text-blue-800 font-bold mb-3 text-lg">🎯 Common Choices</div>
  <div class="text-base text-blue-700">
    • <strong>Standard deviations:</strong> HalfNormal, Half Cauchy<br>
    • <strong>Probabilities:</strong> Beta, Uniform(0,1)<br>
    • <strong>Rates:</strong> Gamma, Exponential<br>
    • <strong>Coefficients:</strong> Normal(0, s) for standardized data<br>
    • <strong>Always</strong> do prior predictive checks!
  </div>
</div>

<!--
The classic beginner mistake: using Normal priors for parameters that must be positive:

Wrong Constraint Priors:
- sigma = pm.Normal('sigma', mu=0, sigma=5) allows negative values
- Creates "Bad initial energy" errors when MCMC draws negative standard deviations
- Impossible likelihoods when sigma < 0
- This is the most frustrating category of errors for beginners

The Fix is Simple:
- Use constrained distributions: HalfNormal, Exponential, Gamma for positive parameters
- sigma = pm.HalfNormal('sigma', sigma=5) ensures sigma > 0
- Critical for standard deviations, variances, rates, scales

Other Common Prior Mistakes:
- Overly vague priors (sigma=10000) allow unrealistic parameter values
- Uniform priors create sampling difficulties (flat regions are hard to explore)
- Normal priors for probabilities (should use Beta)

Practical Rules for Common Parameters:
- Standard deviations: HalfNormal(sigma=1) or Exponential(lam=1)
- Probabilities: Beta(2, 2) (mild preference for 0.5)
- Correlation coefficients: LKJ prior for positive definite matrices
- Regression coefficients: Normal(0, 2.5) for standardized predictors

The pattern: choose distributions whose support matches parameter constraints. Prior predictive checks catch violations before sampling.
-->

---
layout: top-title
align: c
---

:: title ::

# Debugging Workflow

:: content ::

<div class="text-2xl mb-6">When things go wrong...</div>

<div class="grid grid-cols-2 gap-8 mt-4">
  <div>
    <div class="text-xl mb-3">🔍 Diagnostic Steps</div>
    <ol class="text-sm space-y-2">
      <li>Check trace plots</li>
      <li>Look at R-hat values</li>
      <li>Check effective sample size</li>
      <li>Count divergences</li>
      <li>Do posterior predictive checks</li>
    </ol>
  </div>
  <div>
    <div class="text-xl mb-3">🛠️ Fix Strategy</div>
    <ol class="text-sm space-y-2">
      <li>Try sampler tuning first</li>
      <li>Examine prior predictive samples</li>
      <li>Simplify the model</li>
      <li>Reparameterize if needed</li>
      <li>Ask for help on discourse!</li>
    </ol>
  </div>
</div>

<!--
When your model isn't working, follow this systematic debugging approach:

Diagnostic Phase:
1. Trace plots: Do they look like fuzzy caterpillars?
2. R-hat: Are all values < 1.01?
3. ESS: Do you have > 400 effective samples?
4. Divergences: Are there any? Even a few is concerning
5. Posterior predictive: Does the model capture your data?

Fix Strategy:
1. Sampler tuning: Try target_accept=0.95, more tuning steps
2. Prior predictive: Do your priors make sense? Generate reasonable data?
3. Simplify: Remove complexity until it works, then add back gradually
4. Reparameterize: Non-centered parameterization, parameter transforms
5. Get help: PyMC community is very supportive of beginners

Common Progression:
- Start with simplest possible model
- Check it works (good diagnostics)
- Add one piece of complexity at a time
- Diagnose issues immediately when they arise
- Don't move forward with bad diagnostics

Remember: a simple model that works is better than a complex model that doesn't. You can always add complexity later once you have a solid foundation.
-->


---
layout: top-title
align: c
---

:: title ::

# Bambi: High-Level Modeling

<div class="text-center mb-6">
  <a href="https://github.com/bambinos/bambi" target="_blank" class="text-blue-400 hover:text-blue-300 text-lg font-mono">
    📦 github.com/bambinos/bambi
  </a>
</div>

:: content ::

```python
import bambi as bmb

# R-style formula interface
model = bmb.Model('y ~ x1 + x2 + (1|group)', data=my_data)

# Automatic priors and sampling
results = model.fit()
```

<div class="text-2xl mt-8 text-center">
  🎯 Like rstanarm/brms for Python!
</div>

<!--
Bambi provides a high-level interface for common statistical models:

Key Features:

Formula Interface:
- R-style formula syntax: 'y ~ x1 + x2 + (1|group)'
- Automatic handling of categorical variables
- Built-in interactions and transformations
- Hierarchical/mixed effects models

Automatic Priors:
- Sensible default priors based on data
- Weakly informative, properly scaled
- Can override when needed
- Handles centering and scaling automatically

Common Model Types:
- Linear regression
- Logistic regression
- Hierarchical/mixed effects models
- Generalized linear models
- Time series models

When to Use Bambi:
- Standard statistical models
- Quick exploratory analysis
- When you want to focus on interpretation, not model specification
- Teaching statistics (great for students coming from R)

When to Use PyMC Directly:
- Custom models not covered by Bambi
- Need full control over priors and likelihood
- Complex, domain-specific models
- Research applications

Bambi is perfect for 80% of applied statistical modeling, while PyMC handles the remaining 20% of specialized applications.
-->

---
layout: top-title-two-cols
align: c-lt-lt
columns: is-6
---

:: title ::

# PyMC-Extras: Cutting Edge

<div class="text-center mb-6">
  <a href="https://github.com/pymc-devs/pymc-extras" target="_blank" class="text-blue-400 hover:text-blue-300 text-lg font-mono">
    📦 github.com/pymc-devs/pymc-extras
  </a>
</div>

:: left ::

<div class="text-2xl mb-3">🧪 New Methods</div>
<ul class="text-lg space-y-2">
  <li>Pathfinder and Laplace approximations</li>
  <li>Sequential Monte Carlo (SMC)</li>
  <li>State space modeling toolkit (filters, models)</li>
  <li>GP latent approximations</li>
</ul>

:: right ::

<div class="text-2xl mb-3">🚀 Experimental Features</div>
<ul class="text-lg space-y-2">
  <li>Extra distributions and transforms</li>
  <li>Model builder and linear-model helpers</li>
  <li>Preprocessing and utilities</li>
  <li>Experimental inference APIs</li>
</ul>

<div class="mt-6 text-center text-lg text-gray-600">
  💡 Some features matriculate to PyMC when stable
</div>

<!--
PyMC-Extras is where new features are developed and tested:

New Statistical Methods:
- Pathfinder: mode-seeking approximate inference
- Laplace approximation around posterior mode
- Sequential Monte Carlo (SMC)
- GP latent approximations
- State space toolkit (filters, models)

Experimental Features:
- Additional distributions and transforms
- Model builder, priors, printing, and serialization helpers
- Preprocessing and utility functions
- Experimental inference APIs (fit utilities)

How It Works:
- Install: pip install pymc-extras
- Import specific modules you need
- Features are less stable than main PyMC
- Extensive testing before moving to core PyMC
- Breaking changes possible between versions

Benefits:
- Access to cutting-edge methods
- Contribute to development through testing
- Preview future PyMC features
- Research applications requiring newest methods

Caution:
- Less documentation than main PyMC
- APIs may change
- Use main PyMC for production applications
- Good for research and experimentation
-->

---
layout: center
---

# Community & Learning Resources

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4">📚 Learning</div>
    <ul class="text-lg space-y-2">
      <li>📖 <strong>pymc.io/learn</strong></li>
      <li>🎥 YouTube tutorials</li>
      <li>📓 Example gallery</li>
      <li>📚 "Bayesian Analysis with Python"</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4">💬 Community</div>
    <ul class="text-lg space-y-2">
      <li>🗣️ <strong>discourse.pymc.io</strong></li>
      <li>🦋 @pymc-devs.bsky.social</li>
      <li>💻 GitHub discussions</li>
      <li>🎪 PyData conferences</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-2xl text-blue-400">
    🤝 Welcoming community for all skill levels!
  </div>
</div>

<!--
The PyMC community is one of its greatest strengths:

Learning Resources:

Official Documentation:
- pymc.io/learn: comprehensive tutorials and guides
- API reference with examples
- Getting started guides for different backgrounds

Video Content:
- PyMC YouTube channel with tutorials
- Conference talks from PyData events
- Live coding sessions and workshops

Example Gallery:
- 100+ worked examples covering many domains
- Real datasets and complete workflows
- Best practices demonstrated
- Code you can copy and modify

Books:
- "Bayesian Analysis with Python" by Osvaldo Martin
- "Bayesian Methods for Machine Learning" by various authors
- Academic textbooks using PyMC

Community Support:

Discourse Forum (discourse.pymc.io):
- Primary place for questions and discussion
- Searchable archive of solved problems
- Core developers actively participate
- Beginner-friendly atmosphere

Social Media:
- @pymc-devs.bsky.social on Bluesky for updates
- LinkedIn PyMC community
- Reddit r/BayesianStatistics

The community motto: "No question is too basic!" Everyone was a beginner once.
-->

---
layout: top-title
---

:: title ::

# 📓 Finding PyMC Example Notebooks

:: content ::

<div class="grid grid-cols-2 gap-8 mt-6">
  <div>
    <div class="text-2xl mb-4 text-blue-400">🎯 Official Examples</div>
    <ul class="text-lg space-y-3">
      <li><strong>pymc.io/projects/examples</strong></li>
      <li>100+ worked examples</li>
      <li>Real datasets & complete workflows</li>
      <li>Organized by topic & difficulty</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4 text-green-400">🔍 How to Use Them</div>
    <ul class="text-lg space-y-3">
      <li>Start with similar problem types</li>
      <li>Copy & adapt the structure</li>
      <li>Focus on model specification</li>
      <li>Check diagnostic patterns</li>
    </ul>
  </div>
</div>

<div class="mt-8 bg-blue-50 p-6 rounded-lg">
  <div class="text-blue-800 font-bold mb-3 text-lg">💡 Pro Tips</div>
  <div class="text-base text-blue-700">
    • <strong>Browse by domain:</strong> Finance, Biology, Marketing, etc.<br>
    • <strong>Check the notebook dates:</strong> Newer examples use current best practices<br>
    • <strong>Run examples locally:</strong> Experiment with different data and parameters<br>
    • <strong>Read the explanations:</strong> Understanding why > copying code
  </div>
</div>

<!--
The PyMC example gallery is one of the best resources for learning:

Official Example Gallery:
- Located at pymc.io/projects/examples
- Over 100 worked examples covering many domains
- Each example includes complete workflow from data to interpretation
- Examples are organized by topic (regression, time series, etc.) and difficulty level
- All examples are Jupyter notebooks you can download and run

How to Use Examples Effectively:
1. Find examples similar to your problem domain
2. Don't just copy code - understand the model structure
3. Pay attention to prior choices and their justification
4. Look at diagnostic plots and interpretation
5. Adapt the structure to your specific data and questions

Categories Include:
- Generalized Linear Models
- Hierarchical/Multilevel Models
- Time Series Analysis
- Gaussian Processes
- Causal Inference
- Survival Analysis
- And many more specialized topics

The examples are maintained by the PyMC team and community contributors, so they represent current best practices and working code.
-->

---
layout: top-title
---


:: title ::

# Getting Help & Contributing

:: content ::

<div class="grid grid-cols-2 gap-8 mt-6">
  <div class="bg-blue-50 p-6 rounded-lg">
    <div class="text-blue-800 text-xl mb-4">🆘 Need Help?</div>
    <ul class="text-blue-700 text-base space-y-2">
      <li>✅ Search discourse.pymc.io first</li>
      <li>✅ Include minimal working example</li>
      <li>✅ Share error messages and diagnostics</li>
      <li>✅ Describe what you've tried</li>
    </ul>
  </div>
  <div class="bg-green-50 p-6 rounded-lg">
    <div class="text-green-800 text-xl mb-4">🤝 Want to Contribute?</div>
    <ul class="text-green-700 text-base space-y-2">
      <li>📝 Documentation improvements</li>
      <li>🐛 Bug reports with examples</li>
      <li>💡 Feature suggestions</li>
      <li>🧪 Testing experimental features</li>
    </ul>
  </div>
</div>

<!--
How to get help effectively:

Before Asking:
- Search discourse.pymc.io - your question may already be answered
- Check the documentation and examples
- Try to create a minimal working example

When Asking for Help:
- Include a complete, runnable code example
- Share the full error message (not just "it doesn't work")
- Include your PyMC and Python versions
- Describe what you expected vs what happened
- Show diagnostic plots if relevant

Good Question Example:
```python
import pymc as pm
# minimal data and model code
# error message
# "I expected X but got Y"
```

Ways to Contribute:

Documentation:
- Fix typos and unclear explanations
- Add examples for under-documented features
- Improve tutorials for beginners
- Translate documentation

Bug Reports:
- Include minimal reproducing examples
- Check if already reported on GitHub
- Help developers understand the issue

Feature Requests:
- Describe the use case clearly
- Check if similar functionality exists
- Be willing to help test implementations

Testing:
- Try experimental features and report issues
- Validate examples on different platforms
- Help with pre-release testing

Every contribution, no matter how small, is valued by the community!
-->

---
layout: section
color: purple-light
---

# 🚀 Future Directions

Where PyMC is heading

<!--
Let's look at where PyMC and Bayesian modeling are heading in the next few years.

The field is evolving rapidly, with new developments in:
- Computational performance improvements
- New statistical methods and applications
- Easier interfaces for domain experts

Understanding these trends will help you stay current and make good decisions about when and how to adopt new tools.
-->

---
layout: center
---

# 🧠 Inference Improvements

- **Variational inference** modernization for faster, more stable VI
- **Pathfinder**: JAX compatibility and robust NUTS initialization
- **Normalizing flows** for richer variational families
- **Zarr-backed sampling**: resumable runs and compatibility across samplers
- **Superchains**: cross-run diagnostics (with ArviZ support)

<div class="mt-6 text-center text-lg text-gray-500">
  Goal: make inference faster, more reliable, and easier to scale
</div>

---
layout: center
---

# 🧩 User Experience Priorities

- Smarter **automation** and defaults for newcomers
- **pip install improvements** (uv) to make setup simple and reliable
- **Warm starts** to resume or iterate sampling seamlessly

<div class="mt-6 text-center text-lg text-gray-500">
  Goal: reduce friction from install → first model → iteration
</div>


---
layout: center
---

# 🧱 Computational Backends

- Choose a **better default backend**: easier to install and more performant
- **Automatic hardware detection** to inform backend selection

<div class="mt-6 text-center text-lg text-gray-500">
  Goal: “just works” defaults across CPU/GPU/Apple Silicon
</div>

---
layout: center
---

# 🫶 Community & Process

- Permanent **office hours** and broader outreach (incl. academia)
- Clearer **funding pathways** to sustain development
- **Enhancement proposals** (like NumPy/pandas NEPs) and regular roadmap reviews

<div class="mt-6 text-center text-lg text-gray-500">
  Goal: a healthy, transparent, and well‑supported community
</div>

---
layout: credits
class: text-center
---

# Questions? 🤔

<br>

<div class="grid grid-cols-3 gap-8 text-lg">
  <div>
    <div class="text-3xl mb-2">💬</div>
    <div>discourse.pymc.io</div>
  </div>
  <div>
    <div class="text-3xl mb-2">📚</div>
    <div>pymc.io</div>
  </div>
  <div>
    <div class="text-3xl mb-2">🦋</div>
    <div>@pymc-devs.bsky.social</div>
  </div>
</div>

<div class="text-2xl mt-8 mb-8">
  Thank you for your interest in PyMC!
</div>

<div class="flex justify-center items-center mt-4">
  <img src="/4-pymc-labs-transp-black.png" alt="PyMC Labs" class="h-16 opacity-80">
</div>

<!--
Thank you for joining this comprehensive introduction to PyMC!

Quick recap of what we covered:
- What PyMC is and why Bayesian modeling matters
- Installation and setup (easier than you might think!)
- Core concepts: models, distributions, observed data
- Complete worked example with real data and diagnostics
- Common pitfalls and how to avoid them
- The broader ecosystem and community resources
- Future directions and opportunities to contribute

Key takeaways:
1. Bayesian modeling gives you uncertainty quantification for free
2. PyMC makes complex statistical modeling accessible
3. Always check your diagnostics before trusting results
4. The community is welcoming and supportive
5. Start simple and add complexity gradually

Next steps:
- Try the bioassay example yourself
- Apply PyMC to your own data
- Join the discourse forum for support
- Explore the example gallery for inspiration

Resources for continued learning:
- discourse.pymc.io: get help and see discussions
- pymc.io: official documentation and tutorials
- @pymc-devs.bsky.social: stay updated on new developments

Remember: every expert was once a beginner. Don't hesitate to ask questions and engage with the community!

Happy Bayesian modeling! 🎉
-->
