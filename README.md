# har2sip

Extract SIP-over-WebSocket frames from a browser HAR into a pcap.
Python 3, no dependencies.

## Install

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
