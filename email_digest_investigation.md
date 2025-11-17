# Email digest subscriber investigation

## Findings
- The repository's subscriber list lives in [`subscribers.json`](subscribers.json), and the file currently contains an empty array. With no addresses present, any job that reads this file for e-mail recipients will report that there are "no subscribers."
- `subscribers.json` was introduced empty in commit `936b283` ("Create subscribers.json for subscriber system"), and there have been no subsequent updates to populate it with subscriber data.

## Implications
Because the subscriber list remains empty and there is no code in this repository that populates it, the cron job responsible for sending the e-mail digest will continue to log "no subscribers" until valid addresses are written to `subscribers.json` or another data source is connected.
