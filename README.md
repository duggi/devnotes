```
#
# ---- devnotes ----
# 


---- 250221 ----
# flatten files in recursive directories

## v1: append dupes with number
mkdir -p ./flatten
find ./flatten/ -type f | while read file; do
    base=$(basename "$file")
    dir="./flatten/"
    if [[ -e "$dir/$base" ]]; then
        ext="${base##*.}"
        name="${base%.*}"
        counter=1
        while [[ -e "$dir/${name}_$counter.$ext" ]]; do
            ((counter++))
        done
        mv "$file" "$dir/${name}_$counter.$ext"
    else
        mv "$file" "$dir/$base"
    fi
done

## v2: append dupes with timestamp
(...)
    if [[ -e "$dir/$base" ]]; then
        ext="${base##*.}"
        name="${base%.*}"
        timestamp=$(date +%s)  # Get current Unix timestamp
        mv "$file" "$dir/${name}_$timestamp.$ext"
    else
(...)

## to run it
- hardcoded to look for flatten/ dir and mv files to it
- create dir named flatten at root of directory to flatten from
- put flatten.sh script above in parent of flatten/
- chmod +x flatten.sh // give execute permission
- issue `flatten` to run script
- destructive, so copy dir if you want to preserce originals
- can prob `cp` instead of `mv` in script?

---- 241110 ----
# nvm
install using git
git checkout v<latest>

# node
nvm install --lts
nvm use --lts

# npm
npm i -g npm@latest

# vite
npm create vite@latest s5 -- --template react-ts
but then use weakest TS settings possible lol
also change package.json to:
`"build": "vite build",`


# tailwind, postcss
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

# react router dom
npm install react-router-dom

# shadcn


```
