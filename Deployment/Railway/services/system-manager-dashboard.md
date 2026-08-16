# system-manager-dashboard

React (Vite) platform-admin SPA served by Nginx. Public.

| Field | Value |
|---|---|
| Railway Service Name | `system-manager-dashboard` |
| Build Context | `./Frontend/React/system-manager-dashboard` |
| Dockerfile Path | `Dockerfile` |
| Build Args | `VITE_API_BASE_URL=https://<api-gateway-public-domain>` (**required**), `VITE_GRAFANA_URL=https://grafana-production-b423.up.railway.app`, `VITE_GRAFANA_DASHBOARD_UID=medicare-platform` |
| Start Command | *(image default: nginx)* |
| Port | container listens on `80` — set Railway target port to `80` |
| Public / Private | **Public** |
| Health Check | `GET /health` → `200` |

## API wiring (Railway)
No Docker DNS (`127.0.0.11` / `api-gateway:3000`). The SPA calls the public gateway via `VITE_API_BASE_URL`.

## Dependencies
- api-gateway (public + CORS)
- grafana (optional embed)

## Smoke tests
```bash
curl -f https://<system-dashboard-domain>/health
```
