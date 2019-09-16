





 docker run -v c:/Users/mark/dev/blue-green/traefik.toml:/traefik.toml -v /var/run/docker.sock:/var/run/docker.sock -p 80:80 --name traefik --rm -l traefik.frontend.rule=Host:monitor.localhost -l traefik.port=8080 traefik:1.7.2-alpine --docker --loglevel="DEBUG"                                                                                                                                                                                                      


docker run -l traefik.frontend.rule=Host:nginx.localhost --rm nginx



http://devonhubner.org/using_traefik_with_consul/

consul kv put traefik/frontends/dapp/backend dapp
consul kv put traefik/frontends/dapp/entrypoints http
consul kv put traefik/frontends/dapp/routes/dapp0/rule "Host:dapp.hubner.org"

consul kv put traefik/backends/dapp/servers/server0/url    "http://0.0.0.0:80"
consul kv put traefik/backends/dapp/servers/server0/weight 1