# Node Siting Tool

Self-contained interactive map for fulfillment node placement.

- Population-weighted USPS zone averages
- Time-in-transit overlays (business days), two kinds kept separate:
  - **Carrier-stated** (works from any node): USPS Ground Advantage / Priority / First-Class,
    UPS Ground / Next Day / 2nd Day / 3 Day Select, FedEx Ground, Amazon Shipping Ground
    (Springfield only — Amazon quotes only from our pickup), DHL eCommerce Parcel
    Ground / Expedited / Expedited Max (DHL uses the injection DC nearest the node)
  - **Measured** (Springfield node only): our own parcels, carrier possession scan → delivered,
    95% plan days, for UPS Ground / Ground Saver, FedEx Ground / Home Delivery / Ground Economy,
    USPS Ground Advantage / Priority, DHL Parcel Ground / Expedited / Expedited Max, Amazon,
    UniUni and GOFO. Source: Carrier Lane Transit Reference.
- Transit comparison tab: every service across every saved network
- 3PL directory network load + versus comparison, billed-rate cost comparison

**Live:** https://we-re-good-company.github.io/node-siting-tool/

Rebuild locally:

```bash
python3 ~/.hermes/scripts/node_siting_transit_extra.py      # FedEx / DHL / measured matrices
python3 ~/.hermes/scripts/node_siting_map_build.py ~/.hermes/state/zone-geo/node_siting_map.html
cp ~/.hermes/state/zone-geo/node_siting_map.html index.html
git add index.html && git commit -m "rebuild" && git push
```

Data is embedded; no server required. File is large (~21 MB) because zone + transit matrices ship inline.
