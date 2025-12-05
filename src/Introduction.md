# Torr-ust-ent

In this .md repo, I will document my journey developing a torrent client in Rust.
This journey serves a couple of different purposes:
1. I want to get better at Rust and develop intuition about all the features unique to the language (What's better for really getting familiar with a language then a huge project?)
2. I want to get better at documenting my work (This is where this book comes in :)

## Roadmap
The following are general points of action in order to build a working (albeit basic) torrent client. Every stage will create more tasks in order to really make this client feature complete.
Thus each of these points will have sub-chapters, and they will not be necessarily chornological in the order I implement them
01. Bencoding
02. .torrent file parsing
03. Tracker communication
04. Peer communication
05. Peer state machine
06. Piece manager
07. File I/O and Disk layout
08. SHA-1 piece verification
09. Multi-Peer download
10. Seeding
11. CLI Interface
12. Logging and Telemetry
13. Web UI

## Your Input
If you read this .md book and take an interest in my work, first of all, thank you :)
Second of all, I will try to explain and dive deep into every topic, but If something is not explained well enough/you have suggestions/any other reason I'm not thinking of right now, I would really appreciate you contancting me or opening an issue, In the end, I'm here to learn and get better.