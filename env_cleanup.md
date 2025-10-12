# 🧹 How to Remove a Leaked `.env` File from Git History (GitHub Safe Cleanup)

If your `.env` file was accidentally pushed to a remote repository, follow this guide to remove it from version control, clean the history and prevent future leaks.

---

## ⚙️ Step-by-Step Guide

### ✅ 1. Stop Tracking the `.env` File

```bash
git rm --cached .env
```

This removes the file from Git tracking **without deleting it locally**.

---

### 🛡️ 2. Add `.env` to `.gitignore`

```bash
echo ".env" >> .gitignore
```

This ensures the `.env` file won’t be tracked again in future commits.

---

### 💾 3. Commit and Push the Changes

```bash
git add .gitignore
git commit -m "Remove .env from tracking and add to .gitignore"
git push origin main
```

Replace `main` with your branch name if different.

---

## 🧹 4. Clean Up Commit History

Depending on how recently the `.env` was committed, choose one of the following cleanup options:

---

### 🔹 Option A — Remove the Last Commit Only

If the `.env` was added in your **most recent commit**, run:

```bash
git reset --soft HEAD~1
git restore --staged .env
echo ".env" >> .gitignore
git commit -m "Remove .env from tracking"
git push origin main --force
```

🧠 This rewrites only the last commit. Safe if the leak was caught early.

---

### 🔹 Option B — Remove `.env` from the Entire History

If the `.env` was added **long ago**, use `git-filter-repo` to completely purge it:

```bash
# Install git-filter-repo if not installed
pip install git-filter-repo

# Remove all traces of the .env file
git filter-repo --path .env --invert-paths

# Force push the cleaned history
git push origin --force
```

⚠️ Warning: This **rewrites the entire history**.  
All collaborators will need to re-clone the repository.

---

## 🔒 5. Revoke Exposed Credentials

If the `.env` contained sensitive data (API keys, tokens, secrets):
- Regenerate **all compromised credentials**.
- Update your local `.env` with the new values.
- Never commit `.env` files again — use secure storage instead.

---

## 💡 Security Tips

- Always include `.env` in your `.gitignore` from project initialization.
- For secret management in CI/CD, use:
  - **AWS Secrets Manager**
  - **Google Secret Manager**
  - **HashiCorp Vault**
  - **GitHub Actions Encrypted Secrets**

---

## ✅ Summary

| Step | Action | Command |
|------|---------|----------|
| 1 | Untrack file | `git rm --cached .env` |
| 2 | Ignore file | `echo ".env" >> .gitignore` |
| 3 | Commit | `git commit -m "remove .env"` |
| 4 | Push changes | `git push origin main` |
| 5 | Clean history (optional) | `git reset --soft HEAD~1` or `git filter-repo ...` |
| 6 | Revoke keys | — regenerate all leaked secrets |

---

> 🧠 **Best Practice:**  
> Keep your `.env` local and use secret managers for production environments.

---

### 🧩 Example: Secure CI/CD Integration (GitHub Actions)

```yaml
env:
  DATABASE_URL: ${{ secrets.DATABASE_URL }}
  STRIPE_API_KEY: ${{ secrets.STRIPE_API_KEY }}
```

Your application reads these secrets securely — **without committing them** to the repo.

---

🛡️ **Stay Safe — Protect Your Secrets, Always!**

----

[Environment File Explanation](env_explanation.md) <- `Back`

[Home](README.md) <-