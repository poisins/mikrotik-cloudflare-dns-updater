# mikrotik-cloudflare-dns-updater
RouterOS Script that updates Cloudflare DNS record with current external IP

## Requirements
* JSON parsing library added as script with name `JParseFunctions`: https://github.com/Winand/mikrotik-json-parser
  * System -> Scripts
* RouterOS v7.9 (Verified on 7.9, might work on older versions)

## Usage
1. Add record in Cloudflare DNS
1. Add script in ` System -> Scripts`
   * Remember to edit `APIKEY`, `ZONEID`, `HOSTNAME` and `HOSTNAMETYPE`
   * Edit `UPDATECONTENT` JSON content according to https://developers.cloudflare.com/api/operations/dns-records-for-a-zone-update-dns-record with more information about domain if not sticking with defaults (hardcode or read from response similar to `targetDnsRecordId`)
1. Run or schedule!

## Limitations
`/tool fetch` does not support `http-method=patch` (update) method at the moment, so `http-method=put` (overwrite) is used instead. This might break configuration if defaults are not used. In that case, make sure to send complete JSON body for PUT request (hardcoded or re-use existing settings). 
