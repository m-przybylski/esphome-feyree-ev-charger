# Feyree EV Charger

ESPHome component for Feyree EV Charger.
Need resolder or reflash installed tuya wifi module.

## Datapoints configuration

### Datapoint ID:  124

dpID 124 command value does NOT persist. It reverts to WaitOperation (~2/Ready) approximately 1 second after command execution.
This means when you send OpenCharging, the MCU:
1. Closes the relay, starts charging
2. Reverts dp 124 back to WaitOperation after ~1 second
When you send CloseCharging, the MCU:
1. Opens the relay, stops charging
2. Reverts dp 124 back to WaitOperation after ~1 second
WaitOperation is the MCU's default idle state - it's not a "mode" you set, but rather what the MCU reports when it's ready but not actively charging.

| Tuya Value |	HA Mapping	| Meaning |
|---|---|---|
| 0 (OpenCharging)	| "on"	| Force start charging immediately |
| 1 (CloseCharging)	| "off"	| Stop charging |
| 2 (WaitOperation)	| "on_demand" |	Ready & waiting for vehicle to request charge |


## TODO

- [ ] Error bitmask (completed for portable changer)
- [ ] Status enum (completed for portable changer)
- [ ] Docs
