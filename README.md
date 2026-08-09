# Nand2Tetris
# 📓 Computer Architecture Notes

## Topic 1: Signals, Boolean Values, and High/Low Voltages

### 1. Core Definitions

- **Signal:** An electrical voltage passing through a wire that carries information.
- **Bit (Binary Digit):** The smallest unit of data in computing, which can store either a `0` or a `1`.
- **Boolean Value:** A logical value that can only be either `True` (`1`) or `False` (`0`).
- **Boolean Logic:** A system of mathematical rules for processing `0`s and `1`s (named after George Boole).
- **Truth Table:** A visual chart that maps every possible input combination to its corresponding output.

### 2. Physical Electronics vs. Boolean States

| **Physical State** | **Electrical Level** | **Boolean Value** | **Digital State** |
| --- | --- | --- | --- |
| Current Flowing / On | HIGH Voltage (e.g., ~5V) | `True` | **`1`** |
| No Current / Off | LOW Voltage (0V) | `False` | **`0`** |

### 3. Key Concepts & Principles

1. **Why Binary?**
    - Physical hardware components (transistors, switches) operate with high reliability when distinguishing strictly between **ON** and **OFF**.
    - Multi-level systems (e.g., 0–9 voltage levels) suffer from electrical noise, component degradation, and ambiguity.
2. **Input Combinations Rule ($2^n$ Formula):**
    - For any circuit with $n$ binary inputs, the total number of possible input combinations is given by:
        
        $$\text{Total Combinations} = 2^n$$
        
    - **Examples:**
        - $1\text{ input} \rightarrow 2^1 = 2\text{ rows}$ (`0`, `1`)
        - $2\text{ inputs} \rightarrow 2^2 = 4\text{ rows}$ (`00`, `01`, `10`, `11`)
        - $3\text{ inputs} \rightarrow 2^3 = 8\text{ rows}$ (`000`, `001`, `010`, `011`, `100`, `101`, `110`, `111`)

### 4. Visual Reference: Truth Table Structure

A standard truth table format for a single-input system (e.g., a door sensor alarm):

| **Input (A)** | **Output (Y)** | **Meaning** |
| --- | --- | --- |
| `0` | `0` | Door Closed $\rightarrow$ Alarm Silent |
| `1` | `1` | Door Open $\rightarrow$ Alarm Rings |

### 5. Common Pitfalls & Exam Tips

- ❌ **Pitfall:** Thinking `0` means an "error" or "nothing."
    - **Fact:** `0` is a valid piece of information meaning `False` or `OFF`.
- ❌ **Pitfall:** Confusing binary `1` with "1 Volt."
    - **Fact:** `1` represents a "HIGH voltage state," regardless of whether the physical circuit uses 5V, 3.3V, or 1.8V.
- 💡 **Exam Tip:** When drawing truth tables, always count your rows using $2^n$ to ensure you haven't missed any input combination.

### 6. Quick Summary

- Electricity in a computer is simplified into two discrete states: **HIGH (`1`)** and **LOW (`0`)**.
- **Boolean Logic** allows us to build complex computer decisions using simple ON/OFF signals.
- **Truth Tables** list all input possibilities and their resulting outputs.

---

## Topic 2: Elementary Logic Gates (NOT, AND, OR)

### 1. Core Definitions

- **Logic Gate:** An electronic component that performs a basic logical operation on one or more binary inputs to produce a single binary output.
- **NOT Gate (Inverter):** A single-input logic gate that reverses (flips) the input signal.
- **AND Gate:** A logic gate that outputs `1` **only if all** of its inputs are `1`.
- **OR Gate:** A logic gate that outputs `1` if **at least one** of its inputs is `1`.

### 2. Logic Gate Summary & Truth Tables

### A. NOT Gate

- **Inputs:** 1
- **Boolean Expression:** `NOT A = Ā`
- **Rule:** Flips `0` to `1` and `1` to `0`.

| Input (A) | Output (Ā) |
| --- | --- |
| `0` | **`1`** |
| `1` | **`0`** |

---

### B. AND Gate

- **Inputs:** 2 or more
- **Boolean Expression:** `A AND B = A · B`
- **Rule:** Requires **unanimity**. The output is `1` **only when all inputs are `1`**.

| Input (A) | Input (B) | Output (A · B) |
| --- | --- | --- |
| `0` | `0` | `0` |
| `0` | `1` | `0` |
| `1` | `0` | `0` |
| `1` | `1` | **`1`** |

