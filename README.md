# My blog with Hugo.

### add new post
cd ChrisCodes
`hugo new --kind post content/posts/<name>.md`

### run server
`hugo server`

### build static files
cd ChrisCodes/
`hugo -t PaperMod`

### update ChrisCodes
after building static files:
cd ChrisCodes/public 
git add .
git commit -m "message"
git push