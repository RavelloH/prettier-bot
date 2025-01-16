# prettier-bot
Auto run "prettier --write ." for your repo.

# How to use
create a file in `.github/workflows/[the_name_of_your_file].yml`:

```yml
on: [push]

jobs:
  prettier:
    runs-on: ubuntu-latest
    name: prettier-bot
    steps:
      - uses: actions/checkout@v3
      - name: Tree
        uses: RavelloH/prettier-bot@latest
      - name: commit
        continue-on-error: True
        run: |
          git init
          git pull
          git config --local user.email "actions@github.com"
          git config --local user.name "github-actions"
          git add .
          git commit -m "[Prettier-bot]`date '+%Y-%m-%d %H:%M:%S'`" || exit
          git status
          git push -f
```

And you can change the username and email to yours.
