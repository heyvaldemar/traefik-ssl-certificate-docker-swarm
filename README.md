# Traefik with SSL Certificate in a Docker Swarm

Install Docker Swarm by following my [guide](https://www.heyvaldemar.com/install-docker-swarm-on-ubuntu-server/).

Create a network for Traefik, config and secrets for storing the Traefik configuration, certificate and key on the Docker Swarm manager node before applying the configuration.

Create a network for Traefik using the command:

`docker network create -d overlay traefik-network`

Create a secret for storing the certificate using the command:

`docker secret create wildcard-heyvaldemar-net.crt /path/to/wildcard-heyvaldemar-net.crt`

Create a secret for storing the key using the command:

`docker secret create wildcard-heyvaldemar-net.key /path/to/wildcard-heyvaldemar-net.key`

Create a config for storing the Traefik configuration using the command:

`docker config create traefik-dynamic-configuration.yml /path/to/traefik-dynamic-configuration.yml`

Example of traefik-dynamic-configuration.yml:

```
tls:
  certificates:
    - certFile: /run/secrets/wildcard-heyvaldemar-net.crt
      keyFile: /run/secrets/wildcard-heyvaldemar-net.key
```

Deploy Traefik in a Docker Swarm using the command:

`docker stack deploy -c traefik-ssl-certificate-docker-swarm.yml traefik`

# Author

I’m Vladimir Mikhalev, the [Docker Captain](https://www.docker.com/captains/vladimir-mikhalev/), but my friends can call me Valdemar.

🌐 My [website](https://www.heyvaldemar.com/) with detailed IT guides\
🎬 Follow me on [YouTube](https://www.youtube.com/channel/UCf85kQ0u1sYTTTyKVpxrlyQ?sub_confirmation=1)\
🐦 Follow me on [Twitter](https://twitter.com/heyValdemar)\
🎨 Follow me on [Instagram](https://www.instagram.com/heyvaldemar/)\
🧵 Follow me on [Threads](https://www.threads.net/@heyvaldemar)\
🐘 Follow me on [Mastodon](https://mastodon.social/@heyvaldemar)\
🧊 Follow me on [Bluesky](https://bsky.app/profile/heyvaldemar.bsky.social)\
🎸 Follow me on [Facebook](https://www.facebook.com/heyValdemarFB/)\
🎥 Follow me on [TikTok](https://www.tiktok.com/@heyvaldemar)\
💻 Follow me on [LinkedIn](https://www.linkedin.com/in/heyvaldemar/)\
🐈 Follow me on [GitHub](https://github.com/heyvaldemar)

# Communication

👾 Chat with IT pros on [Discord](https://discord.gg/AJQGCCBcqf)\
📧 Reach me at ask@sre.gg

# Give Thanks

💎 Support on [GitHub](https://github.com/sponsors/heyValdemar)\
🏆 Support on [Patreon](https://www.patreon.com/heyValdemar)\
🥤 Support on [BuyMeaCoffee](https://www.buymeacoffee.com/heyValdemar)\
🍪 Support on [Ko-fi](https://ko-fi.com/heyValdemar)\
💖 Support on [PayPal](https://www.paypal.com/paypalme/heyValdemarCOM)
