# Valid Parentheses Checker 🧩

A simple and efficient **bracket validation algorithm** built in C++ using the Stack data structure. This project checks if a given string of parentheses is valid by ensuring that every opening bracket has a matching closing bracket in the correct order.

---

## 🛠️ Tech Stack

- **C++** – Language used for algorithm implementation.
- **STL Stack** – Used for tracking open brackets efficiently.
- **Time Complexity** – O(n) for linear traversal and validation.

---

## 📸 Features

- ✅ Checks for correct nesting of `()`, `{}`, and `[]`.
- ❌ Returns false for mismatched or unbalanced brackets.
- ⚡ Handles up to 10,000 characters efficiently.
- 🔍 Uses a helper function to keep logic modular and clean.

---

## ▶️ How to Use

1. Copy the `Solution` class into your C++ file.
2. Call the `isValid(string s)` method with a bracket string.
3. Returns `true` if valid, `false` otherwise.

```cpp
Solution sol;
bool result = sol.isValid("()[]{}"); // returns true
```

---

👨‍💻 Author  
Prit Vadodaria  
Student at Birla Vishvakarma Mahavidyalaya  
GitHub | LinkedIn