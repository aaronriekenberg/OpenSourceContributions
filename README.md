# Open Source Contributions
My contributions to open source projects in reverse chronological order.

- 2021 (Go quic-go): [Made port HTTP3 Alt-Svc header configurable](https://github.com/quic-go/quic-go/pull/3272/files)
  - Needed when Layer 4 firewall is redirecting UDP port for HTTP3 servers (e.g. `443 -> 8443`)
  - quic-go library is used as go HTTP3 library in [Caddy](https://caddyserver.com/) and [cloudflared](https://github.com/cloudflare/cloudflared) for example
- 2021 (Java Hazelast): [Added Nonnull annotations to StreamSerializer](https://github.com/hazelcast/hazelcast/pull/18071)
  - A colleague and I were unsure if parameters and return values from read/write methods were nullable.  So I proposed above PR to Hazelcast to enforce this at compile-time.
  - Change allows [Java FindBugs](https://github.com/findbugsproject/findbugs) can use these annotations at compile time to check null handling.
  - Also alows Kotlin code using Hazelcast to enforce [null-safety](https://kotlinlang.org/docs/null-safety.html).
- 2018 (Go CoreDNS): [Added MINTTL option](https://github.com/coredns/coredns/pull/2055)
  - Can be used to clamp minimum TTL when caching DNS responses similar to [`cache-min-ttl` option in Unbound](https://nlnetlabs.nl/documentation/unbound/unbound.conf/)
  - [MINTTL option still exists in CoreDNS](https://coredns.io/plugins/cache/)
- 2018 (Rust Hyper): [Update send_file example](https://github.com/hyperium/hyper/pull/1533/files)
  - Made example using async file operations provided by [tokio](https://tokio.rs/)
- 2017 (Rust Hyper): [Fixed infinite loop](https://github.com/hyperium/hyper/pull/1343)
  - Infinite loop happened converting from [`Cow::Owned`](https://doc.rust-lang.org/std/borrow/enum.Cow.html) string or bytes to hyper http body.
- 2016 (Java Apache Camel): [Fixed Kafka key and partition field names](https://github.com/apache/camel/pull/785/files) in [Apache Camel Kafka Component](https://github.com/apache/camel/pull/785/files)
  - Made these fields easier to use as properties on Camel exchange.
- 2014 (C/Java Netty): [Fixed issue 2280 in Netty](https://github.com/netty/netty/pull/2294/files)
  - In early days of Netty having an [epoll transport written in C and JNI](https://netty.io/wiki/native-transports.html), the epoll client transport was [incorrectly firing `channelActive` events even if connecting to server failed](https://github.com/netty/netty/issues/2280).
  - I fixed this bug in [Netty's C and Java code using JNI](https://github.com/netty/netty/pull/2294/files)
  - In modern times much of the JVM REST API world is running on Netty epoll transport (e.g. Spring Boot Webflux, Cassandra, Micronaut, others)
- 2011 (Java Netty): [Contributed failImmediatelyOnTooLongFrame option to Netty decoders](https://github.com/netty/netty/pull/25)
  - These options [still](https://github.com/netty/netty/blob/4.1/codec/src/main/java/io/netty/handler/codec/DelimiterBasedFrameDecoder.java#L67) [exist](https://github.com/netty/netty/blob/4.1/codec/src/main/java/io/netty/handler/codec/LengthFieldBasedFrameDecoder.java#L196) in Netty
  - Options been renamed to better name [`failFast`](https://github.com/netty/netty/commit/0850449b096218c1bf1c5de5e9603ff490f8efcb) which is a good move in retrospect :)
- 2011 (C++ boost): [Contributed lock-free version](https://lists.boost.org/boost-bugs/2011/12/20673.php) of `boost::shared_ptr` for IBM AIX operating system to improve performance by 5x.
  - [`boost::shared_ptr`](https://theboostcpplibraries.com/boost.smartpointers-shared-ownership) is reference-counted, thread-safe smart pointer similar to [Arc in Rust](https://doc.rust-lang.org/std/sync/struct.Arc.html).
  - My code [still exists in the boost source code](https://github.com/boostorg/smart_ptr/blob/develop/include/boost/smart_ptr/detail/sp_counted_base_aix.hpp).
  - Eventually `boost::shared_ptr` became [`std::shared_ptr`](https://en.cppreference.com/w/cpp/memory/shared_ptr) in c++11.
