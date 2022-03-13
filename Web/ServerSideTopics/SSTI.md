## Identifying engine by inducing errors
### Ruby ERB:
- `<%= foobar %>`
- `<%= 7/0 %>`

### Twig or Jinja2
- `${{foobar}}`
- `${{7/0}}`

### Twig
- `{{1/0}}`

### Tornado
- `{{foobar}}`

### Java
- `${foobar}`
- `${7/0}`

### Polyglot to induce error:
- `${{<%[%'"}}%\.`

## Identifying the context:
### Plaintext context:
- The input is inserted into the template as it is.

### Code context:
- The input is inserted into the tag, like `{{here}}` or `<%= here %>`
