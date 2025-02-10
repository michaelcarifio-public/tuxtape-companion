# tuxtape companion

This repo is my personal "companion" to the [tuxtape](https://github.com/tuxtape/) repo. I've squirreled away notes to myself, various scripts and a recipe or three
to interact with tuxtape and it's github repository. Most of it's frankly remedial and serves as a quick reminder for how I should do things.

## setup

install, configure rust _et al_ on Ubuntu 24.04 tbs

### dev

Start:

```bash
export me=michaelcarifio-public project=tuxtape upstream=geico ## my public github account for working on tuxtape
gh repo clone ${upstream}/${project} ~/src/${me}/${project} # origin is currently geico/tuxtape
cd ~/src/${me}/${project}
gh repo fork ${me}/${project} # origin now ${me}/tuxtape, upstream is geico/tuxtape
cargo update ...
cargo test ...
```

Add:

```bash
## catch up with geico/tuxtape:main
git checkout main && gh pull upstream main ## periodically
cargo update ... # more needed here
cargo test ... # if/when you break something below, it's easier to identify what you broke

# create a branch and work on it
export branch="a-branch"
git checkout -b ${branch}
ide || emacs || code ...  ## add something 
cargo test ... # iterate
git commit -u origin ${branch} ## periodically
```

Contribute:

```bash
git ${something} ## squash all the branch commits down to one
git commit -am "commit summary"
git push --upstream origin ${branch}
gh pr create --base ${branch} --fill --draft --web  ## ... and review in your browser
```


