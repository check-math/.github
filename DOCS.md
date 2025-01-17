## **1. Introduction**

The system allows users to compare two values **automatically generated by the system**. Users only need to input a comparison operator (`<`, `>`, or `=`) to determine the relationship between the two generated values.

---

## **2. System Workflow**

### **2.1 Input**

- The user provides a comparison operator (`<`, `>`, or `=`).  
  Examples:
    - `<`
    - `>`
    - `=`

---

### **2.2 System Processing**

1. **Generate arithmetic values**:
    - The system automatically generates **two arithmetic expressions** or **two integers** to compare.
    - Expressions are created based on the complexity level (which can be pre-configured):
        - **Easy (ez):** Generates simple integers (e.g., `100` and `102`).
        - **Normal:** Generates basic expressions with operations (`+`, `-`, `*`, `/`).
        - **Hard:** Creates more complex expressions involving multiple operators, negative numbers, or large multiplications/divisions.

2. **Perform comparison**:
    - Evaluates the values of the two integers or expressions.
    - Compares the values based on the operator provided by the user.

3. **Evaluate results**:
    - Returns **"True"** if the comparison is correct.
    - Returns **"False"** if the comparison is incorrect.

---

### **2.3 Output**

The system outputs the following:

- The two generated numbers or expressions.
- The comparison result.

**Examples:**

1. User input: `<`
    - Generated: `100 ? 102`
    - Result: `100 < 102 => True`
2. User input: `>`
    - Generated: `999 + 13 ? 435 + 299`
    - Result: `1012 > 734 => True`
3. User input: `=`
    - Generated: `99/3 + 30 ? 23x4 - 20`
    - Result: `33 + 30 = 92 => False`

---

## **3. Technical Details**

### **3.1 Automatic Value Generation**

The system generates two values based on three difficulty levels:

- **Easy (ez):**
    - Generates two random integers within the range `[1, 1000]`.
    - Example: `100`, `102`.
- **Normal:**
    - Generates expressions with basic operations `+`, `-`, `*`, `/`.
    - Example: `999 + 13`, `435 + 299`.
- **Hard:**
    - Generates complex expressions involving multiple operators, negative numbers, or larger computations.
    - Example: `99/3 + 30`, `23x4 - 20`.

---

### **3.2 Input Validation**

1. Reads the comparison operator provided by the user (`<`, `>`, `=`).
2. Validates the operator:
    - If invalid, returns an error: **"Invalid operator. Please enter `<`, `>`, or `=`."**

---

### **3.3 Value Computation**

- Generated expressions are evaluated using computation libraries (e.g., `eval()` in Python or JavaScript).
- Ensures compliance with mathematical order of operations (BODMAS/PEDMAS).

---

### **3.4 Comparison and Result Output**

- Compares the values of the two expressions.
- Outputs the result along with the computed values of the expressions.

---

## **4. Error Handling**

The system handles the following errors:

1. **Invalid operator**:
    - If the user inputs an invalid character that is not `<`, `>`, or `=`.  
      **Example**: `?` → **"Error: Invalid operator."**

2. **Arithmetic errors in generated expressions**:
    - Example: Division by zero in an expression.  
      **Handling**: Re-generate the expression or return an appropriate error message.

---

## **5. Examples**

| **Input** | **Generated Expressions** | **Result**           |
|-----------|----------------------------|-----------------------|
| `<`       | `50 ? 100`                 | `50 < 100 => True`    |
| `>`       | `45 + 5 ? 20 * 2`          | `50 > 40 => True`     |
| `=`       | `10*3 + 10 ? 20 + 20`      | `40 = 40 => True`     |
| `<`       | `99/3 + 20 ? 30 + 30`      | `53 < 60 => True`     |
| `>`       | `15*5 ? 12*6`              | `75 > 72 => True`     |
| `=`       | `100 ? 100`                | `100 = 100 => True`   |

---

## **6. Potential Extensions**

- Add functionality for users to set the difficulty level (`ez`, `normal`, `hard`).
- Provide a RESTful API for generating and validating mathematical comparisons for external applications.
- Develop a user-friendly interface for quizzes and tests.