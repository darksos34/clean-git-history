# Clean Git History

## 🛡️ Step 1: Backup

```bash
# Create backup branch
git branch backup-now

# Clone to backup directory
git clone . ../backup
```

## ↩️ Step 2: Undo Commits

```bash
# Undo last commit (keep changes staged)
git reset --soft HEAD~1

# Undo last commit (unstage changes)
git reset HEAD~1

# Undo last commit (delete everything)
git reset --hard HEAD~1
```

## 🔄 Step 3: Restore

```bash
# View recent actions
git reflog

# Restore from backup branch
git reset --hard backup-now

# Or undo last action
git reset --hard HEAD@{1}
```

---

## Quick Reference

```bash
# Backup
git branch backup-now && git clone . ../backup

# Undo last commit
git reset --soft HEAD~1    # Keep changes
git reset HEAD~1           # Unstage
git reset --hard HEAD~1    # Delete

# Restore
git reset --hard backup-now
git reset --hard HEAD@{1}
```

---

## Database Config

```yaml
# application.yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/clean_git_history
    username: postgres
    password: ${DB_PASSWORD:postgres}
```

Set password:
```bash
export DB_PASSWORD="your_password"
```

