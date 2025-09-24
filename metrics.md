# Lean Metrics

- [Chain Metrics](#chain-metrics)
    - [State](#state)
    - [Block](#block)
    - [Attestations](#attestations)
- [Validator Metrics](#validator-metrics)
- [Fork-choice Metrics](#fork-choice-metrics)
- [Network Metrics](#network-metrics)
    - [ReqResp](#reqresp)
    - [Gossip](#gossip)
    - [API](#api)
    - [Sync](#sync)
    - [Peers](#peers)
- [Hardware](#hardware)

## Chain Metrics

### State

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|

### Block

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_previous_epoch_orphaned_blocks` | Gauge | Number of blocks orphaned in the previous epoch | On epoch transition | □ | □ | □ |
| `lean_store_block_cache_hit_total` | Gauge | Total number of block cache hits | On epoch transition | □ | □ | □ |
| `lean_state_block_cache_miss_total` | Gauge | Total number of block cache misses | On epoch transition | □ | □ | □ |
| `lean_block_delay_count` | Histogram | Block delay count, bucket size yet to be decided | On slot | □ | □ | □ |
| `lean_block_proposed_total` | Gauge | Total number of blocks proposed | On epoch transition | □ | □ | □ |
| `lean_processor_gossip_block_imported_total`| Gauge | Total number of imported blocks | On epoch transition | □ | □ | □ |

### Attestations

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_attestations_published_total` | Gauge | Total number of attestations published | On epoch transition | □ | □ | □ |
| `lean_attestations_received_total` | Gauge | Total number of attestations received | On epoch transition | □ | □ | □ |
| `lean_aggregated_attestations_published_total` | Gauge | Total number of aggregated attestations published | On epoch transition | □ | □ | □ |
| `lean_aggregated_attestations_received_total` | Gauge | Total number of aggregated attestations received | On epoch transition | □ | □ | □ |
| `lean_attestation_delay_count` | Histogram | Attestation delay count | On epoch transition |  □ | □ | □ |

## Validator Metrics

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_current_validators` | Gauge | Number of `status="pending\|active\|exited\|withdrawable"` validators in current epoch | On epoch transition | □ | □ | □ |
| `lean_current_active_validators` | Gauge | Current total active validators | On epoch transition | □ | □ | □ |
| `lean_previous_validators` | Gauge | Number of `status="pending\|active\|exited\|withdrawable"` validators in previous epoch | On epoch transition |  □ | □ | □ |
| `lean_current_live_validators` | Gauge | Number of active validators that successfully included attestation on chain for current epoch | On block |  □ | □ | □ |
| `lean_previous_live_validators` | Gauge | Number of active validators that successfully included attestation on chain for previous epoch | On block |  □ | □ | □ |
| `lean_processed_deposits_total` | Gauge | Total number of deposits processed | On epoch transition | □ | □ | □ |
| `lean_pending_deposits` | Gauge | Number of pending deposits (`state.eth1_data.deposit_count - state.eth1_deposit_index`) | On block | □ | □ | □ |
| `lean_processed_deposits_total` | Gauge | Number of total deposits included on chain | On block | □ | □ | □ |
| `lean_pending_exits` | Gauge | Number of pending voluntary exits in local operation pool | On slot | □ | □ | □ |
| `lean_local_validator_count` | Gauge | Count of the number of local validators | On slot | □ | □ | □ |
| `lean_attester_slashing_created_total` | Gauge | Total number of slashing created | On epoch transition | □ | □ | □ |
| `lean_attester_slashing_received_total` | Gauge | Total number of attestor slashing received | On epoch transition | □ | □ | □ |

## Fork-choice Metrics

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_head_slot` | Gauge | Latest slot of the beacon chain | On fork choice | □ | □ | □ |
| `lean_finalized_epoch` | Gauge | Current finalized epoch | On epoch transition | □ | □ | □ |
| `lean_current_justified_epoch` | Gauge | Current justified epoch | On epoch transition | □ | □ | □ |
| `lean_previous_justified_epoch` | Gauge | Previously justified epoch | On epoch transition | □ | □ | □ |
| `lean_head_state_finalized_root` | Gauge | Current finalized root* | On epoch transition | □ | □ | □ |
| `lean_current_justified_root` | Gauge | Current justified root* | On epoch transition | □ | □ | □ |
| `lean_previous_justified_root` | Gauge | Previously justified root* | On epoch transition | □ | □ | □ |
| `lean_head_state_root` | Gauge | Head state root* | On slot | □ | □ | □ |
| `lean_reorgs_total` | Counter | Total number of chain reorganizations | On fork choice | □ | □ | □ |

\* All `root*` values are converted to signed 64-bit integers utilizing the last 8 bytes interpreted as little-endian (`int.from_bytes(root[24:32], byteorder='little', signed=True)`).

## Network Metrics

### ReqResp

| Name | Type | Usage | Sample collection event | Grandine | Lighthouse | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|

### Gossip

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_gossipsub_mesh_peers_per_main_topic` | Gauge | Number of peers per gossipsub topic | On slot | □ | □ | □ |
| `libp2p_pubsub_validation_failure_total` | Gauge | Number of pubsub validation messages failed | On epoch transition | □ | □ | □ |

### API

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_http_api_requests_total` | Gauge | Total number of requests to the HTTP API endpoint | On slot | □ | □ | □ |
| `lean_http_api_successes_total` | Gauge | Total number of successful requests to the HTTP API endpoint | On slot | □ | □ | □ |

### Sync

| Name | Type | Usage | Sample collection event | Grandine | Lighthouse | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_sync_state` | Gauge | Beacon sync state, 0 for not syncing, 1 for synced, 2 for syncing | On slot | □ | □ | □ |

### Peers

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_libp2p_peers` | Gauge | Tracks the total number of libp2p peers | On peer add/drop | □ | □ | □ |

## Hardware

| Name | Type | Usage | Sample collection event | Qlean | Ream | Zeam |
|--------|-------|-------|-------------------------|----------|------------|----------|
| `lean_process_cpu_seconds_total` | Gauge | Total CPU time in seconds | On slot | □ | □ | □ |
| `lean_process_max_fds` | Gauge | Maximum number of file descriptors | On slot | □ | □ | □ |
