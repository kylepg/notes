<title>git - github cli</title>

# Git - GitHub CLI

## New repo (user)

```
curl -u 'USERNAME' https://api.github.com/user/repos -d '{"name":"REPO-NAME"}'
```

#### Alfred:

```
function new-git() {
  curl -u 'USERNAME' https://api.github.com/user/repos -d '{"name":"'$1'"}'
}
new-git {query}
```

&nbsp;

## New repo (organization)

```
curl -u 'USERNAME' https://api.github.com/orgs/celticsdev/repos -d '{"name":"REPO-NAME"}'
```

#### Alfred:

```
function new-git() {
  curl -u 'USERNAME' https://api.github.com/orgs/celticsdev/repos -d '{"name":"'$1'"}'
}
new-git {query}
```
