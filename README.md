# ⚠️ DEPRECATED — use the official integration

**This repository is archived and no longer maintained.**

All improvements from this fork (Eco preset, mode attributes, staggered startup, and related fixes) are available in the official integration:

**→ [mattik-gh/heatit_wifi6](https://github.com/mattik-gh/heatit_wifi6)**

Do **not** install this repository in HACS.

---

## Migrate to `mattik-gh/heatit_wifi6`

This fork used the Home Assistant domain `heatit_wifi6_custom`. The official integration uses `heatit_wifi6`.  
To keep existing `climate.*` entity IDs (and avoid `*_2` duplicates), remove the old config entries **before** adding the official ones again with the **same name and host**.

### Recommended order

1. **Note each thermostat’s exact `name` and `host`**  
   (Settings → Devices & services → each Heatit WiFi6 Custom entry.)
2. **Delete all `heatit_wifi6_custom` config entries**  
   (Do this first — do not install the official integration in parallel.)
3. **Remove this fork from HACS**  
   - HACS → Integrations → remove **Heatit WiFi6 Custom** (if listed)  
   - HACS → Custom repositories → remove `atlehogberg/heatit_wifi6_custom`
4. **Install the official integration**  
   - Prefer HACS: add/install [mattik-gh/heatit_wifi6](https://github.com/mattik-gh/heatit_wifi6)  
   - Or vendor `custom_components/heatit_wifi6` from that repo
5. **Restart Home Assistant**
6. **Add each thermostat again** with the **exact same `name` and `host`** as before  
   (Name controls the `climate.*` entity_id slug.)
7. **Verify**  
   - Same number of climate entities as before  
   - No new `climate.*_2` entities  
   - Platform is `heatit_wifi6`

If a device still got a `*_2` entity_id, rename it back in the UI and remove any leftover unavailable orphans.

YAML automations/scripts that already use your `climate.*` entity IDs should keep working when names/hosts match.

Thank you to everyone who tested and contributed to this fork.

---

## Historical note

This was a temporary fork of [mattik-gh/heatit_wifi6](https://github.com/mattik-gh/heatit_wifi6) used while Eco mode, attributes, and startup congestion fixes were developed and upstreamed. Development continues only in the official repository.

### Last release on this fork

* **1.1.2** — Prepared for upstream merge; domain/logic aligned for compatibility  
* **1.1.1** — Stability and logic improvements  
* Earlier 0.9.x releases — initial fork work (dynamic `sensorMode` temperature, etc.)

## License

[MIT License](LICENSE.md) — third-party software, not affiliated with Heatit (Thermo-Floor AS).
