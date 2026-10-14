# Security Testing and Validation

## Test Results

| Test | Result | Remaining Check |
| --- | --- | --- |
| Windows event collection | Application, Security, and System sources searchable in Splunk | Measure collection completeness and latency |
| Failed authentication | EventCode 4625 result with failure reason and logon type 2 | Validate coverage across additional endpoints |
| Failed-login threshold | Five-minute account-group results reached a count of 5 | Normalize multivalued account fields before comparing distinct attempts |
| Account lockout policy | Default-domain policy returned threshold 5, duration 30 minutes, and reset window 30 minutes | Check any fine-grained policy overrides |
| Controlled authentication test | Five failed-attempt messages followed by LockedOut=True | Individual catch messages do not independently classify each error |
| Account lockout event | EventCode 4740 at displayed time 2026-10-14 13:20:40.937 with account and caller populated | Measure recovery after the configured lockout duration |
| Dashboard | Populated login charts and account/lockout tables | Validate the password-reset panel's underlying search |
| Failed-login alert | Trigger entry at 2026-10-14 11:50:01 Central Daylight Time | Confirm final search bounds and suppression behavior |
| Lockout alert | Trigger entry at 2026-10-14 13:40:01 Central Daylight Time | Confirm final search bounds and suppression behavior |

## Alert Configuration

The configuration screenshots show cron `*/5 * * * *`, a result-count condition greater than zero, and a 15-minute throttle. The lockout alert action uses High severity and Add to Triggered Alerts.

The alert dialogs show a 15-minute lookback. A subsequent time picker selects five minutes ago with beginning-of-minute snapping and latest now, equivalent to `-5m@m` through `now`. The final saved five-minute window needs confirmation for both alerts.

## Further Testing

- Confirm and export the saved alert time bounds.
- Test suppression within the 15-minute throttle and re-trigger behavior after expiry.
- Confirm whether distinct accounts are suppressed together or separately.
- Normalize target-account attribution in failed-login searches.
- Check effective policy for the specific test account, including fine-grained overrides.
- Measure actual account recovery after 30 minutes.
- Validate the password-reset search before adding a standalone query.
- Verify event latency, schedule timezone, endpoint coverage, and licensing.

## Detection Limitations

Fixed five-minute buckets can split an authentication burst at a boundary. A 15-minute lookback on a five-minute schedule revisits events, while an immediate five-minute lookback can miss late arrivals.

Failed logons and account lockouts can result from typos or stale stored credentials. Threshold results support investigation and do not establish that an attack occurred.

The EventCode 4740 extraction assumes English Message formatting and an existing Caller_Computer_Name extraction. Index scope must be configured for the deployment.

## Supporting Evidence

The screenshot inventory maps original filenames to the selected images. Command screenshots containing password-like strings and alert-history screenshots containing personal browser context are excluded from the public evidence folder.
