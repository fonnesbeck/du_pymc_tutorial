---
theme: neversink
title: Getting Started with PyMC v5
info: |
  ## Getting Started with PyMC v5
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

# Getting Started with PyMC v5

<div class="text-4xl mb-4">
  🐍 + 📊 + 🧠 = PyMC
</div>

<div class="text-2xl">
  Data Umbrella Tutorial
</div>

<div class="text-xl mt-8">
  Christopher Fonnesbeck<br>
  <span class="text-lg">PyMC Labs</span>
</div>

<!--
Welcome to this comprehensive 1-hour tutorial on PyMC v5!

Today we'll cover:
- What PyMC is and why you should use it
- How to install and set up PyMC
- The fundamentals of probabilistic programming
- Building your first Bayesian model with real data
- Diagnosing and interpreting results
- Common pitfalls and how to avoid them
- The broader PyMC ecosystem

By the end, you'll have hands-on experience with Bayesian modeling and know how to build, fit, and diagnose your own models.
-->

---
layout: intro
---

# 🎯 What We'll Learn Today

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-4xl mb-4">🧠</div>
    <div class="text-xl mb-2">Bayesian Thinking</div>
    <div class="text-sm text-gray-600">Understanding uncertainty and probabilistic models</div>
  </div>
  <div>
    <div class="text-4xl mb-4">🔧</div>
    <div class="text-xl mb-2">Practical Skills</div>
    <div class="text-sm text-gray-600">Building and diagnosing real models</div>
  </div>
  <div>
    <div class="text-4xl mb-4">📊</div>
    <div class="text-xl mb-2">Data Analysis</div>
    <div class="text-sm text-gray-600">Working with real-world examples</div>
  </div>
  <div>
    <div class="text-4xl mb-4">🚀</div>
    <div class="text-xl mb-2">Best Practices</div>
    <div class="text-sm text-gray-600">Avoiding common pitfalls</div>
  </div>
</div>

<!--
This tutorial is designed to be practical and hands-on. We'll start with the basics but quickly move to real examples.

The four key areas we'll focus on:

1. Bayesian Thinking: Understanding how to think in terms of uncertainty, priors, and updating beliefs with data.

2. Practical Skills: You'll learn to write PyMC code, run MCMC samplers, and interpret results.

3. Data Analysis: We'll work with actual datasets and solve real problems, not just toy examples.

4. Best Practices: I'll share common mistakes I see in the field and how to avoid them.

This isn't just about learning PyMC syntax - it's about becoming a better data scientist who can handle uncertainty properly.
-->

---
layout: center
---

# What is PyMC?

<div class="text-6xl mb-8 mt-16">
  🐍 + 📊 + 🧠 = PyMC
</div>

<div class="text-2xl text-gray-600">
  Python + Statistics + Probabilistic Thinking
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
layout: center
---

# Why Bayesian Modeling?

<div class="grid grid-cols-2 gap-12 mt-8">
  <div>
    <div class="text-4xl mb-4">📈</div>
    <div class="text-2xl mb-4">Traditional Approach</div>
    <div class="text-lg">
      <ul>
        <li>Point estimates</li>
        <li>p-values</li>
        <li>Confidence intervals*</li>
        <li>Null hypothesis testing</li>
      </ul>
    </div>
  </div>
  <div>
    <div class="text-4xl mb-4">🎯</div>
    <div class="text-2xl mb-4">Bayesian Approach</div>
    <div class="text-lg">
      <ul>
        <li>Full distributions</li>
        <li>Probability statements</li>
        <li>Credible intervals</li>
        <li>Direct inference</li>
      </ul>
    </div>
  </div>
</div>

<!--
The Bayesian approach is fundamentally more intuitive and informative:

