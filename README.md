# go-gmail-reader
VIP


# Targets
- [ ] Should run as command line applicacion
- [ ] Should be able to authentificate to google (see link #1)1
- [ ] Must read emails with label (example: 'to_proces') and looks for thouse having attachments
- [ ] Get email's attachment to working directory (for example `./work`)
- [ ] If attachemnt is archive, then extract it
- [ ] Parse XML files to be able to indentify type
- [ ] Figure out rules how to identifi files ()
- [ ] Be able cofigure rules extrarnaly (by config file)
- [ ] Files which matches rule copy to directory (specific for rule)

Example of rule config:
```yaml
rules:
- name: socialna poistonva
  target: ~/data/firma/odvody/sp/{{.Year}}-{{.Month}} # https://pkg.go.dev/text/template@go1.20.7
  identify:
  - /mvpp
  params:
  - xpath: /mvpp/obdobie  # xpath syntax: https://www.w3schools.com/xml/xpath_syntax.asp
    valueMath: (\d{2})(\d{4}) # rexexp sytaxL: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Cheatsheet
    values:
    - name: Year
      matchingGroup: 2
    - name: Month
      matchingGroup: 1
```

# LINKS
1. [Gmail API](https://pkg.go.dev/google.golang.org/api/gmail/v1) - how to work with emails
2. [Quick stat with Gmail](https://developers.google.com/gmail/api/quickstart/go) - how to authentificate


# Hints for developers
- https://pkg.go.dev/std - standard library documentation
- https://gobyexample.com/ - how to use go
- https://regexr.com/ - explains regular expresions

Start app:
```sh
# install dependencies
go get golang.org/x/oauth2
go get golang.org/x/oauth2/google
go get google.golang.org/api/gmail/v1
go get google.golang.org/api/option
# clean init
go mod tidy

# stat app
go run .
```
