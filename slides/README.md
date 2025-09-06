# Setting up slides in quarto and github
The following are few steps to setup your quarto slides in github pages.

## Edit and preview slides

### Dependencies
* quarto installation (See more: https://github.com/mxochicale/tools/tree/main/quarto)
```
wget https://raw.githubusercontent.com/mxochicale/tools/refs/heads/main/quarto/download_install_quart.bash
bash download_install_quart.bash
rm download_install_quart.bash
quarto check
```

### Quarto extensions?
```
quarto list extensions
quarto add parmsam/quarto-subtitles
quarto remove parmsam/subtitles
#https://github.com/parmsam/quarto-subtitles
```

### Edit and preview slices
* Open [index.qmd](index.qmd) to edit slides. 
* Then you can preview them:
```
cd slides
quarto preview index.qmd
```


## Creating scalfolding, ci workflows, code of conduct, contributions and slides
```
$ tree 
.
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└── slides
    ├── favicon.svg
    ├── figures
    │   ├── 00_template-vector-images
    │   │   └── drawing-v00.svg
    │   └── mx.svg
    ├── index.qmd
    └── README.md

3 directories, 9 files
```



## Commit and upload slides
* (1/3) first commit
```
git add .
git commit -m ':fire: 1st commit: adds scalfolding for slides #1'
git branch -M main
git push -u origin main
```

* (2/3) Create gh-pages branch
```
git checkout --orphan gh-pages 
#An orphan branch is not connected to the other branches and commits, and its working tree has no files at all. 
#See [here](https://git-scm.com/docs/git-checkout) for more info.
git reset --hard
git commit --allow-empty -m "Initializing gh-pages branch"
git push origin gh-pages
git checkout main
#https://jiafulow.github.io/blog/2020/07/09/create-gh-pages-branch-in-existing-repo/
```
See [hash for template](https://github.com/mxochicale/physical-ai-in-healthcare-slides/commit/74d43f86ec3fce761d0e92927c9fe8fbce7ac07f)


* (3/3) Goes to [PAGES](https://github.com/mxochicale/physical-ai-in-healthcare-slides/settings/pages) and select in the menu `Deploy from branch` and select gh-pages


### Push changes and publish slides
Github action to [publish-quarto.yml](https://github.com/mxochicale/physical-ai-in-healthcare-slides/blob/main/.github/workflows/publish-quarto.yml)
```bash
git add .
git commit -m '<add message> CI #ISSUE_NUMBER'
git push origin <feature_branch>
```

## References
* https://quarto.org/docs/presentations/revealjs/
* https://quarto.org/docs/presentations/revealjs/advanced.html

