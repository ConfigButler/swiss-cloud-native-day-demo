# k8s-audit-trail

A **sink**, not a source. Nothing here is applied to any cluster.

Every commit in this repository was written by
[gitops-reverser](https://github.com/ConfigButler/gitops-reverser) running on
`k8s.koudijs.dev`, mirroring live Kubernetes objects into YAML after somebody
changed them through the API server.

The interesting part is the **author** of each commit. It is not a robot: it is
the human whose credential the API server authenticated, recovered from the
kube-apiserver audit event. During the coffee demo those humans are conference
attendees who signed in with a room code, so a commit here reads:

```
Author: Ada <p-1a2b3c@demo.invalid>
Commit: ConfigButler <gitops-reverser@k8s.koudijs.dev>
```

The author name is whatever that person typed into the join form. The address is
synthetic — `demo.invalid` has no mailbox behind it, by design.

## Layout

```
clusters/k8s.koudijs.dev/voter/    the coffee demo namespace, mirrored live
```

## Lifetime

Disposable. This repository is reset between demos and carries no history worth
keeping.
