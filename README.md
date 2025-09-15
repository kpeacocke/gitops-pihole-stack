# dns-stack (Pi-hole + Unbound, Portainer GitOps)

Deploys Pi-hole (port 53/80) and Unbound (port 5335) via host networking.
Each host sets HOST_IP and WEBPASSWORD via Portainer env vars.

## Per-host env (examples)

- terror (192.168.5.52): HOST_IP=192.168.5.52, WEBPASSWORD=*****
- harmony (192.168.5.54): HOST_IP=192.168.5.54, WEBPASSWORD=*****

## Root hints refresh (manual)

docker run --rm --network host -v "$PWD/unbound:/mnt" curlimages/curl \
  -o /mnt/root.hints <https://www.internic.net/domain/named.root>
