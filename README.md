# Making with Code

Making with Code is a new, old approach to teaching computer science based in Constructionism. It’s new because it draws on the tools of modern computational practice and is grounded in youths’ digital worlds. It is old because technologists have been dreaming of an empowering, transformative integration of education and technology for over half a century.



## Set up 

1) Install Hugo: `brew install hugo`

2) Run a local server: `hugo server`
- in the current local branch, loads all files with `draft: false` 


## Branch Setup

- `production` - live site
- `dev` - proof version with year1 and year2 edits
- `year1` - edits for year 1 course
- `year2` - edits for year 2 course


### Example Workflow 

1) make edits to a lab in `year1`
1) use `hugo server` to check edits 
1) push edits to Github
1) switch to `dev` branch with `git checkout dev`
1) merge edits from `year1` with `git merge year1`
1) use `hugo server` to check edits 
1) push merge to `dev` 
1) switch to `production`
1) merge edits from `dev` with `git merge dev`
1) use `hugo server` to check edits 
1) push edits to Github to edit live site 

## Theme

[Amethyst Hugo Theme](https://github.com/64bitpandas/amethyst)


