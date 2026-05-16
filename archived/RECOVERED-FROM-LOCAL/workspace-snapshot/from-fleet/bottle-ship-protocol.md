# [I2I:BOTTLE] plato-ship-protocol — 6-Layer Ship Interconnection Protocol

**Repo:** `SuperInstance/plato-ship-protocol`
**Tests:** 8/8 passing
**Gap Closed:** GAP 6 (6-Layer Protocol Stack) — Sprint 3 ahead of schedule

## 6 Traits Defined

| Layer | Trait | Methods |
|-------|-------|---------|
| L1 Harbor | `HarborLayer` | resolve_peer, register_peer, list_peers |
| L2 TidePool | `TidePoolLayer` | enqueue, dequeue, buffer_len |
| L3 Current | `CurrentLayer` | export, import, transport_id |
| L4 Channel | `ChannelLayer` | bridge_send, bridge_recv, is_live |
| L5 Beacon | `BeaconLayer` | emit_event, observe, trust_score |
| L6 Reef | `ReefLayer` | persist, restore, handoff |

## ShipStack
Holds Box<dyn LayerTrait> for each layer.
send() routes L1→L6 (address → route → transport → bridge → signal → persist)
receive() routes L6→L1 (restore → observe → unbridge → import → dequeue → peer)

Zero deps. cargo 1.75 compatible.

## Next: Existing Crates Implement These Traits
- plato-address → HarborLayer
- plato-relay → TidePoolLayer  
- plato-bridge → CurrentLayer
- plato-sim-bridge → ChannelLayer
- cuda-trust → BeaconLayer
- plato-afterlife → ReefLayer
