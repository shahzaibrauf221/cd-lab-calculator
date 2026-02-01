# Lab Part 2: Continuous Delivery (CD)

## Project Structure

```
cd-lab-calculator/
├── .github/
│   └── workflows/
│       ├── ci.yml          # CI Pipeline
│       ├── cd.yml          # CD Pipeline
│       └── staging.yml     # Staging Pipeline (Exercise 2)
├── src/
│   └── calculator.py
├── tests/
│   └── test_calculator.py
├── requirements.txt
└── README.md
```

## Step 1: Understanding the Trigger

Look at `cd.yml`. Notice it doesn't run on every push. It waits for a **Tag**.

## Step 2: Creating your first Release

1. Ensure your code is working and all tests pass.
2. Tag your code:

```bash
git tag v1.0
git push origin v1.0
```

3. Go to **Actions** tab - "Continuous Delivery" starts!
4. Check **Releases** in sidebar - v1.0 available!

## Step 3: The Safety Net

1. Break your code (change `return x + y` to `return x * 99`)
2. Try to ship broken version:

```bash
git add .
git commit -m "Attempting to ship broken code"
git tag v1.1
git push origin main
git push origin v1.1
```

3. CD pipeline fails at "Sanity Check"

## Exercises

- Exercise 1: Actor name in release notes ✅
- Exercise 2: Staging workflow ✅
- Exercise 3: Environment secrets (manual)
- Exercise 4: Rollback - release v1.2
- Exercise 5: requirements.txt in package ✅
