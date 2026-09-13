# Git Branch Switching — 4 Important Cases

## Case 1 — Modified Tracked File + Target Has Same File

```text
main → test3.txt = "hello from main" ✅ committed
test → test3.txt = "hello from test" ✅ committed

On main:
test3.txt → modified ❗ (not committed)

git switch test
```

❌ **ERROR**

```text
Your local changes to the following files would be overwritten by checkout:
    test3.txt
```

**Why?**
Switching would overwrite your uncommitted changes.

---

## Case 2 — Untracked File + Target Does NOT Have It

```text
main → new.txt ❗ untracked
test → new.txt does not exist
```

```bash
git switch test
```

✅ **NO ERROR**

`new.txt` remains in the working directory.

**Why?**
The file is untracked and switching does not need to overwrite it.

---

## Case 3 — Untracked File + Target Has Same File

```text
main → new.txt ❗ untracked
test → new.txt ✅ committed
```

```bash
git switch test
```

❌ **ERROR**

```text
The following untracked working tree files would be overwritten by checkout:
    new.txt
```

**Why?**
The target branch would overwrite your untracked file.

---

## Case 4 — Committed File + No Local Changes

```text
main → test3.txt = "hello from main" ✅ committed
test → test3.txt = "hello from test" ✅ committed

On main:
test3.txt → NOT modified
```

```bash
git switch test
```

✅ **NO ERROR**

Git changes the file:

```text
hello from main
       ↓
hello from test
```

**Why?**
Your current version is already committed, so Git can safely replace it.

---


