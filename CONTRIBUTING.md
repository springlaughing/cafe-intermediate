# Contributing

This project uses a simple branching model: `main` is the only permanent
branch. All work happens on short-lived branches that start from `main` and
merge back into `main` by pull request. Reading this top to bottom should be
enough to make your first change correctly.

---

## Branches

| Branch | Purpose |
|---|---|
| `main` | The only permanent branch. Always in a working state. |
| `feature/<description>` | One piece of work. Branch from `main`, merge into `main`, delete after. |

`<description>` is two or three words in **kebab-case** — lowercase, hyphens
instead of spaces:

- ✅ `feature/about-page`
- ❌ `feature/AboutPage`, `feature/add_the_about_page`

**Exception:** the merge-conflict drill uses `text-change-A` and
`text-change-B`, named as the lab specifies.

---

## Commits

Format:

    <type>(<scope>): <subject>

Only `<type>` and `<subject>` are required.

### Type

| Type | Use when you... | Example |
|---|---|---|
| `feat` | add something a visitor can see | `feat: add bare about.html` |
| `fix` | correct broken behaviour or content | `fix: typo in contact` |
| `docs` | change documentation only | `docs: add contribution conventions` |
| `style` | change formatting only — indentation, whitespace | `style: reindent styles.css` |
| `chore` | change tooling, config, or housekeeping | `chore: project scaffold` |

`style` means **code formatting**, not CSS. A change to colours is `feat`.

### Scope

Optional. Names the area the change touches, in parentheses:

    feat(about): add bare about.html

Use one of these and only these:

| Scope | Covers |
|---|---|
| `about` | about.html |
| `contact` | contact.html |
| `home` | index.html |
| `styles` | styles.css |
| `config` | .gitignore, editor settings, tooling |

Omit it when a change spans several areas or the subject is already clear.
Adding a scope is fine — add it to this table in the same commit.

### Subject

1. **Write the subject as an instruction**, like a to-do item —
   `✅ add about page`, ❌ `added about page`, ❌ `adds about page`.
2. **Lowercase first letter.**
3. **No trailing period.**
4. **Under ~50 characters.**

---

## Pull requests

- Title follows the commit format: `feat: add about page`
- Every PR targets `main`
- Merge with a merge commit, not squash, so branches stay visible in
  `git log --graph`
- Delete the branch after merging

---

## Stash vs. commit

Stash when you need to switch branches for a few minutes and the work isn't
worth a commit yet. Commit to a temporary branch when the work will take longer
than a short interruption, or when you might want it on another machine — a
stash lives only on this computer and only in this repository.

## Rewriting history

`git reset --hard` and `git push --force` throw away commits. Use them only on
your own branch, before anyone else has pulled it. On `main` or any shared
branch, use `git revert` instead — it undoes a change with a new commit and
leaves history intact.

---

## Setup (once, after cloning)

```bash
git config commit.template .gitmessage
```

## First change, start to finish

```bash
git checkout main
git pull
git checkout -b feature/about-page
# ...edit files...
git add .
git commit -m "feat(about): add bare about.html"
git push -u origin feature/about-page
```

Then open a pull request on GitHub targeting `main`.