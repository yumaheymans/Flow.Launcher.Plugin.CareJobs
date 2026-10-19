# Flow.Launcher.Plugin.CareJobs

Search free US healthcare jobs from [Flow Launcher](https://www.flowlauncher.com/), with the pay employers post. Nurses, CNAs, techs, therapists, medical assistants and more, from [CareJobs.Now](https://carejobs.now).

Type `cj`, a job, and a state. Press Enter to open the job.

## Install

In Flow Launcher:

```
pm install CareJobs.Now
```

Then restart Flow Launcher if it asks you to. (The `pm install` name works once the plugin is listed in the Flow Launcher plugin store. Until then, download `Flow.Launcher.Plugin.CareJobs.zip` from the Releases page and unzip it into `%APPDATA%\FlowLauncher\Plugins\CareJobs.Now`, then restart Flow Launcher.)

## Usage

| Type this | You get |
| --- | --- |
| `cj icu nurse tx` | ICU nurse jobs in Texas |
| `cj travel cna in phoenix` | Travel CNA jobs matching "phoenix" |
| `cj rn texas` | Registered nurse jobs in Texas (a full state name works too) |
| `cj remote coding` | Remote medical coding jobs |
| `cj` | A hint and five popular searches (registered nurse, CNA, LPN, medical assistant, travel nurse) |

How the text is read:

- A two-letter US state code (`tx`, `NY`) is a state when it is the last word. A full state name at the end works too (`new york`, `texas`).
- The word `remote` limits the search to remote jobs.
- A leading or trailing `in` is ignored. To search Indiana, type `indiana` in full.
- A lone `pa` or `ma` is searched as a job word (physician assistant, medical assistant), not as a state.
- Everything else is the job search.

Each result shows `Title at Employer`, then the pay (when there is one), the location and the date listed. Pay that CareJobs.Now measured from an employer's open jobs, not stated by the posting itself, is marked `typical at <employer>`.

Press Enter to open the job. Open the context menu (Shift+Enter) on a job to open the job or the employer's page on CareJobs.Now. The last result, "See all N jobs", opens the same search on the CareJobs.Now board with filters.

If CareJobs.Now cannot be reached within 25 seconds, you get one result that opens the search in your browser instead. The plugin never crashes Flow.

## Privacy

The plugin sends only what you type after `cj` (and the state or `remote` flag read from it) to `https://carejobs.now/api/mcp`, over HTTPS, to get the matching jobs. There is no account, no API key, no tracking and no analytics. Nothing is stored on your computer.

## Development

The plugin is one file, `main.py`, using the Python standard library plus the `flowlauncher` package Flow needs (`requirements.txt`). To try it without Flow:

```
pip install -r requirements.txt -t ./lib
python main.py '{"method": "query", "parameters": ["icu nurse tx"]}'
```

The GitHub Actions workflow (`.github/workflows/Publish Release.yml`) installs the dependency into `lib/`, zips the plugin as `Flow.Launcher.Plugin.CareJobs.zip` and publishes it as release `v<Version>` (the version in `plugin.json`).

## License

MIT. See [LICENSE](LICENSE).
