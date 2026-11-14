# UnvibeCode PR Brief (prototype)

Turns an UnvibeCode review into one short comment on a pull request:
workflows touched, files to review first, and a low/medium/high label.

Prototype only. It is not an official UnvibeCode tool.

## Try it
1. `python -m unvibecode review --repository <repo> --output out`
2. `python pr_brief.py --results out/<analysis-folder> --changed src/a.py src/b.py`

## What it uses
- `connections.jsonl` (from the results ZIP): who imports whom
- `business-workflows.html`: which workflow references which file

## Known limits
- The risk label is a simple rule (dependents + 3 x workflows touched), not a security verdict.
- Links come from UnvibeCode's map, so wrong links in the map show up here too
  (for example it listed `tests/conftest.py` as a dependency of `src/flask/helpers.py`).
- The GitHub Action file is untested on GitHub. It reviews the PR branch only, with no base-branch cache yet.
- Python standard library only.
