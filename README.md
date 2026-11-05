# TrackerPulse – BitTorrent Tracker Validator

Check your trackers. Clean your lists. Export what works.

TrackerPulse is a desktop application for validating and organizing BitTorrent tracker lists. It checks HTTP, HTTPS, and UDP trackers, separates working entries from unreachable or invalid ones, and lets you export the results through a dark-themed graphical interface.

Whether you’re maintaining a small collection or checking a large tracker list, TrackerPulse brings scanning, diagnostics, filtering, and exporting into one place.

## Screenshots

[![TrackerPulse main interface](https://i.postimg.cc/26FFNnr2/Screenshot-2026-11-05-104423.png)](https://i.postimg.cc/26FFNnr2/Screenshot-2026-11-05-104423.png)

[![TrackerPulse application in action](https://i.postimg.cc/9MttHyCx/Screenshot-2026-11-05-104508.png)](https://i.postimg.cc/9MttHyCx/Screenshot-2026-11-05-104508.png)

## VirusTotal

[View the VirusTotal scan report](https://www.virustotal.com/gui/file-analysis/ZDVhZDljNmE5MjUzMTRlYTc2NTBkYTgzODA2NDNkNWI6MTc5Mzg3MjYyNw==)

## Features

- **Multi-protocol validation** — Check HTTP, HTTPS, and UDP tracker URLs.
- **Concurrent scanning** — Validate multiple trackers simultaneously, with configurable thread counts and connection timeouts.
- **Clear result categories** — Separate trackers into alive, dead, and invalid groups.
- **Response-time measurements** — Optionally measure how long each validation request takes.
- **Diagnostic details** — Review connection errors, timeouts, invalid responses, and other validation results.
- **Invalid-page detection** — Identify common signs of parked domains, advertising pages, and ordinary HTML pages instead of tracker responses.
- **Automatic deduplication** — Remove duplicate tracker URLs when importing a list.
- **Live progress tracking** — Monitor completed checks, category counts, scanning speed, and estimated time remaining.
- **Search and filtering** — Find specific entries and display results by status.
- **Flexible exports** — Save a categorized report or export only working trackers.
- **Configurable autosave** — Save partial results after a chosen number of checks, a time interval, or both.
- **Stop and save** — Stop a scan while preserving the results already collected.
- **Persistent settings** — Keep your scanning and export preferences between sessions.

## How It Works

1. Select a text file containing your tracker URLs.
2. Choose where to save the results.
3. Adjust the thread count and timeout to suit your connection.
4. Enable response-time measurements or autosave if needed.
5. Start the scan and review results as they arrive.
6. Export the full report or save only the working trackers.

## Input Format

Create a text file with one tracker URL per line:

```text
udp://tracker.example.org:6969/announce
[https://tracker.example.net/announce](https://tracker.example.net/announce)
http://tracker.example.com:8080/announce
```

Duplicate URLs are automatically removed during import.

## Understanding Results

| Status | Meaning |
| --- | --- |
| Alive | The endpoint responded and was recognized as a tracker by the application's checks. |
| Dead | The check failed because of a timeout, connection error, HTTP error, or an unrecognized response. |
| Invalid | The entry has an invalid or unsupported URL, or the endpoint was identified as a non-tracker page or another invalid target. |

Diagnostic details appear beside each result to help explain its classification.

A tracker that returns a valid protocol-level failure response may still be classified as alive: the tracker is responding even if it rejects the test request.

## Export Options

### Categorized Report

Save a report containing:

- Checked tracker count and category totals.
- Results grouped by status and protocol.
- Diagnostic reasons for dead and invalid entries.
- Elapsed scanning time.
- Optional response-time measurements.

### Working Trackers Only

Export only the trackers classified as alive.

Leave response-time information disabled when you need a URL-only list.

### Partial Results

Autosave can preserve progress:

- After every specified number of trackers.
- After a specified time interval.
- When either condition is reached.

You can also save results manually while a scan is running.

## Keyboard Shortcuts

| Shortcut | Action |
| --- | --- |
| `Ctrl + O` | Select an input file |
| `F5` | Start scanning |
| `Ctrl + S` | Save current results |
| `Ctrl + Q` | Exit the application |

## Validation Notes

- Results reflect the endpoint's response at the time of the scan.
- An alive result does not guarantee that the tracker will accept every torrent or return peers.
- Measured response time includes DNS resolution and protocol negotiation; it is not an ICMP ping measurement.
- A timeout can indicate a temporarily unavailable or slow endpoint, not necessarily a permanently dead tracker.
- TrackerPulse validates tracker endpoints; it is not a torrent client and does not download torrent content.
