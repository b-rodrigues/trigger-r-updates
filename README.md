Original readme:

The `copy-trigger-file.yaml` CI of this repository
creates an empty **trigger artifact file** with time stamp and pushes that to
the `r-daily-source` branch of the target repository at
[`rstats-on-nix/nixpkgs`](https://github.com/rstats-on-nix/nixpkgs).

The action is used is based on
[https://github.com/cpina/github-action-push-to-another-repository](cpina/github-action-push-to-another-repository).
Pushing the trigger file of format `_trigger-file/_trigger_$(date "+%Y-%m-%d_%H%M%S")`
from source to the root directory of the target repo is configured via a SSH
deployment key. More details to set it up and more examples can be found in the [docs of the 
action](https://cpina.github.io/push-to-another-repository-docs/setup.html#setup-using-ssh-deploy-keys).
- Trigger source file:
  - `_trigger-file/_trigger_$(date "+%Y-%m-%d_%H%M%S")`
  - Created every given CRON-job interval, pushed to target, and then the folder
    and file is deleted in this source repo. Hence, the target repo will create
    only the last successful push file in the latest commit.
