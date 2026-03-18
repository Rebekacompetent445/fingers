# fingers

A small TLS-only plaintext request/response protocol inspired by Finger.

This repository contains the working draft specification for `fingers://`.

## Files

- `fingers-protocol-draft.md` — current draft spec
- `LICENSE` — license for the spec text

## Status

This is an early draft.

The protocol is intentionally small and syntax-focused. It defines transport, request syntax, URI mapping, and response framing. It does not require any specific backend model.

## Core ideas

- mandatory TLS from connection start
- one request per connection
- one plaintext response per connection
- UTF-8 text
- no headers
- no status codes
- no length fields
- URI scheme: `fingers://`
- default port: `8179`

## Scope

This draft standardizes only the protocol surface:

- transport and TLS behavior
- request-line syntax
- URI mapping
- response framing
- reserved syntax space

It does not standardize server internals. A conforming daemon may use plain files, scripts, CGI, templates, databases, or any other local mechanism.

## Licensing

The specification text in this repository is licensed under **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)**.

That license applies to the spec text and derivative documentation. It does not automatically apply to independently written clients or servers that implement the protocol.

If reference code is added later, it can be licensed separately.

## Notes

- The authority host is the only network endpoint and TLS identity.
- Additional path segments are request components only.
- Optional client certificates may be used for implementation-defined identity-aware behavior.

## Example

URI:

```text
fingers://example.com/alice?PLAN&mode=full
```

Request sent:

```text
/PLAN /mode=full alice<CRLF>
```

## Development

This draft is meant to be simple and easy to evolve. The goal is a small, readable protocol document that people can implement without needing a large software stack.
