## `figs` directory

This is where input figures for the manuscript are stored

This directory also contains a `.gitignore`, for two reasons:
- You don't want to commit most figures since they can be quite voluminous, tend to have many versions and can be quickly generated using the R scripts in `/R/`. Only commit figures which require manual editing.
- The directory could not exist in the remote repository if it was empty

## Content of the `.gitignore`
```
# Ignore everything in this directory
*
# Except this file
!.gitignore
``` 