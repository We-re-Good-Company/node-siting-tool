# Node Siting Tool

Self-contained interactive map for fulfillment node placement.

- Population-weighted USPS zone averages
- USPS + UPS time-in-transit overlays
- 3PL directory network load + versus comparison

**Live:** https://we-re-good-company.github.io/node-siting-tool/

Rebuild locally:

```bash
python3 ~/.hermes/scripts/node_siting_map_build.py ~/.hermes/state/zone-geo/node_siting_map.html
cp ~/.hermes/state/zone-geo/node_siting_map.html index.html
git add index.html && git commit -m "rebuild" && git push
```

Data is embedded; no server required. File is large (~19 MB) because zone + transit matrices ship inline.
