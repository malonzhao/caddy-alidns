# Caddy AliDNS

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Alibaba Cloud (as is Aliyun) accounts.

## Config examples

To use this module for the ACME DNS challenge with the Caddyfile:

```
# globally

acme_dns alidns {
  access_key_id {env.ALIYUN_ACCESS_KEY_ID}
  access_key_secret {env.ALIYUN_ACCESS_KEY_SECRET}
}
```

```
# one site

tls {
  dns alidns {
    access_key_id {env.ALIYUN_ACCESS_KEY_ID}
    access_key_secret {env.ALIYUN_ACCESS_KEY_SECRET}
  }
}
```

If you have `SecurityToken` for aliyun's STS authorization you can configure like:


```
# globally

acme_dns alidns {
  access_key_id {env.ALIYUN_ACCESS_KEY_ID}
  access_key_secret {env.ALIYUN_ACCESS_KEY_SECRET}
  security_token {env.ALIYUN_SECURITY_TOKEN}
}
```

```
# one site

tls {
  dns alidns {
    access_key_id {env.ALIYUN_ACCESS_KEY_ID}
    access_key_secret {env.ALIYUN_ACCESS_KEY_SECRET}
    security_token {env.ALIYUN_SECURITY_TOKEN}
  }
}
```

You can replace `{env.ALIYUN_ACCESS_KEY_ID}`,`{env.ALIYUN_ACCESS_KEY_SECRET}`,`{env.ALIYUN_SECURITY_TOKEN}` with the actual auth token in the `""` if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See [the associated README in the libdns package](https://github.com/libdns/alidns) for important information about credentials.

## Note

Inspired by [Caddy Cloudflare](https://github.com/caddybuilds/caddy-cloudflare).
