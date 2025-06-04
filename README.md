# Approximate Bayesian Computation (ABC) for SIR Model Parameter Estimation

This repository contains a Python implementation of Approximate Bayesian Computation (ABC) applied to the SIR (Susceptible-Infectious-Recovered) epidemiological model. The goal is to infer the transmission rate (`β`) and the recovery rate (`α`) from observed infection data using ABC rejection sampling.

## 📁 Files

- `ABC_Code_Implementation.ipynb`: Main Jupyter notebook containing the full implementation.
- `data.csv`: Input file containing infection data (columns: `Days`, `Infected`).

## 🧮 Method

This project uses the ABC rejection algorithm to estimate the parameters of the SIR model. The steps are:

1. Define prior distributions for `α` and `β` (uniform on [0,1]).
2. Simulate the SIR model using sampled parameter pairs.
3. Compute a distance metric between observed and simulated infected counts.
4. Accept parameter samples with distance below a predefined threshold `ε`.
5. Repeat until a desired number of accepted samples `M` is obtained.

## 🧾 Model

The SIR model is defined as:

$$
\frac{dS}{dt} = -\beta S I, \quad \frac{dI}{dt} = \beta S I - \alpha I, \quad \frac{dR}{dt} = \alpha I
$$

Where:
- `S(t)`: Number of susceptible individuals at time `t`
- `I(t)`: Number of infected individuals at time `t`
- `R(t)`: Number of recovered individuals at time `t`

The system is solved numerically using `scipy.integrate.odeint`.

## 📊 Requirements

- `numpy`
- `pandas`
- `matplotlib`
- `scipy`

Install dependencies with:

```bash
pip install numpy pandas matplotlib scipy
```

## 🚀 How to Run

1. Place the `data.csv` file in the same directory as the notebook.
2. Open the Jupyter notebook and run all cells sequentially.
3. The notebook will display posterior distributions of `α` and `β`, along with simulation fits.

## ⚙️ Parameters

- `M`: Number of accepted samples (e.g., 1000)
- `ε`: Tolerance threshold for acceptance (e.g., Euclidean distance ≤ 20)
- Initial population conditions (S₀, I₀, R₀) and total population `N`
- Time range: Must match the data length

## 📈 Output

- Histograms of posterior distributions for `α` and `β`
- Simulated infection curves using accepted parameters
- Acceptance rate diagnostics

## 📝 Notes

- Uniform priors U(0,1) are used for both parameters.
- You can tune the `ε` value for stricter or looser acceptance criteria.
- The code assumes `data.csv` has no missing values.

## 📚 References

- Maia Martcheva, *An Introduction to Mathematical Epidemiology*, 2015.

## 🧑‍💻 Author

This implementation was written for educational purposes in parameter estimation using ABC techniques.

---
```ABC_Code_Implementation.ipynb``` is best viewed in a Jupyter environment.
