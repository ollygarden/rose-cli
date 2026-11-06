# rose-cli

Rose CLI binaries and templates for self-hosting Rose in your environment.

> Internal use only for now: the action downloads the CLI from the private
> `ollygarden/rose` releases.

## GitHub Actions

Copy [templates/github/rose-review.yml](templates/github/rose-review.yml) to
`.github/workflows/`, add these secrets, and run it from the Actions tab
(Run workflow) on the branch to review:

| Secret | Description |
| --- | --- |
| `OLLYGARDEN_ROSE_RELEASES_TOKEN` | Fine-grained token with `Contents: read` on `ollygarden/rose` |
| `OLLYGARDEN_API_KEY` | OllyGarden organization API key |
| `OPENROUTER_API_KEY` | OpenRouter key for the default models |

The automatic `GITHUB_TOKEN` cannot read `ollygarden/rose` releases from other
repositories.

### Action inputs

| Input | Required | Default | Description |
| --- | --- | --- | --- |
| `command` | Yes | | `review`, `fix` or `instrumentation` |
| `github-token` | Yes | | Token that can read `ollygarden/rose` releases |
| `ollygarden-api-key` | Yes | | OllyGarden organization API key |
| `openrouter-api-key` | Yes | | OpenRouter key for the default models |
| `model` | No | CLI default | `<provider>/<model-id>[:<thinking>]` |
| `version` | No | `latest` | Rose release tag, e.g. `v0.6.62` |
| `api-url` | No | `https://api.ollygarden.cloud` | OllyGarden API base URL |

Runs on `ubuntu-latest` (Linux x64) and Apple silicon macOS runners. The CLI's
output is written to the job summary. Self-hosted runs report their status to
OllyGarden; findings stay in the job output.
