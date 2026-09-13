# 🔀 Git Merge — 3 Main Cases

> **Common Ancestor = the original version both branches started from.**

Assume the common ancestor is:

```text
test1.txt

hello
```

---

## 🟢 Case 1 — Only One Branch Changes

**Common Ancestor:**

```text
hello
```

**main:**

```text
hello
```

**test:**

```text
hi from test
```

```text
Original
   │
   ├── main → hello
   │
   └── test → hi from test
```

✅ **No conflict**

**Why?** Only `test` changed the file.

---

## 🟢 Case 2 — Both Change Different Parts

**Common Ancestor:**

```text
hello
welcome
```

**main:**

```text
hi from main
welcome
```

**test:**

```text
hello
welcome from test
```

```text
Original
   │
   ├── main → changes line 1
   │
   └── test → changes line 2
```

✅ **No conflict**

**Why?** Both changed different parts of the file.

---

## 🔴 Case 3 — Both Change the Same Part Differently

**Common Ancestor:**

```text
hello
```

**main:**

```text
hi from main
```

**test:**

```text
hi from test
```

```text
             hello
             /   \
            /     \
         main     test
           ↓        ↓
    hi from main  hi from test
```

❌ **Merge Conflict**

**Why?** Both branches changed the same original line differently.

---

# 🧠 Remember

| Case | Main           | Test                          | Result        |
| ---- | -------------- | ----------------------------- | ------------- |
| 1    | No change      | Changes                       | ✅ No conflict |
| 2    | Changes part A | Changes part B                | ✅ No conflict |
| 3    | Changes part A | Changes same part differently | ❌ Conflict    |

> **Git checks what BOTH branches changed compared to their common ancestor.**
