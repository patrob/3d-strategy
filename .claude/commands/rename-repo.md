# Repository Rename: RPI Strategy → 3D Strategy

## Goal
Rename the GitHub repository from `rpi-strategy` to `3d-strategy` and update all local references.

## Prerequisites
- Ensure you have `gh` CLI installed and authenticated
- Ensure you have push access to the repository
- Current repository: `patrob/rpi-strategy`
- Current local remote: `git@github.com-personal:patrob/rpi-strategy.git`

## Atomic Steps

### Step 1: Rename Repository on GitHub
```bash
gh repo edit patrob/rpi-strategy --name 3d-strategy
```
**Expected Result:** Repository will be renamed to `patrob/3d-strategy` on GitHub

### Step 2: Update Local Git Remote URL
```bash
git remote set-url origin git@github.com-personal:patrob/3d-strategy.git
```
**Expected Result:** Local git remote points to new repository URL

### Step 3: Verify Remote Update
```bash
git remote -v
```
**Expected Output:**
```
origin	git@github.com-personal:patrob/3d-strategy.git (fetch)
origin	git@github.com-personal:patrob/3d-strategy.git (push)
```

### Step 4: Test Connection
```bash
git fetch origin
```
**Expected Result:** Successfully fetches from the renamed repository

### Step 5: Push Any Pending Changes (Optional)
```bash
git push origin main
```
**Expected Result:** Successfully pushes to the renamed repository

## Verification Checklist
- [ ] GitHub repository shows new name `3d-strategy`
- [ ] Local git remote points to new URL
- [ ] `git fetch` works without errors
- [ ] `git push` works without errors
- [ ] Repository is accessible at `https://github.com/patrob/3d-strategy`

## Notes
- GitHub automatically creates redirects from the old repository URL
- The redirect will work for clone operations for a limited time
- Any bookmarks or external references should eventually be updated to the new URL
- The SSH key configuration (`github.com-personal`) remains unchanged

## Rollback (if needed)
If something goes wrong, you can rename back:
```bash
gh repo edit patrob/3d-strategy --name rpi-strategy
git remote set-url origin git@github.com-personal:patrob/rpi-strategy.git
```

## Complete!
Once these steps are completed, the repository will be fully transitioned from "RPI Strategy" to "3D Strategy" both in content and naming.