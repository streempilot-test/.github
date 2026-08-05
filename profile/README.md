# streempilot-test

Independent acceptance organization for **StreemPilot**.

Browser studio, WebRTC, multi-guest, RTMP, destinations, recording, SDK/API/websocket, Flutter, and network-scale acceptance.

## Portfolio

| Repository | Class | Readiness | Primary dependency path |
|---|---|---|---|
| `browser-studio-e2e` | browser E2E | `ready` | `matrix` |
| `webrtc-signaling` | protocol conformance | `ready` | `matrix` |
| `multi-guest-room` | performance/scale | `ready` | `matrix` |
| `rtmp-ingest-egress` | media pipeline | `ready` | `matrix` |
| `destination-provider-adapters` | provider adapter | `ready` | `matrix` |
| `recording-media` | media pipeline | `ready` | `matrix` |
| `clients-api-websocket-contract` | SDK consumer | `ready` | `matrix` |
| `flutter-device-e2e` | mobile/emulator | `ready` | `matrix` |
| `network-scale-chaos` | chaos/fault injection | `ready` | `matrix` |

Pull requests run deterministic harness checks. Emulators, desktop matrices, live APIs/providers, databases, chaos, scale, and soaks are scheduled/manual. Missing upstreams or credentials are blocked readiness—not false passes or product regressions.
