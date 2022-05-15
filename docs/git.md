# GIT

---

## Installation

```sh
sudo apt-get update
sudo apt-get install git
```

## Set remote origin with token

```sh
git remote set-url origin https://<githubtoken>@github.com/<username>/<repositoryname>.git
```

## Extremely basic commands:

Add new files and files with changes, on prepare to the commit

```sh
git add .
```

If the files added are not the corrects, always it is posible to reset the `add`:

```sh
git reset
```

If all the files included in the `add` command are correct, the you can commit all the changes:

```sh
git commit -m "<very important commentary about the code change>"
```

Once you commit the change in your PC you can upload the change to Github or Gitlab:
```sh
git push origin <mvery important origin>
```

Always it is recomendable to make a pull before starting coding. You can do that with the `pull` command:
```sh
git pull origin <very important origin>
```