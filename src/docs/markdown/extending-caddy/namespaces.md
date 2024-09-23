---
title: "Module Namespaces"
---

# Module Namespaces

Caddy guest modules are loaded generically as `interface{}` or `any` types. In order for the host modules to be able to use them, the loaded guest modules are usually type-asserted to a known type first. This page describes the mapping from module namespaces to Go types for all the standard modules.

Documentation for non-standard module namespaces can be found with the documentation for the host module that defines them.

<aside class="tip">
	One way to read this table is, "If your module is in &lt;namespace&gt;, then it should compile as &lt;type&gt;."
</aside>

Namespace | Expected Type | Description | Notes
--------- | ------------- | ----------- | ----------
|         | [`caddy.App`](https://pkg.go.dev/github.com/caddyserver/caddy/v2?tab=doc#App) | Caddy app
caddy.config_loaders | [`caddy.ConfigLoader`](https://pkg.go.dev/github.com/caddyserver/caddy/v2#ConfigLoader) | Loads a config | <i>⚠️ Experimental</i>
caddy.fs  | [`fs.FS`](https://pkg.go.dev/io/fs#FS) | Virtual file system |  <i>⚠️ Experimental</i>
caddy.listeners | [`caddy.ListenerWrapper`](https://pkg.go.dev/github.com/caddyserver/caddy/v2#ListenerWrapper) | Wrap network listeners
caddy.logging.encoders | [`zapcore.Encoder`](https://pkg.go.dev/go.uber.org/zap/zapcore#Encoder) | Log entry encoder
caddy.logging.encoders.filter | [`logging.LogFieldFilter`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/logging?tab=doc#LogFieldFilter) | Log field filter
caddy.logging.writers | [`caddy.WriterOpener`](https://pkg.go.dev/github.com/caddyserver/caddy/v2?tab=doc#WriterOpener) | Log writers
caddy.storage | [`caddy.StorageConverter`](https://pkg.go.dev/github.com/caddyserver/caddy/v2?tab=doc#StorageConverter) | Storage backends
dns.providers | [`certmagic.DNSProvider`](https://pkg.go.dev/github.com/caddyserver/certmagic#DNSProvider) | DNS challenge solver
events.handlers | [`caddyevents.Handler`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyevents#Handler) | Event handlers | <i>⚠️ Experimental</i>
http.authentication.hashes | [`caddyauth.Comparer`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/caddyauth?tab=doc#Comparer) | Password hashers/comparers
http.authentication.providers | [`caddyauth.Authenticator`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/caddyauth?tab=doc#Authenticator) | HTTP authentication providers
http.encoders | [`encode.Encoder`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/encode#Encoder) | Usually, compression
http.handlers | [`caddyhttp.MiddlewareHandler`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp#MiddlewareHandler) | HTTP handlers
http.ip_sources | [`caddyhttp.IPRangeSource`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp#IPRangeSource) | IP ranges for trusted proxies
http.matchers | [`caddyhttp.RequestMatcher`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp?tab=doc#RequestMatcher) | HTTP request matchers
http.precompressed | [`encode.Precompressed`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/encode#Precompressed) | Supported precompress mappings
http.reverse_proxy.circuit_breakers | [`reverseproxy.CircuitBreaker`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/reverseproxy?tab=doc#CircuitBreaker) | Reverse proxy circuit breakers
http.reverse_proxy.selection_policies | [`reverseproxy.Selector`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/reverseproxy?tab=doc#Selector) | Load balancing selection policies
http.reverse_proxy.transport | [`http.RoundTripper`](https://pkg.go.dev/net/http?tab=doc#RoundTripper) | HTTP reverse proxy transports
http.reverse_proxy.upstreams | [`reverseproxy.UpstreamSource`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddyhttp/reverseproxy?tab=doc#UpstreamSource) | Dynamic upstream source | <i>⚠️ Experimental</i>
tls.certificates | [`caddytls.CertificateLoader`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddytls?tab=doc#CertificateLoader) | TLS certificate source
tls.client_auth | [`caddytls.ClientCertificateVerifier`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddytls#ClientCertificateVerifier) | Verifies client certificates
tls.handshake_match | [`caddytls.ConnectionMatcher`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddytls?tab=doc#ConnectionMatcher) | TLS connection matcher
tls.issuance | [`certmagic.Issuer`](https://pkg.go.dev/github.com/caddyserver/certmagic?tab=doc#Issuer) | TLS certificate issuer
tls.get_certificate | [`certmagic.Manager`](https://pkg.go.dev/github.com/caddyserver/certmagic?tab=doc#Manager) | TLS certificate manager | <i>⚠️ Experimental</i>
tls.stek | [`caddytls.STEKProvider`](https://pkg.go.dev/github.com/caddyserver/caddy/v2/modules/caddytls?tab=doc#STEKProvider) | TLS session ticket key source

Namespaces marked as "Experimental" are subject to change. (Please develop with them so we can finalize their interfaces!)
