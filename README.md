Github Issues to JIRA via JSON
==============================

JIRA now provides a JSON import facility that is vastly easier to use than the CSV one.

This is a simple script to generate a JSON file for this import from the GitHub Issues v3 API.

https://confluence.atlassian.com/pages/viewpage.action?pageId=293830712

Set Up
------

install with `bundle install`

Copy `config.yml.sample` to `config.yml` and edit the configuration to suit your needs.


Running
-------


```bash
./g2j.rb --help
Options:
  -s, --start=<i>       starting github issue to avoid rate limiting
  -t, --stop=<i>        stopping github issue to avoid rate limiting
  -r, --renumber=<i>    start the issues at this number to avoid overwriting existing issues
  -h, --help            Show this message
```

Run with default options:
`./g2j.rb`

If you have a lot of issues (this tool makes at least 2 requests per issue), You can set a range of issue numbers to work around the GitHub API rate limit (< 5000 req/hour).

```bash
./g2j.rb --start 1 --stop 1000
```

If your jira project already has issues in it and you just want an import, you can add a constant number to each issue so they won't overwrite your existing issues.

```bash
./g2j.rb --renumber 500
```

TODO
----

- Attachments
