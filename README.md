# Angular Monorepo

This is a prototype for a new repository we would host on the github.com/angular org.

It would be a single master upstream tree for all Angular projects, including Material,
CLI/Devkit, Universal, etc.

It's also suitable for
- other Angular related projects that want to share build/CI infrastructure with us,
  eg. AngularFire or ngRx
- Hosting examples of how enterprise-scale development works

## Design

TODO(alexeagle): fill in more detail

- Each existing repository can choose to stay open to collect issues and PRs, or
  archive and merge fully into angular/angular.
- The repository should switch to Bazel at the same time, so that it's possible
  to have incremental build/CI across the whole tree. Otherwise CI would become
  impossible because of the volume of tests times the number of commits.
- angular/angular would stay open and would collect issues/PRs/milestones etc.
- angular/monorepo would have the canonical post-merge CI - we want a global
  green across all our projects at head
- Enforce that certain subtrees are owned in a given repository, eg. don't allow
  changes to angular/packages/core to land in the material repository.
- Some tooling - to be created - should automatically create a merge PR from
  green angular/monorepo back down to each repository. And each change merged to
  a repository should be cherry-picked as a PR to angular/monorepo. Whenever one
  of these merge/cherry-pick PRs fails, alert the caretaker that there's a CI
  breakage between different repositories.