> **Easy way to remember:** AND = **Everyone must say YES.**
> 

---

### C. OR Gate

- **Inputs:** 2 or more
- **Boolean Expression:** `A OR B = A + B`
- **Rule:** The output is `1` if **at least one input is `1`**.

| Input (A) | Input (B) | Output (A + B) |
| --- | --- | --- |
| `0` | `0` | **`0`** |
| `0` | `1` | `1` |
| `1` | `0` | `1` |
| `1` | `1` | `1` |

> **Easy way to remember:** OR = **Anyone can say YES.**
> 

---

## 2. Boolean Algebra Analogies

Boolean algebra uses symbols similar to normal mathematics, but the rules are different.

### AND → Multiplication (`·`)

| Operation | Result |
| --- | --- |
| `0 · 0` | `0` |
| `0 · 1` | `0` |
| `1 · 0` | `0` |
| `1 · 1` | `1` |

Therefore:

```
A · B
```

represents an **AND** operation.

---

### OR → Addition (`+`)

| Operation | Result |
| --- | --- |
| `0 + 0` | `0` |
| `0 + 1` | `1` |
| `1 + 0` | `1` |
| `1 + 1` | `1` |

> **Important:** In Boolean algebra, `1 + 1 = 1`, not `2`.
> 

This is because Boolean values can only be:

```
0 or 1
```

Therefore:

```
1 + 1 = 1
```

in Boolean logic.

---

## 3. Key Rules & Properties

### 3.1 Double Negation Law

Applying NOT twice gives the original value:

```
NOT(NOT(A)) = A
```

Or:

```
Ā̄ = A
```

### Example

If:

```
A = 1
```

After the first NOT:

```
NOT(1) = 0
```

After the second NOT:

```
NOT(0) = 1
```

Therefore:

```
NOT(NOT(1)) = 1
```

> **Remember:** Two NOT gates in series cancel each other out.
> 

---

## 4. AND vs OR

The easiest way to distinguish AND and OR is to remember their conditions for producing `1` or `0`.

### AND Gate

AND outputs `1` **only when all inputs are `1`**.

```
A AND B = 1
```

only when:

```
A = 1 AND B = 1
```

Otherwise:

```
Output = 0
```

### OR Gate

OR outputs `0` **only when all inputs are `0`**.

```
A OR B = 0
```

only when:

```
A = 0 AND B = 0
```

Otherwise:

```
Output = 1
```

### Quick Comparison

| Gate | Output `1` when... | Output `0` when... |
| --- | --- | --- |
| **AND** | All inputs are `1` | At least one input is `0` |
| **OR** | At least one input is `1` | All inputs are `0` |
| **NOT** | Input is `0` | Input is `1` |

---

## 5. Common Pitfalls & Exam Tips

### ❌ Pitfall 1: Confusing OR with XOR

Standard **OR** is an **inclusive OR**.

This means:

```
1 OR 1 = 1
```

So the truth table is:

| A | B | OR |
| --- | --- | --- |
| `0` | `0` | `0` |
| `0` | `1` | `1` |
| `1` | `0` | `1` |
| `1` | `1` | **`1`** |

> **XOR** is different: XOR outputs `1` only when the inputs are different.
> 

---

### 💡 Exam Tip: Solve from the Inside Out

For complex Boolean expressions, evaluate the innermost operation first.

For example:

```
NOT(A AND B)
```

First calculate:

```
A AND B
```

Then apply:

```
NOT
```

### Example

If:

```
A = 1
B = 0
```

Then:

```
A AND B = 1 · 0 = 0
```

Now apply NOT:

```
NOT(0) = 1
```

Therefore:

```
NOT(A AND B) = 1
```

---

## 6. Quick Revision Summary

### NOT

```
NOT(0) = 1
NOT(1) = 0
```

### AND

```
A AND B = 1
```

**only when:**

```
A = 1 AND B = 1
```

### OR

```
A OR B = 0
```

**only when:**

```
A = 0 AND B = 0
```

### Most Important Rules

```
NOT(NOT(A)) = A

A · B  → AND

A + B  → OR

1 + 1 = 1   (Boolean algebra)
```

---

## 7. One-Minute Revision

> **NOT** → Flip it
> 
> 
> **AND** → Everyone must be `1`
> 
> **OR** → Anyone can be `1`
> 

```
AND → 1 only if ALL are 1
OR  → 0 only if ALL are 0
NOT → Flips the input
```