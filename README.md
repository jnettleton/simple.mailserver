# Simple.MailServer

Simple SMTP Mail Server in C# 5 (using async features)

**Fork of [hanswolff/simple.mailserver](https://github.com/hanswolff/simple.mailserver)**, which its author marked discontinued and which is now archived (last upstream commit August 2017).

Changed in July 2021 to address a server that kept waiting on connections whose clients had gone away. Changes:

- The command read loop is awaited instead of fire-and-forget.
- The 100 ms delayed disconnect after QUIT is replaced by a `Disconnecting` flag.
- A configurable `DisconnectIdleTimeout` (default 2 s) is enforced by the idle watchdog for connections marked as disconnecting.
- Dead connections with no FIN are still reaped by the existing `ConnectionIdleTimeout` (default 60 s).
- The vendored `packages/` folder is removed (use NuGet restore), and the version is bumped to 1.0.0.

No new tests. Not published to NuGet.

## Installation

    PM> Install-Package Simple.MailServer    (installs the upstream package; build from source for this fork)

## Supported Features

- basic SMTP protocol (extendible through provided interfaces)
- multiple port bindings
- extensive use of C# 5 async (for better performance than just threads)
- certain MIME features for encoding, date parsing (RFC 2822, RFC 5335)

## Planned Features

- SMTP Authentication
- SSL/TLS support
- basic POP3 protocol

# Related Projects

If you need to parse mail messages, have a look at MimeKit:  
https://github.com/jstedfast/MimeKit

# Contact

Please let me know if there are bugs or if you have suggestions how to improve the code.

And maybe follow me [@quadfinity](https://twitter.com/quadfinity) :)
