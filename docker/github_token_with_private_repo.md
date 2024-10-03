# Github token with private repo
================================

**Author**: Lien Chen  **Date**: 2021-03-22

Usually using git command's clone, pull. You may need to input account name and password.
But in docker, you may need to enter into container to input password.

Now, there is a better way to clone, pull the repo.
Replace `https://github.com/` to `https://${GITHUB_TOKEN}@github.com/`. It still work perfect.

[reference](https://gist.github.com/zoellner/940fa8845e1331a841d9aef3e5c361aa)