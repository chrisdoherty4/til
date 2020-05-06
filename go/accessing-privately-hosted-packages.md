# Accessing privately hosted packages

In essence, we can configure a privately hosted repository via the 
`GOPRIVATE` env variable. We can get finer grained control using `GONOPROXY` 
and `GOPROXY` variables.

```
go env -w GOPRIVATE="my.domain.com"
```

#### Go doc

```
go help module-private
```

#### Env vars of interest

```
GOPRIVATE
GONOPROXY
GOPROXY
GOSUMDB
```

#### Documentation

[Module configuration for non-public modules](https://golang.org/cmd/go/#hdr-Module_configuration_for_non_public_modules)

