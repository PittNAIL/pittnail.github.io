This is the PittNAIL website hosted via [GitHub Pages][pages] and generated using [Zola][zola].

Run the command below to build and deploy it locally:

```console
zola build && zola serve
```

## Workflow

The workflow has been fully automated. One just needs to make changes in the `code` branch and the
rest will be handled by GitHub Actions workflow.

## Manual Workflow

1. Navigate to the `main` branch
2. Edit the files in `content`, under the specific folder.
3. Push the changes.
4. Run `zola build` after making the changes.
5. Move the generated `public` folder to the directory outside the repository.
6. `git checkout` the `gh-pages` branch and remove all the files (except the `.git` folder).
7. Copy the contents from the generated `public` folder to the `main` branch.

## Implementation

[Website][website] has been implemented by [David Oniani][david].

[pages]: https://pages.github.com/
[zola]: https://www.getzola.org/
[website]: https://github.com/pittnail/pittnail.github.io
[david]: https://oniani.ai
