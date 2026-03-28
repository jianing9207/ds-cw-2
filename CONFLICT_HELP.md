# Fixing GitHub merge conflict for `H00479060 DS CW2.ipynb`

If GitHub shows **"This branch has conflicts that must be resolved"**, do this locally (recommended for `.ipynb` files):

## 1) Get both branches locally
```bash
git fetch origin
```

## 2) Switch to your PR branch
```bash
git checkout <your-pr-branch>
```

## 3) Merge target branch (usually `main`)
```bash
git merge origin/main
```

## 4) For notebook conflicts, keep your latest notebook version
```bash
git checkout --ours "H00479060 DS CW2.ipynb"
# if you instead want target branch version, use --theirs
```

## 5) Mark resolved and commit
```bash
git add "H00479060 DS CW2.ipynb"
git commit -m "Resolve notebook merge conflict"
```

## 6) Push and refresh PR
```bash
git push origin <your-pr-branch>
```

---

## Quick decision guide
- You want to keep your newest coursework text/code: use `--ours`.
- You want to discard your branch notebook and keep target branch: use `--theirs`.

For coursework, `--ours` is usually correct if your notebook contains your latest final write-up.
