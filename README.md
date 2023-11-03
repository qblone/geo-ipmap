# geo-ipmap

This repository contains geo-location data of manually verified IP addresses.

## Scope

The scope of this project is currently limited to IP Addresses in the CAPIF region. We may consider extending this scope after the pilot study.

## Methodology

Our methodology for geolocating IP addresses involves the following steps:

1. **Priority IP Addresses:** We will identify IP addresses with priority for geolocation. These include:
   - IP addresses belonging to Internet Exchange Points (IXPs).
   - IP addresses associated with border routers of Autonomous Systems (ASes).
   - Determining the previous and next hop IP addresses in traceroutes for these addresses.

2. **Geolocation for IXP Hops:** For IP addresses belonging to IXPs, we can assign locations based on the IXP metadata.

3. **Geolocation for Other IPs:** For IP addresses not belonging to IXPs, we will assign locations using the following metrics:
   - If the IP address has a corresponding host (using ip2host, please see ips.json-fragment file for translations and list of ip addresses).
   - Low round-trip time (RTT) to our probes (less than 5ms).
   - If the IP address is present in our IP mapping data.
   - Location information in traceroute data, specifically the hop before and after the IP address.
   - Source and destination IP addresses.

## Format for IP Address Geolocation Data

Please follow the specified format when filling in the IP addresses and their geolocation data:


Here is a breakdown of the fields:
- `ipaddr`: The IP address.
- `family`: The address family (e.g., IPv4 or IPv6).
- `city_code`: Code representing the city where the IP address is located.
- `country_code`: Code representing the country where the IP address is located.
- `last_updated`: Date of the last update to the geolocation data.
- `updated_by`: Name or identifier of the person who performed the last update.
- `notes`: Any additional notes or comments related to the IP address geolocation.

