Ahh got it! You want to **split the number and the unit into two separate columns** — like:

| A (Original) | B (Number) | C (Unit) |
|--------------|------------|----------|
| 101.2gb      | 101.2      | gb       |
| 500b         | 500        | b        |
| 965kb        | 965        | kb       |
| 314.2mb      | 314.2      | mb       |

### ✅ Do this in Google Sheets:

Assume your original data is in column **A**, starting at A1.

**In column B** (Number):
```excel
=REGEXEXTRACT(A1, "^[0-9.]+")
```

**In column C** (Unit):
```excel
=REGEXEXTRACT(A1, "[a-zA-Z]+$")
```

This will neatly split the number and the unit into two columns.

Let me know if you'd like to convert those units to a standard form (like all to MB or GB)!





























--------------------------------------------------------------------------



























Nice! Now you're leveling up 😎 — let’s convert everything in **Column B (Number)** to **GB**, based on the unit in **Column C**.

---

### 🧮 Assumptions
You now have:

| A (Original) | B (Number) | C (Unit) |
|--------------|------------|----------|
| 101.2gb      | 101.2      | gb       |
| 500b         | 500        | b        |
| 965kb        | 965        | kb       |
| 314.2mb      | 314.2      | mb       |

You want to put the converted value in **Column D**, all in **GB**.

---

### ✅ Formula for Column D:
In **D1**, use:

```excel
=IF(C1="gb", B1, IF(C1="mb", B1/1024, IF(C1="kb", B1/1024/1024, IF(C1="b", B1/1024/1024/1024, "Unknown Unit"))))
```

---

### 💡 Explanation:
- `gb` → same
- `mb` → divide by 1024
- `kb` → divide by 1024×1024
- `b`  → divide by 1024×1024×1024
- Anything else = `"Unknown Unit"`

---

### ✅ Output Example:

| B (Number) | C (Unit) | D (Value in GB) |
|------------|----------|-----------------|
| 101.2      | gb       | 101.2           |
| 500        | b        | 4.66E-07        |
| 965        | kb       | 0.000920296     |
| 314.2      | mb       | 0.30625         |

Want to round it or format nicely (like 3 decimal places)? Just wrap it:

```excel
=ROUND(IF(C1="gb", B1, IF(C1="mb", B1/1024, IF(C1="kb", B1/1024/1024, IF(C1="b", B1/1024/1024/1024, "Unknown Unit")))), 3)
```

Let me know if you want to go the other way (GB to MB, etc.) too.
