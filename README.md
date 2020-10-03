# lokalni.dev

Doména `lokalni.dev` má v základu DNS A záznamy:
```
  lokalni.dev   127.0.0.1
*.lokalni.dev   127.0.0.1
```
_NS jsou vedeny u Cloudflare (free plán) kvůli jejich API._

Aktuální konfigurace:
```bash
docker-compose config
```

Sledování logů:
```bash
docker-compose logs -f
```

## Traefik

https://doc.traefik.io/traefik/v2.0/

### HTTP only

URL: http://traefik-127-0-0-1.nip.io/
```bash
make set-http
docker-compose up -d
```

### HTTPS Let's Encrypt (DNS Challenge Cloudflare)

Cloudflare API tokenu nastavit práva `Zone > Zone > Read` a `Zone > DNS > Edit`. Taky přidat omezení pouze na zónu `lokalni.dev`.  
Zdroj: https://joshuaavalon.io/setup-traefik-v2-step-by-step

Cloudflare e-mail a API token pak zapsat do `.cloudflare.env` (vykopírovat ze šablony `.cloudflare.env.template`).

URL: https://traefik.lokalni.dev/
```bash
make set-https-cloudflare LE_ACME_EMAIL=email@email.email
docker-compose up -d
```

## Portainer

### HTTP only

URL: http://portainer-127-0-0-1.nip.io/
```bash
make set-http
docker-compose up -d
```

### HTTPS Let's Encrypt (DNS Challenge Cloudflare)

URL: http://portainer.lokalni.dev/
```bash
make set-https
docker-compose up -d
```
