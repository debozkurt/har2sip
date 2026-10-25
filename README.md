# har2sip

Extract SIP-over-WebSocket frames from a browser HAR into a pcap.
Python 3, no dependencies.

Browser softphones send SIP over a secure WebSocket, so a normal packet capture never shows the SIP
messages. Chrome DevTools records those WebSocket frames in a HAR file. har2sip re-wraps each SIP
frame as IPv4/UDP on port 5060, so Wireshark and sngrep can dissect it.

The SIP bytes, direction, and timestamps come from the HAR. The client address is synthetic, because
a HAR never records the browser's own IP. The server address comes from the Via and Contact headers,
or from `--peer-ip`.

> **Before you share a HAR or a pcap:** HAR files can hold cookies and auth tokens, and SIP headers
> can hold phone numbers and digest authentication data. Remove them first.

## Install

```bash
curl -o ~/.local/bin/har2sip https://raw.githubusercontent.com/debozkurt/har2sip/main/har2sip
chmod +x ~/.local/bin/har2sip
```

Or from a local copy:

```bash
cp har2sip ~/.local/bin/
chmod +x ~/.local/bin/har2sip
```

## Use

```bash
har2sip trace.har                    # -> trace.sip.pcap + trace.sip.txt
har2sip trace.har --open sngrep
har2sip trace.har --open wireshark
har2sip *.har                        # batch
har2sip --help
```

## License

MIT. See [LICENSE](LICENSE).