Traditional Statistics:
- Gives you point estimates with error bars
- p-values are confusing (what's the probability that the null hypothesis is true? NOT what p-values tell you!)
- Confidence intervals have a weird interpretation: "If we repeated this study 100 times, 95% of the confidence intervals would contain the true value"
- Focuses on rejecting null hypotheses rather than quantifying effects

Bayesian Statistics:
- Gives you the full distribution of possible parameter values
- You can make direct probability statements: "There's a 95% chance the effect is between X and Y"
- Credible intervals have the intuitive interpretation you want
- You can incorporate prior knowledge naturally
- You get uncertainty quantification for free

The Bayesian approach answers the questions you actually want to ask about your data.
-->

---
layout: default
---

# Real-World Applications

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4 text-blue-400">🏥 Healthcare</div>
    <ul class="text-sm space-y-2">
      <li>Clinical trial design</li>
      <li>Drug dosing optimization</li>
      <li>Epidemiological modeling</li>
      <li>Diagnostic test evaluation</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4 text-green-400">💰 Finance</div>
    <ul class="text-sm space-y-2">
      <li>Risk modeling</li>
      <li>Portfolio optimization</li>
      <li>Credit scoring</li>
      <li>Market forecasting</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4 text-purple-400">🧬 Science</div>
    <ul class="text-sm space-y-2">
      <li>Parameter estimation</li>
      <li>Model comparison</li>
      <li>Experimental design</li>
      <li>Meta-analysis</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4 text-orange-400">📱 Tech</div>
    <ul class="text-sm space-y-2">
      <li>A/B testing</li>
      <li>Recommendation systems</li>
      <li>Anomaly detection</li>
      <li>User behavior modeling</li>
    </ul>
  </div>
</div>

<!--
PyMC is used across many industries because uncertainty is everywhere:

Healthcare:
- Clinical trials need to account for patient variability
- Drug dosing must be personalized based on patient characteristics
- Epidemiological models help track disease spread with uncertainty
- Diagnostic tests have false positive/negative rates that need proper handling

Finance:
- Risk models must quantify uncertainty in potential losses
- Portfolio optimization needs to account for parameter uncertainty
- Credit scoring benefits from hierarchical models for different populations
- Market forecasting explicitly acknowledges we don't know the future

Science:
- Parameter estimation with proper uncertainty quantification
- Model comparison using information criteria and cross-validation
- Experimental design optimizes information gain
- Meta-analysis combines evidence from multiple studies

Technology:
- A/B testing with proper statistical inference
- Recommendation systems that adapt to user preferences
- Anomaly detection that adapts to changing baselines
- User behavior models that capture individual differences

The common thread: all these applications involve uncertainty that needs to be properly quantified and propagated.
-->


---
layout: section
---

# 📦 Installation & Setup

<div class="text-4xl mt-8">
  Let's get you up and running!
</div>

<!--
Before we dive into modeling, let's make sure everyone has PyMC properly installed and configured.

There are a few different ways to install PyMC, and the choice depends on your setup and needs. I'll show you the recommended approaches and help you troubleshoot common issues.

Don't worry if you run into problems - PyMC has some complex dependencies, and installation issues are common. We'll work through them together.
-->

---
layout: center
---

# 🚀 Recommended Installation

<div class="text-4xl mb-8 font-mono">
  conda install -c conda-forge pymc
</div>

<div class="text-lg text-gray-500 mb-8">
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
layout: two-cols
---

# Sampling Backends & Libraries

<div class="grid grid-cols-2 gap-4 text-sm">

<div class="bg-green-100 p-3 rounded">
  <div class="text-lg font-bold text-green-800 mb-2">🔧 PyTensor (Default)</div>
  <div class="text-green-700">
    • CPU-based, most stable<br>
    • Works everywhere<br>
    • All PyMC features supported
  </div>
</div>

<div class="bg-blue-100 p-3 rounded">
  <div class="text-lg font-bold text-blue-800 mb-2">⚡ JAX + NumPyro</div>
  <div class="text-blue-700">
    • GPU/TPU acceleration<br>
    • <code>conda install numpyro</code><br>
    • Some limitations
  </div>
</div>

<div class="bg-purple-100 p-3 rounded">
  <div class="text-lg font-bold text-purple-800 mb-2">🚀 Nutpie</div>
  <div class="text-purple-700">
    • Rust + Numba performance<br>
    • <code>conda install -c conda-forge nutpie</code><br>
    • CPU-optimized NUTS
  </div>
</div>

<div class="bg-orange-100 p-3 rounded">
  <div class="text-lg font-bold text-orange-800 mb-2">⚫ BlackJAX</div>
  <div class="text-orange-700">
    • JAX-based samplers<br>
    • <code>conda install blackjax</code><br>
    • Advanced MCMC methods
  </div>
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
   - GPU and TPU acceleration
   - Install: conda install numpyro
   - 5-10x faster for large models
   - JIT compilation for speed
   - Some PyMC features may have limitations

3. Nutpie (Fast CPU sampling):
   - Rust-based NUTS implementation with Numba
   - Install: conda install -c conda-forge nutpie
   - Optimized for CPU performance
   - Faster than default PyTensor for many models

4. BlackJAX (Advanced JAX samplers):
   - JAX-based sampling library
   - Install: conda install blackjax
   - Advanced MCMC algorithms
   - Useful for research and specialized sampling

For this tutorial, we'll use the default PyTensor backend since it works reliably for everyone and handles all our examples perfectly.

You can explore faster backends later when working with larger, more complex models.
-->

---
layout: center
---

# ✅ Test Your Installation

```python {all|1-2|4-5|7-8}
import pymc as pm
print(f"PyMC version: {pm.__version__}")

import arviz as az
print(f"ArviZ version: {az.__version__}")

# Quick test
x = pm.Normal.dist(mu=0, sigma=1)
print(f"Test sample: {pm.draw(x, draws=3)}")
```

<div v-click class="text-2xl mt-8 text-green-500">
  🎉 If this runs, you're ready!
</div>

<StickyNote color="green" class="mt-4">
💡 <strong>Pro Tip:</strong> The first run might be slow due to compilation, but subsequent runs will be much faster!
</StickyNote>

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
layout: center
---

# 🛠️ Development Setup

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-blue-50 p-6 rounded-lg">
    <div class="text-2xl mb-3">📓 Jupyter Notebooks</div>
    <div class="text-lg mb-4 text-blue-900">Recommended for learning</div>
    <div class="text-sm space-y-2 text-blue-800">
      <div>✅ Interactive exploration</div>
      <div>✅ Immediate plot display</div>
      <div>✅ Great for tutorials</div>
    </div>
  </div>
  <div class="bg-green-50 p-6 rounded-lg">
    <div class="text-2xl mb-3">🆚 VS Code + Jupyter</div>
    <div class="text-lg mb-4 text-green-900">Best of both worlds</div>
    <div class="text-sm space-y-2 text-green-800">
      <div>✅ Code completion</div>
      <div>✅ Git integration</div>
      <div>✅ Notebook support</div>
    </div>
  </div>
</div>

<!--
For Bayesian modeling, your development environment matters:

Jupyter Notebooks:
- Perfect for exploratory data analysis
- Interactive plots work seamlessly
- Easy to iterate on models
- Great for sharing results
- ArviZ plots display beautifully
- Recommended for learning PyMC

VS Code:
- Better for production code
- Excellent debugging capabilities
- Smart code completion for PyMC
- Integrated version control
- Can run notebooks natively
- Better for larger projects

Other good options:
- PyCharm: Great IDE features, good for complex projects
- Google Colab: Free GPU access, good for large models
- Spyder: Popular in scientific computing

For this tutorial, either Jupyter or VS Code will work great. Choose what you're most comfortable with.

Pro tip: Start with Jupyter for exploration, then move to VS Code when you want to turn your analysis into reusable code.
-->

---
layout: center
---

# 🔧 Troubleshooting Common Issues

<Admonition type="warning" title="Most Common Issue">
The g++ compiler warning on Windows causes 10-100x performance degradation! Install `m2w64-toolchain` to fix this.
</Admonition>

<div class="grid grid-cols-2 gap-8 mt-4">
  <div class="bg-red-50 p-4 rounded">
    <div class="text-red-700 font-bold mb-2">💥 Import Errors</div>
    <div class="text-sm text-red-600">
      pip install --upgrade pymc arviz<br>
      conda update -c conda-forge pymc
    </div>
  </div>
  <div class="bg-yellow-50 p-4 rounded">
    <div class="text-yellow-700 font-bold mb-2">⚠️ g++ Compiler Warning</div>
    <div class="text-sm text-yellow-600">
      <strong>Windows users:</strong><br>
      conda install m2w64-toolchain<br>
      Fixes severe performance degradation
    </div>
  </div>
  <div class="bg-blue-50 p-4 rounded">
    <div class="text-blue-700 font-bold mb-2">🖥️ Platform-Specific</div>
    <div class="text-sm text-blue-600">
      <strong>Mac M1/M2:</strong> Use conda-forge only<br>
      <strong>Linux:</strong> Generally smooth<br>
      <strong>Colab:</strong> May need runtime restart
    </div>
  </div>
  <div class="bg-green-50 p-4 rounded">
    <div class="text-green-700 font-bold mb-2">🔍 Need Help?</div>
    <div class="text-sm text-green-600">
      discourse.pymc.io<br>
      Friendly community support!
    </div>
  </div>
</div>

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
---

# 🧠 PyMC Fundamentals

<div class="text-4xl mt-8">
  The building blocks of Bayesian models
</div>

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
layout: center
---

# The Model Container

<div class="text-6xl mb-8">
  📦
</div>

```python {all|1|2-3|5-6}
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
layout: default
---

# Random Variables & Distributions

<div class="mt-8">

```python {all|1-2|4-5|7-8}
# Unobserved (parameters to estimate)
mu = pm.Normal("mu", mu=0, sigma=10)
sigma = pm.HalfNormal("sigma", sigma=1)

# Deterministic transformations
scaled_mu = pm.Deterministic("scaled_mu", mu * 2)

# Observed (your data)
y = pm.Normal("y", mu=mu, sigma=sigma, observed=data)
```

</div>

<!--
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

The key insight: you're building a generative model. You're saying "this is how I think the data was generated" and then inverting that process to learn about the parameters.
-->

---
layout: center
---

# Distribution Zoo 🦁

<img src="/plots/distributions/distribution_zoo.png" class="w-full max-w-3xl mx-auto mt-4">

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
layout: two-cols
---

# Observed Data

::left::

```python {all|1-2|4-5|6-7|8}
# Your actual data
data = np.array([1.2, 2.3, 1.8, 2.9, 3.1])

with pm.Model() as model:
    mu = pm.Normal("mu", mu=0, sigma=10)
    sigma = pm.HalfNormal("sigma", sigma=1)
    observations = pm.Normal("obs", mu=mu, 
                           sigma=sigma, observed=data)
```

::right::

<div class="mt-8">
  <div class="text-2xl mb-4">Key Points</div>
  <ul class="text-sm space-y-2">
    <li>🎯 <code>observed=data</code> makes it a likelihood</li>
    <li>📊 Data shape must match distribution</li>
    <li>🔗 Links parameters to your actual data</li>
    <li>⚡ This is where Bayes' theorem happens!</li>
  </ul>
</div>

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
layout: center
---

# 📊 Data Handling Pitfalls

<div class="grid grid-cols-2 gap-6 mt-8">
  <div class="bg-red-50 p-4 rounded">
    <div class="text-red-700 font-bold mb-2">❌ Pandas Inside Model</div>
    <div class="text-sm text-red-600">
      PyMC operates on tensors, not DataFrames!
    </div>
  </div>
  <div class="bg-green-50 p-4 rounded">
    <div class="text-green-700 font-bold mb-2">✅ Prepare Data First</div>
    <div class="text-sm text-green-600">
      Prepare data outside model context
    </div>
  </div>
</div>

```python
# ❌ Wrong: pandas operations inside model
with pm.Model():
    means = df.groupby('category').mean()  # This fails!

# ✅ Correct: prepare data first  
means = df.groupby('category').mean().values
with pm.Model():
    data = pm.Data("data", means)
```

<div class="mt-6 bg-blue-50 p-4 rounded">
  <div class="text-blue-800 font-bold mb-2">🔧 Key Patterns</div>
  <div class="text-sm text-blue-700">
    • Complete pandas operations <strong>outside</strong> model context<br>
    • Convert to numpy arrays before entering model<br>
    • Use <code>pm.Data()</code> for data that might change<br>
    • Use <code>pt.where()</code> for missing data (JAX/NumPyro compatible)
  </div>
</div>

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
layout: center
---

# The Bayesian Recipe

<div class="text-4xl mb-8">
  Prior × Likelihood = Posterior
</div>

```python {all|2-3|5-6|8}
with pm.Model() as model:
    # Prior: What we believe before seeing data
    mu = pm.Normal("mu", mu=0, sigma=10)
    
    # Likelihood: How we think data was generated
    y = pm.Normal("y", mu=mu, sigma=1, observed=data)
    
    # Posterior: Updated beliefs (computed by MCMC)
```

<!--
This is the heart of Bayesian statistics:

Prior:
- Your beliefs before seeing the data
- Can be informative (based on domain knowledge) or uninformative (letting data dominate)
- Example: mu ~ Normal(0, 10) says we think mu is probably near 0

Likelihood:
- Your model of how the data was generated
- Given parameters, what's the probability of observing your data?
- Example: y ~ Normal(mu, 1) says each observation comes from a normal distribution

Posterior:
- Your updated beliefs after seeing the data
- Combines prior knowledge with information from data
- This is what MCMC sampling gives you
- Automatically balances prior and likelihood based on data quality

Bayes' theorem: P(parameters | data) ∝ P(data | parameters) × P(parameters)

The beauty: everything is probabilistic, so you get full uncertainty quantification for free.
-->

---
layout: default
---

# PyMC ❤️ ArviZ Integration

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4">🎨 PyMC</div>
    <ul class="text-lg space-y-2">
      <li>Model specification</li>
      <li>MCMC sampling</li>
      <li>Prior/posterior predictive</li>
      <li>Model comparison</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4">📊 ArviZ</div>
    <ul class="text-lg space-y-2">
      <li>Visualization</li>
      <li>Diagnostics</li>
      <li>Model checking</li>
      <li>Summary statistics</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-lg text-gray-600">
    Seamless workflow: PyMC → InferenceData → ArviZ
  </div>
</div>

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
---

# 🏗️ Building Your First Model

<div class="text-4xl mt-8">
  From data to insights with real examples
</div>

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
layout: center
---

# 🧪 The Bioassay Problem

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4">The Question</div>
    <div class="text-lg">
      How does drug dose affect mortality in lab animals?
    </div>
  </div>
  <div>
    <div class="text-2xl mb-4">The Data</div>
    <div class="text-lg mt-4 space-y-2">
      <div><strong>Dose:</strong> [-0.86, -0.3, -0.05, 0.73]</div>
      <div><strong>Animals:</strong> [5, 5, 5, 5]</div>
      <div><strong>Deaths:</strong> [0, 1, 3, 5]</div>
    </div>
  </div>
</div>

<div class="mt-8 text-center text-lg text-gray-600">
  Classic dose-response modeling problem
</div>

<!--
This is a classic problem in toxicology and pharmacology:

The Setup:
- We have 4 different dose levels (on log scale, centered)
- 5 animals tested at each dose
- We count how many animals died at each dose
- Goal: model the dose-response relationship

Why this matters:
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
layout: default
---

# Building the Model

```python {all|1-4|6-7|9-10|11-12|14-15}
# The data
dose = np.array([-0.86, -0.3, -0.05, 0.73])
n_animals = np.array([5, 5, 5, 5])
n_deaths = np.array([0, 1, 3, 5])

with pm.Model() as bioassay_model:
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
layout: center
---

# ⚠️ Common Modeling Errors

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-red-50 p-4 rounded">
    <div class="text-red-700 font-bold mb-2">🔢 Shape Mismatches</div>
    <div class="text-sm text-red-600">
      <code>ValueError: Input dimension mis-match</code><br>
      Matrix vs element-wise operations<br>
      Explicit shape specification needed
    </div>
  </div>
  <div class="bg-orange-50 p-4 rounded">
    <div class="text-orange-700 font-bold mb-2">📊 Broadcasting Issues</div>
    <div class="text-sm text-orange-600">
      Mixing <code>shape</code> and <code>dims</code><br>
      Inconsistent coordinate systems<br>
      Check tensor shapes explicitly
    </div>
  </div>
</div>

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
layout: center
---

# Prior Predictive Check

<img src="/plots/bioassay/prior_predictive.png" class="w-full max-w-3xl mx-auto">

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
layout: center
---

# Sampling the Posterior

```python {all|1-2|4-5}
with bioassay_model:
    trace = pm.sample(2000, tune=1000, chains=4, random_seed=42)

# PyMC automatically:
# ✓ Chose NUTS sampler    ✓ Tuned parameters
# ✓ Ran 4 parallel chains ✓ Checked convergence
```

<div class="text-2xl mt-8 text-center">
  ⚡ Modern MCMC is (mostly) automatic! ⚡
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
layout: center
---

# Trace Plots: Checking Convergence

<img src="/plots/bioassay/trace_plot.png" class="w-full max-w-3xl mx-auto">

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
layout: center
---

# Posterior Distributions

<img src="/plots/bioassay/posterior_plot.png" class="w-full max-w-3xl mx-auto">

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
layout: default
---

# Parameter Relationships

<div class="flex flex-col items-center justify-center h-full">
<img src="/plots/bioassay/pair_plot.png" class="w-full max-w-3xl mx-auto">
</div>

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
layout: center
---

# Model Summary

```python
az.summary(trace, var_names=['alpha', 'beta'])
```

```
        mean     sd  hdi_3%  hdi_97%  mcse_mean  mcse_sd  ess_bulk  ess_tail  r_hat
alpha  0.241  0.634  -0.985    1.430      0.010    0.008    4266.0    4089.0    1.0
beta   4.034  1.447   1.532    6.869      0.022    0.018    5094.0    4724.0    1.0
```

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
layout: center
---

# Posterior Predictive Check

<img src="/plots/bioassay/posterior_predictive.png" class="w-full max-w-3xl mx-auto">

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
layout: center
---

# Making Predictions

```python {all|1-2|4-5|7-8}
# Predict mortality at new doses
new_doses = np.array([-1.0, 0.0, 1.0])

with bioassay_model:
    pm.set_data({'dose': new_doses})
    posterior_pred = pm.sample_posterior_predictive(trace)

# Get prediction intervals
pred_mortality = posterior_pred.posterior_predictive['deaths']
```

<div class="text-2xl mt-8 text-center">
  🔮 Full uncertainty quantification for free!
</div>

<!--
One of the biggest advantages of Bayesian modeling - making predictions with uncertainty:

The Process:
1. Define new dose values we want predictions for
2. Use pm.set_data() to update the model with new doses (requires dose to be defined with pm.Data)
3. Sample from posterior predictive distribution
4. Get full distribution of possible outcomes

What we get:
- Not just point predictions, but full distributions
- Credible intervals for mortality rates
- Probability of any specific outcome
- Proper uncertainty propagation from parameter uncertainty

Example interpretations:
- "At dose -1.0, we predict 0-2 deaths out of 5 animals with 95% probability"
- "At dose 1.0, we predict 4-5 deaths out of 5 animals with 95% probability"
- "The median predicted mortality at dose 0.0 is 60%"

Compared to classical approaches:
- Classical: point prediction ± standard error
- Bayesian: full predictive distribution
- Can answer any question: "What's the probability that fewer than 2 animals die?"

This uncertainty quantification is crucial for decision-making in pharmaceutical and toxicology applications.
-->

---
layout: section
---

# ⚠️ Common Pitfalls & Solutions

<div class="text-4xl mt-8">
  Avoiding the traps that catch beginners
</div>

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
layout: center
---

# Convergence Diagnostics

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="text-center">
    <div class="text-4xl mb-4">📈</div>
    <div class="text-2xl mb-2">R-hat < 1.01</div>
    <div class="text-lg text-gray-600">Chains have converged</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-4">📊</div>
    <div class="text-2xl mb-2">ESS > 400</div>
    <div class="text-lg text-gray-600">Enough effective samples</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-4">⚠️</div>
    <div class="text-2xl mb-2">Zero Divergences</div>
    <div class="text-lg text-gray-600">No numerical issues</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-4">🔗</div>
    <div class="text-2xl mb-2">Good Mixing</div>
    <div class="text-lg text-gray-600">Fuzzy caterpillars in traces</div>
  </div>
</div>

<!--
Always check these four diagnostics before trusting your results:

R-hat (Potential Scale Reduction Factor):
- Compares within-chain vs between-chain variance
- Should be < 1.01 for all parameters
- > 1.01 means chains haven't converged to the same distribution
- Much > 1.1 is a serious problem

Effective Sample Size (ESS):
- How many independent samples you effectively have
- Accounts for autocorrelation in MCMC chains
- Need ESS > 400 for basic inference, > 1000 is better
- Low ESS means high autocorrelation (slow mixing)

Divergences:
- Numerical instabilities during sampling
- Even a few divergences can bias results
- Often indicate problems with model specification or geometry
- Zero divergences is the goal

Chain Mixing:
- Visual inspection of trace plots
- Should look like "fuzzy caterpillars" - random noise around a mean
- All chains should explore the same space
- Patterns, trends, or stuck chains indicate problems

If any of these fail, don't interpret your results! Fix the underlying issue first.
-->

---
layout: center
---

# The Dreaded Divergences 💥

<div class="bg-red-50 p-6 rounded-lg mt-8">
  <div class="text-red-800 text-xl mb-4">
    "There were 47 divergences after tuning..."
  </div>
  
  <div class="text-red-700">
    <div class="text-lg mb-4">What this means:</div>
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
layout: two-cols
---

# Diagnosing Sampling Problems

::left::

<div class="text-2xl mb-4">🚨 "Bad Initial Energy"</div>

```python
# First: diagnose the problem
with model:
    model.check_test_point()
    
# Shows which variables have infinite log-prob
# Common fixes:
pm.sample(init='adapt_diag')
pm.sample(init='jitter+adapt_diag')

# Or find reasonable starting point
with model:
    start = pm.find_MAP()  # Use sparingly
    trace = pm.sample(start=start)
```

::right::

<div class="text-2xl mb-4">⚡ Divergence Solutions</div>

```python
# Step 1: More conservative sampling
pm.sample(target_accept=0.95, tune=2000)

# Step 2: Model reparameterization  
# Non-centered for hierarchical models
theta_raw = pm.Normal('theta_raw', 0, 1)
theta = pm.Deterministic('theta', mu + tau * theta_raw)

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
layout: center
---

# Performance Optimization

<div class="grid grid-cols-3 gap-6 mt-8">
  <div class="text-center">
    <div class="text-4xl mb-2">🚀</div>
    <div class="text-xl mb-2">JAX Backend</div>
    <div class="text-sm text-gray-600">5-10x speedup for many models</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">📊</div>
    <div class="text-xl mb-2">Vectorization</div>
    <div class="text-sm text-gray-600">Avoid loops, use tensor operations</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">🎯</div>
    <div class="text-xl mb-2">Simpler Models</div>
    <div class="text-sm text-gray-600">Start simple, add complexity gradually</div>
  </div>
</div>

<div class="mt-8">

```python
# Switch to JAX backend for speed
import pymc as pm
pm.set_backend('jax')

# Or install numpyro for even more speed
pip install numpyro
```

</div>

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
layout: center
---

# Prior Specification Problems

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-red-50 p-4 rounded">
    <div class="text-red-700 font-bold mb-2">❌ Wrong Constraints</div>
    <div class="text-sm text-red-600 font-mono">
      # Allows negative values!
      sigma = pm.Normal('sigma', 0, 5)
    </div>
    <div class="text-sm text-red-600 mt-2">
      → "Bad initial energy" errors<br>
      → Impossible likelihoods
    </div>
  </div>
  <div class="bg-green-50 p-4 rounded">
    <div class="text-green-700 font-bold mb-2">✅ Proper Constraints</div>
    <div class="text-sm text-green-600 font-mono">
      # Ensures positive values
      sigma = pm.HalfNormal('sigma', 5)
    </div>
    <div class="text-sm text-green-600 mt-2">
      → Stable sampling<br>
      → Reasonable constraint
    </div>
  </div>
</div>

<div class="mt-6 bg-blue-50 p-4 rounded">
  <div class="text-blue-800 font-bold mb-2">🎯 Golden Rules</div>
  <div class="text-sm text-blue-700">
    • <strong>Standard deviations:</strong> HalfNormal, not Normal<br>
    • <strong>Probabilities:</strong> Beta(2,2), not Uniform(0,1)<br>
    • <strong>Coefficients:</strong> Normal(0, 2.5) for standardized data<br>
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
layout: center
---

# Debugging Workflow

<div class="text-2xl mb-8">When things go wrong...</div>

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-xl mb-4">🔍 Diagnostic Steps</div>
    <ol class="text-sm space-y-2">
      <li>1. Check trace plots</li>
      <li>2. Look at R-hat values</li>
      <li>3. Check effective sample size</li>
      <li>4. Count divergences</li>
      <li>5. Do posterior predictive checks</li>
    </ol>
  </div>
  <div>
    <div class="text-xl mb-4">🛠️ Fix Strategy</div>
    <ol class="text-sm space-y-2">
      <li>1. Try sampler tuning first</li>
      <li>2. Examine prior predictive samples</li>
      <li>3. Simplify the model</li>
      <li>4. Reparameterize if needed</li>
      <li>5. Ask for help on discourse!</li>
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
layout: center
---

# 🤔 Conceptual Clarifications

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-yellow-50 p-4 rounded">
    <div class="text-yellow-700 font-bold mb-2">🗺️ find_MAP() Deprecation</div>
    <div class="text-sm text-yellow-600">
      <strong>Old tutorials say:</strong> Start with MAP<br>
      <strong>Modern practice:</strong> Just call pm.sample()<br>
      <strong>Why?</strong> MAP isn't representative in high dimensions
    </div>
  </div>
  <div class="bg-blue-50 p-4 rounded">
    <div class="text-blue-700 font-bold mb-2">🔢 PyMC3 vs PyMC</div>
    <div class="text-sm text-blue-600">
      <strong>PyMC3:</strong> Old name (legacy)<br>
      <strong>PyMC:</strong> Current name (v4+)<br>
      <strong>Migration:</strong> Most code works with minor changes
    </div>
  </div>
</div>

<div class="mt-6 bg-green-50 p-4 rounded">
  <div class="text-green-800 font-bold mb-2">📊 Prior vs Posterior Predictive</div>
  <div class="text-sm text-green-700">
    <strong>Prior predictive:</strong> Validate model assumptions <em>before</em> seeing data<br>
    <strong>Posterior predictive:</strong> Compare model predictions <em>after</em> fitting<br>
    <strong>Key:</strong> Use joint distributions, not marginals (parameters are correlated!)
  </div>
</div>

<!--
Conceptual confusions that persist even after technical issues are resolved:

find_MAP() Deprecation Confusion:
- Older tutorials and books recommend starting with MAP estimates
- find_MAP() was deprecated because MAP estimates aren't representative in high dimensions
- Modern practice: just call pm.sample() directly with good initialization strategies
- NUTS is robust enough to find good starting points automatically
- MAP can actually hinder NUTS sampling by starting in atypical regions

Version Confusion (PyMC3 vs PyMC):
- PyMC3 was renamed to PyMC starting with version 4
- Current PyMC (v5+) is the actively developed version
- Most PyMC3 code works with minor modifications
- Don't panic if you see "PyMC3" in old tutorials - concepts translate directly
- Check import statements: import pymc3 -> import pymc as pm

Prior vs Posterior Predictive Confusion:
- Prior predictive: sample from model before seeing data, validates assumptions
- Posterior predictive: sample from fitted model, compares to observed data  
- Both require joint distributions because parameters are typically correlated
- Common mistake: using marginal distributions instead of joint samples
- Prior predictive catches model specification errors early
- Posterior predictive validates model fit to actual data

These conceptual issues cause anxiety but are easily resolved with modern workflows.
-->

---
layout: center
---

# ArviZ: Your Visualization Partner

<div class="grid grid-cols-3 gap-6 mt-8">
  <div class="text-center">
    <div class="text-4xl mb-2">📊</div>
    <div class="text-xl mb-2">Trace Plots</div>
    <div class="text-sm">Check convergence</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">🎨</div>
    <div class="text-xl mb-2">Forest Plots</div>
    <div class="text-sm">Compare parameters</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">🔍</div>
    <div class="text-xl mb-2">Model Checking</div>
    <div class="text-sm">Validate assumptions</div>
  </div>
</div>

<img src="/plots/bioassay/forest_plot.png" class="w-full max-w-2xl mx-auto mt-8">

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
layout: center
---

# Bambi: High-Level Modeling

```python {all|1-2|4-5|7-8}
import bambi as bmb
import pandas as pd

# R-style formula interface
model = bmb.Model('y ~ x1 + x2 + (1|group)', data=df)

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
layout: center
---

# PyMC-Experimental: Cutting Edge

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4">🧪 New Methods</div>
    <ul class="text-lg space-y-2">
      <li>Variational inference</li>
      <li>Gaussian processes</li>
      <li>State space models</li>
      <li>Causal inference</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4">🚀 Experimental Features</div>
    <ul class="text-lg space-y-2">
      <li>New samplers</li>
      <li>Advanced diagnostics</li>
      <li>Model comparison</li>
      <li>Optimization tools</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-lg text-gray-600">
    💡 Features graduate to main PyMC when stable
  </div>
</div>

<!--
PyMC-experimental is where new features are developed and tested:

New Statistical Methods:
- Variational inference: faster approximate inference
- Gaussian processes: flexible non-parametric models
- State space models: time series with latent states
- Causal inference: experimental designs and effect estimation

Experimental Features:
- New MCMC samplers (beyond NUTS)
- Advanced diagnostics and model checking
- Information criteria and model comparison tools
- Optimization algorithms for MAP estimation

How It Works:
- Install: pip install pymc-experimental
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

This is where the future of PyMC is being built!
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
      <li>🐦 @pymc_devs</li>
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
- @pymc_devs on Twitter for updates
- LinkedIn PyMC community
- Reddit r/BayesianStatistics

The community motto: "No question is too basic!" Everyone was a beginner once.
-->

---
layout: center
---

# Getting Help & Contributing

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-blue-50 p-6 rounded">
    <div class="text-blue-800 text-xl mb-4">🆘 Need Help?</div>
    <ul class="text-blue-700 text-sm space-y-2">
      <li>✅ Search discourse.pymc.io first</li>
      <li>✅ Include minimal working example</li>
      <li>✅ Share error messages and diagnostics</li>
      <li>✅ Describe what you've tried</li>
    </ul>
  </div>
  <div class="bg-green-50 p-6 rounded">
    <div class="text-green-800 text-xl mb-4">🤝 Want to Contribute?</div>
    <ul class="text-green-700 text-sm space-y-2">
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
---

# 🚀 Future Directions

<div class="text-4xl mt-8">
  Where PyMC is heading
</div>

<!--
Let's look at where PyMC and Bayesian modeling are heading in the next few years.

The field is evolving rapidly, with new developments in:
- Integration with AI/ML workflows
- Computational performance improvements
- New statistical methods and applications
- Easier interfaces for domain experts

Understanding these trends will help you stay current and make good decisions about when and how to adopt new tools.
-->

---
layout: center
---

# 🤖 AI Integration

<div class="grid grid-cols-2 gap-12 mt-8">
  <div class="text-center">
    <div class="text-5xl mb-4">🧠</div>
    <div class="text-2xl">LLM-Assisted Modeling</div>
    <div class="text-lg mt-2 text-gray-600">Natural language → PyMC code</div>
  </div>
  <div class="text-center">
    <div class="text-5xl mb-4">⚡</div>
    <div class="text-2xl">Neural Approximations</div>
    <div class="text-lg mt-2 text-gray-600">Faster inference with neural networks</div>
  </div>
</div>

<div class="mt-8 text-center text-lg text-gray-500">
  "Build a hierarchical model for customer churn prediction"
</div>

<!--
AI is transforming how we build and use Bayesian models:

LLM-Assisted Modeling:
- Natural language descriptions → PyMC code
- Automatic model specification from data descriptions
- Interactive debugging and model improvement
- Democratizing Bayesian modeling for domain experts

Example workflow:
User: "I have sales data by region and want to account for seasonal effects"
AI: Generates hierarchical model with seasonal components in PyMC

Neural Approximations:
- Neural networks to approximate posterior distributions
- Much faster than MCMC for some problems
- Normalizing flows for complex posterior shapes
- Variational autoencoders for model comparison

Current Reality:
- Early stage but rapidly developing
- Some tools already available (GitHub Copilot helps with PyMC code)
- Integration with ChatGPT/Claude for model consultation
- Research active in neural posterior estimation

Future Vision:
- Conversational model building
- Automatic model criticism and improvement
- AI-assisted prior elicitation
- Seamless integration of domain knowledge

This could make Bayesian modeling accessible to many more scientists and analysts who understand their domain but not the technical details of MCMC.
-->

---
layout: center
---

# ⚡ Performance Revolution

<div class="grid grid-cols-3 gap-6 mt-8">
  <div class="text-center">
    <div class="text-4xl mb-2">🚀</div>
    <div class="text-xl mb-2">JAX Backend</div>
    <div class="text-sm text-gray-600">GPU acceleration</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">🔥</div>
    <div class="text-xl mb-2">Compilation</div>
    <div class="text-sm text-gray-600">JIT optimization</div>
  </div>
  <div class="text-center">
    <div class="text-4xl mb-2">📈</div>
    <div class="text-xl mb-2">Scalability</div>
    <div class="text-sm text-gray-600">Larger datasets</div>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-2xl">100x speedups possible for large models</div>
</div>

<!--
Performance improvements are making Bayesian modeling feasible for much larger problems:

JAX Backend:
- GPU/TPU acceleration for massive models
- Automatic differentiation optimized for modern hardware
- Vectorized operations across multiple devices
- Already 5-10x faster for many models

JIT Compilation:
- XLA compiler optimizes entire model graphs
- Eliminates Python overhead
- Aggressive optimization for repeated operations
- Cold start penalty but then much faster

Scalability Improvements:
- Handle millions of observations
- Thousands of parameters in hierarchical models
- Real-time inference for streaming data
- Distributed computation across clusters

Current Status:
- JAX backend already available and improving
- Some limitations vs NumPy backend
- Research into specialized hardware (TPUs)
- Integration with cloud computing platforms

Impact:
- Previously impossible models now feasible
- Real-time decision making with Bayesian uncertainty
- Large-scale A/B testing and experimentation
- Industrial applications with big data

This performance revolution is making Bayesian methods competitive with classical ML for large-scale applications.
-->

---
layout: center
---

# 🌍 Growing Applications

<div class="grid grid-cols-2 gap-8 mt-8">
  <div>
    <div class="text-2xl mb-4 text-purple-400">🔬 Science</div>
    <ul class="text-sm space-y-1">
      <li>Climate modeling</li>
      <li>Genomics & personalized medicine</li>
      <li>Astronomy & cosmology</li>
      <li>Social sciences</li>
    </ul>
  </div>
  <div>
    <div class="text-2xl mb-4 text-blue-400">🏢 Industry</div>
    <ul class="text-sm space-y-1">
      <li>Supply chain optimization</li>
      <li>Financial risk modeling</li>
      <li>Marketing mix modeling</li>
      <li>Quality control</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-lg text-gray-600">
    Uncertainty quantification becoming essential everywhere
  </div>
</div>

<!--
Bayesian methods are expanding into new domains:

Scientific Applications:
- Climate modeling: quantifying uncertainty in climate projections
- Genomics: personalized medicine with individual-level predictions
- Astronomy: discovering exoplanets and dark matter
- Social sciences: causal inference and policy evaluation

Industrial Applications:
- Supply chain: robust optimization under uncertainty
- Finance: regulatory compliance requires uncertainty quantification
- Marketing: attribution and media mix optimization
- Manufacturing: quality control and predictive maintenance

Why the Growth?
- Regulatory requirements for uncertainty quantification
- AI safety concerns driving need for calibrated confidence
- Better tools making Bayesian methods more accessible
- Recognition that point estimates are insufficient

Market Trends:
- Consulting firms building Bayesian practices
- Software companies integrating uncertainty quantification
- Academic programs emphasizing Bayesian statistics
- Industry standards requiring probabilistic forecasts

The future is probabilistic - organizations that embrace uncertainty quantification will have competitive advantages in decision-making under uncertainty.
-->

---
layout: center
---

# 🤝 How You Can Contribute

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="bg-blue-50 p-6 rounded">
    <div class="text-blue-800 text-xl mb-4">👩‍💻 Technical</div>
    <ul class="text-blue-700 text-sm space-y-2">
      <li>🐛 Report bugs with examples</li>
      <li>📚 Improve documentation</li>
      <li>🧪 Test experimental features</li>
      <li>💡 Contribute code improvements</li>
    </ul>
  </div>
  <div class="bg-green-50 p-6 rounded">
    <div class="text-green-800 text-xl mb-4">🌟 Community</div>
    <ul class="text-green-700 text-sm space-y-2">
      <li>❓ Answer questions on discourse</li>
      <li>✍️ Write tutorials and blog posts</li>
      <li>🎤 Give talks at meetups</li>
      <li>👥 Organize local user groups</li>
    </ul>
  </div>
</div>

<div class="mt-8 text-center">
  <div class="text-2xl text-orange-500">
    🚀 Join us in building the future of data science!
  </div>
</div>

<!--
The PyMC community thrives on contributions from users like you:

Technical Contributions:

Bug Reports:
- Include minimal reproducing examples
- Help developers understand and fix issues
- Make PyMC more reliable for everyone

Documentation:
- Fix typos and unclear explanations
- Add examples for complex features
- Improve tutorials for beginners
- Translate content to other languages

Testing:
- Try new features before release
- Report compatibility issues
- Help with cross-platform testing

Code:
- Fix bugs in your area of expertise
- Implement new features
- Optimize performance
- Add new distributions or samplers

Community Contributions:

Support:
- Answer questions on discourse.pymc.io
- Help newcomers get started
- Share your expertise

Content Creation:
- Write blog posts about your analyses
- Create video tutorials
- Share case studies from your domain
- Publish reproducible research

Outreach:
- Give talks at conferences and meetups
- Organize workshops at your institution
- Start local PyMC user groups
- Advocate for Bayesian methods in your field

Every contribution matters - the community values all forms of participation!
-->

---
layout: credits
class: text-center
---

# Questions? 🤔

<div class="text-2xl mt-8 mb-12">
  Thank you for joining this PyMC journey!
</div>

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
    <div class="text-3xl mb-2">🐦</div>
    <div>@pymc_devs</div>
  </div>
</div>

<div class="mt-12 text-gray-500">
  Slides: github.com/fonnesbeck/du_pymc_tutorial
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
- @pymc_devs: stay updated on new developments

Remember: every expert was once a beginner. Don't hesitate to ask questions and engage with the community!

Happy Bayesian modeling! 🎉
-->