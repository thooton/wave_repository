# Wave's default source

This is the public catalog Wave reads (see [README.md](README.md)). It holds
only manifests and icons. Each manifest points to an immutable public HTTPS
release asset. Never hand-edit a manifest: write it with Wave's publishing
tool (`tools/wavesrc/wavesrc publish` in the sibling `../wave` checkout, or
the CI publish action). Commit as thooton, with no AI attribution. *Lint
source* checks every push. *Catalog freshness* runs `tools/ship/ship audit`
to flag public versions that were released but are not listed here.

## Finish every task: commit, push, CI, publish

Every Wave worker finishes completed work the same way, in every Wave
repository, unless the task explicitly says to hold it or not to publish:

1. Commit it and push it to `master`. Rebase on `origin/master`, rerun the
   affected checks, run `oak git push origin HEAD:master`, and never force-push.
2. Wait for master CI on your commit. Fix a failure, or report it.
3. If the change is a publishable deliverable (an app or mod version, or the
   Wave app), publish it through its release channel. Then confirm that its
   catalog lists the new version. Pushing to `master` is not publication.
4. Run `../wave/tools/ship/ship check` and put its output in your final
   report. Report each `BLOCKED` line as an explicit blocker. For an
   explicit hold, pass `--hold "<the task's words>"`; the work must still be
   committed, pushed and green.

Never add a private package, private asset URL or credential here.

See [tools/ship](https://github.com/thooton/wave/blob/master/tools/ship/README.md)
for each repository's channel and what the checker verifies.
