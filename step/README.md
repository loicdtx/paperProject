## Step directory

This directory is for storing intermediary output on their way to the `/latex/figs/` directory, such as figures that require manual editing.

The `.gitignore` is only there for the directory to existing in the remote repository. But you probably do not need to commit the files that pass through here.

Content of the `.gitignore`:
```
*
!.gitignore
```