# My Blog With Hugo.

### Add new post:
- `cd ChrisCodes`
- `hugo new --kind post content/posts/<name>.md`

### Run server:
`hugo server`

### Build static files:
- `cd ChrisCodes/`
- `hugo -t PaperMod`

### Update ChrisCodes:
(after building static files)
- `cd ChrisCodes/public` 
- `git add .`
- `git commit -m "message"`
- `git push`