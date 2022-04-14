This is the PittNAIL website hosted via [GitHub Pages](https://pages.github.com/) and generated
using [Zola](https://www.getzola.org/).

Run the command below to build and deploy it locally:

```console
zola build && zola serve
```

## Workflow

1. Edit the files in `content`, under the specific folder.
2. Run `zola build` after making the changes.
3. Push the changes.
4. Move the generated `public` folder to the directory outside the repository.
5. `git checkout` the `main` branch and remove all the files (except the `.git` folder).
6. Copy the contents from the generated `public` folder to the `main` branch.
