# 📘 Derivative & Integral Visualizer

An interactive Wolfram Language application for exploring mathematical functions, their derivatives, and integrals in both symbolic and numeric forms. This tool provides live visualizations and outputs for learners, educators, and anyone working with calculus-based computations.

## 📌 Overview

This dynamic application enables users to:
- Input any function of \( x \)
- Plot the original function
- Compute and visualize:
  - Derivatives of arbitrary order
  - Indefinite integrals (symbolic)
  - Definite integrals (numerical)
- Adjust input ranges and view symbolic results inline
- Interact in a structured GUI using `DynamicModule` components

## 🖥 Interface Breakdown

### 🔹 Function Input: `f(x)`

The function to be analyzed. Accepts any valid Wolfram Language expression involving the variable `x`.

Examples:
- `Sin[x]^2`
- `x^3 + 2 x`
- `Exp[-x^2]`

### 🔹 Mode Selection: `"Derivative"` or `"Integral"`

**Derivative Mode**:
- Computes and plots the \( n \)-th derivative
- User provides the derivative degree `n`
- Uses `FullSimplify[D[f, {x, n}]]` to symbolically compute
- Automatically updates the plot and symbolic formula

**Integral Mode**:
- Two integration modes:
  1. **Indefinite Integral** (default): Computes the symbolic integral using `FullSimplify[Integrate[f, x]]`. The result is shown below the plot and added as a dashed curve.
  2. **Definite Integral**: Activated by checking the “Use bounds” box. User inputs bounds `{a, b}`. The numeric integral is computed using `NIntegrate[Evaluate[f], {x, a, b}]`. The result is displayed but not plotted (as it's a scalar).

### 🔹 Degree Input (for Derivatives)

Only visible in Derivative mode. Accepts integers \( n \geq 0 \). The input is validated through the Apply button to prevent errors when the field is cleared or contains invalid content.

### 🔹 Use Bounds Checkbox (for Integrals)

Visible only when mode is set to Integral. When enabled, expects `{a, b}` bounds for definite integration. If not enabled, performs indefinite symbolic integration.

### 🔹 X-range and Y-range Inputs

These input fields define the domain and range of the plot:
- `x-range`: Required, e.g., `{-5, 5}`
- `y-range`: Optional, `Automatic` by default

If inputs are left empty or invalid, fallback defaults are applied to avoid crashing.

## 📈 Output Display

### 🔸 Plot

- Always displays the original function \( f(x) \)
- Overlays:
  - Derivative: Dashed line in derivative mode
  - Indefinite Integral: Dashed line in integral mode (symbolic only)
- Definite integrals are not plotted (since they're scalars)
- Includes labeled legends, grid lines, and axis frame
- Interactive range control via x/y inputs

### 🔸 Symbolic/Numeric Output

Below the graph, two expressions are displayed:
1. `f(x)` shown in `TraditionalForm`
2. The derivative or integral result:
   - Derivative (symbolic): `D[f, {x, n}]`
   - Indefinite integral (symbolic): `Integrate[f, x]`
   - Definite integral (numeric): Result of `NIntegrate[...]`

If the computation fails, it displays:
`— (cannot compute)`


## 🔧 Implementation Details

Built with:
- `DynamicModule` for scoped state management
- `InputField`, `PopupMenu`, and `Checkbox` for user interaction
- `D`, `Integrate`, `NIntegrate`, and `FullSimplify` for math
- `TraditionalForm` to format symbolic output nicely
- `Plot`, `Show`, and `PlotLegends` for layered graphing
- Defensive coding using `Quiet@Check[...]` for stability

## 🧪 Example Use Cases

| Function | Mode       | Bounds     | Output                            |
|----------|------------|------------|-----------------------------------|
| `x^3`    | Integral    | `{0, 2}`   | `4.` (numeric definite integral)  |
| `Sin[x]` | Integral    | (none)     | `-Cos[x]` (symbolic)              |
| `Tan[x]` | Derivative  | `n = 1`    | `Sec[x]^2`                        |
| `Exp[-x^2]` | Integral | `{0, 1}`   | `0.746824` (numeric)              |
| `1/x`    | Derivative  | `n = 1`    | `-1/x^2`                          |

## 💡 Tips

- Use `Pi` or `\[Pi]` instead of the Unicode character `π` when entering bounds.
- Always ensure bounds are numeric for definite integrals.
- When editing degree `n`, press **Apply** to confirm changes.
- Symbolic operations may fail for non-differentiable or discontinuous functions.

## 📦 Installation & Usage

### Requirements

- Wolfram Mathematica (version 12 or later recommended)
- Or Wolfram Cloud with full kernel access

### Instructions

1. Open a new Wolfram notebook or Wolfram Cloud notebook.
2. Paste in the provided Wolfram Language code.
3. Evaluate the cell with **Shift + Enter**.
4. Use the visual UI to input functions and interact.

## 📜 License

This tool is free for **personal, educational, and non-commercial use**. Attribution is appreciated but not required. Customize and expand it for your own learning tools or demonstrations.

## 👤 Author

Created by **Aras Artenoğlu**, using the Wolfram Language for intuitive mathematical visualization. Designed for clarity, control, and learning.

## 🧩 Planned Enhancements

- Export symbolic output as LaTeX
- Shade area under curve for definite integrals
- Add sliders for interactive bounds and derivative degree
- Allow saving plots and expressions to PDF or notebook

