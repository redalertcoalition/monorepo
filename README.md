# Red Alert Monorepo

## Why a Monorepo?

A monorepo handles multiple projects in a single git repository. These are widely in use at [Facebook](https://engineering.fb.com/core-data/scaling-mercurial-at-facebook/), [Google](https://research.google/pubs/pub45424/), and many smaller companies.

Note that a *monorepo* is not the same thing as a *monolith*. Each service is still entirely self-contained and has its own build pipeline and testing suite.

The primary benefits of using a monorepo are:

- Simplified organization
- Simplified dependencies
- Simplified integration testing
- Tooling
- Cross-project changes

This [blog post](http://danluu.com/monorepo/#:~:text=With%20a%20monorepo%2C%20projects%20can,reduces%20overhead%20from%20managing%20dependencies.) has more information, if you're interested.

## Contributing

**Always** create a new branch before you start any new work. The branch name should be `worktype/issue-no/description` where `worktype` is `feature` or `bug`, and `issue-no` directly corresponds to a GitHub issue.

```
$ git checkout -b feature/1234/add-a-gizmo
```

To create a new service, create a new directory in the root of the monorepo with the name of the service (service names should be short and descriptive). The service should have:

- Proper automated test coverage
- Sane [Dockerfile](https://docs.docker.com/engine/reference/builder/)
- Sane [Helm chart](https://helm.sh/docs/topics/charts/)

Any secrets (API keys, passwords, security issues) etc should be set up on [Kubernetes](https://kubernetes.io/docs/concepts/configuration/secret/) and not committed to the repository (message @TwilightWinter to get this set up).

You may push your branch as often as you want:

```
git push origin feature/1234/add-a-gizmo
```

When you're done, open a pull request to `master`. Any pull request which does not follow these requirements will be declined.

**ANY DIRECT PUSH TO MASTER WILL RESULT IN REMOVAL FROM THE PROJECT AND A PERMANENT BAN FROM THE ORGANIZATION. DO NOT DO THIS, YOU WILL GIVE ME A HEADACHE.**
