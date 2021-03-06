# Knowledge Memo

## Contents

- [Algorithms and Data structure](#algorithms-and-data-structure)
- [Operating system](#operating-system)
- [Network](#network)
- [Wiki](#wiki)

## Computer science

### Algorithms and Data structure

- Sorting

| Name  | Average  | Worst  | Stable (array) | Method  |
|---|---|---|---|---|
| 1. Bubble sort  | n^2  | n^2  | Yes  | Exchanging  |
| 2. Quick sort  | n·log(n)  | n^2  | Typical not  | Partitioning  |
| 3. Merge sort  | n·log(n)  | n·log(n)  | Yes  | Merging  |
| 4. Heap sort  | n·log(n)  | n·log(n)  | No  | Selection  |
| 5. Selection sort  | n^2  | n^2  | No  | Selection  |
| 6. Insertion sort  | n^2  | n^2  | Yes  | Insertion  |
| 7. Shell sort  |   |   | No  | Insertion  |
| 8. Counting sort  | n+k  | n+k  | Yes  | Non-comparison  |
  9. External sort

- Data structure
  1. Arrays
  2. Linked lists
  3. Stack
  4. Queue
  5. Hash (hash function: easy to compute, even distribution, less collision)
      - [Collision](http://www.ruanyifeng.com/blog/2018/09/hash-collision-and-birthday-attack.html): Separate chaining, Open addressing, 2-choice hashing ([Perfect hash function](https://en.wikipedia.org/wiki/Perfect_hash_function))
      - Bloom Filter
      - SimHash
      - GeoHash
      - Fingerprint
        - Pseudorandom number generator (PRNG): Mersenne Twister
        - [Content ID system](https://en.wikipedia.org/wiki/Content_ID_(system))

- Trees
  1. Binary search trees
  2. Self-balancing binary search tree
      - **AVL tree**
      - Red-black tree
  3. B tree
      - B+ tree
  4. Trie ([Implementation](https://leetcode.com/articles/implement-trie-prefix-tree/))
  5. Heap
  6. traversals: [preorder](https://leetcode.com/problems/binary-tree-preorder-traversal/), [inorder](https://leetcode.com/problems/binary-tree-inorder-traversal/), [postorder](https://leetcode.com/problems/binary-tree-postorder-traversal/), BFS, DFS

- Graph
  1. directed
  2. undirected
  3. adjacency matrix
  4. adjacency list
  5. traversals: BFS, DFS
  6. Shortest path problem: Dijkstra's algorithm, Floyd–Warshall algorithm
  7. Minimum spanning tree (MST): Prim's algorithm, Kruskal's algorithm

- More knowledge
  1. Topological sort
  2. Bitmap
  3. Binary search
  4. Bitwise operations ([Python](https://wiki.python.org/moin/BitwiseOperators))
  5. Backtracking
  6. Dynamic programing
  7. Union find
  8. Greedy
  9. [Regular expression](https://regexr.com/) ([Python](https://www.runoob.com/python/python-reg-expressions.html))

- Time complexity
  - General [Big-O](https://linux.cn/article-7480-1.html) ([Python](https://wiki.python.org/moin/TimeComplexity))

### Operating system

- CPU
  - Memory barrier: Out-of-order execution

- Memory
  - Memory segmentation
    - Code segment - Data segment - .bss - Heap - Stack
  - Garbage Collection (Implicit Memory Allocator, vs: Explicit Allocator)
    - Java
      - GC Roots
      - JVM Heap
        - Young Generation: minor GC
          - Eden - From (s0) - To (s1)
        - Old Generation: major GC
        - Permanent Generation: full GC
      - Garbage Collector: G1 (Serial, Parallel, CMS)
    - Python
      - Tracing: Mark-and-sweep, Generational GC
      - Reference Counting
    - C
      - Manual Memory Management

- I/O
  - Communication
    - Blocking (vs: Non-blocking): connection is blocked until there is some data to read or the data is fully written
      - Possible causes: I/O, lock, network request, database connection
    - Synchronous (vs: Asynchronous): code executing one at a time in sequence, blocking communication
    - Overhead: compute time/resources spent on communication
    - Latency: time to send message from A to B (μs)
    - Bandwidth: amount to data communicated per seconds (GB/s)
  - File
    - Regular file
    - Directory
      - Linking: Static library (.lib) & Dynamic-link library (.dll)
    - Socket

- Process & Thread (task execution)
  - Process
    - States: Running([User space vs Kernel space](http://www.ruanyifeng.com/blog/2016/12/user_space_vs_kernel_space.html)), Waiting, Blocked
  - Thread (subset of a process)
    - Threads share: address space, heap, static data, code segments, and file descriptors
    - Threads have their own: program counter, registers, stack, and state
    - Thread pool: reuses threads to reduce the overhead that would be required to create a new separate thread for every concurrent task
  - CPU bound, Memory bound, I/O bound
  - Inter process communication (IPC)
    - Remote procedure call (**RPC**)
    - Sockets and pipes, Shared memory
  - Concurrency
    - Achieved via context switching in a single core or parallelism in a multi-core
    - Construct concurrent programs
      - Process: each process has a separate memory address space
      - I/O multiplexing: event-driven server runs in the context of a single process
      - Multithreading: process + I/O multiplexing, shared variable synchronization error
    - Mutual exclusion
      - Lock (Mutex)
      - Reentrant lock
      - Readers–writer lock
      - Deadlock (Livelock)
        - Deadlock can occur when multiple threads need to acquire multiple locks
        - Possible causes: mutual exclusion, hold and wait or resource holding, no preemption, circular wait
        - Possible strategies: Lock ordering, Lock timeout
        - Starvation: context manager
      - Semaphore (vs: Lock): can be acquired/released by different threads
    - Synchronization
      - Monitor = Condition variables + Lock
      - Producer–consumer pattern
    - Hardware
      - CPU: Time-sharing
      - RAM: Sharding
    - Amdahl's law
  - Scheduler
    - Scheduling algorithms (context switch)
    - Scheduling goals

- File System
  - Linux ([inode](https://www.ruanyifeng.com/blog/2011/12/inode.html))
  - Redundant Array of Independent Disks (RAID): 0, 1, 10, 5, 6
  - Distributed File System
    - Andrew File System (AFS)
    - InterPlanetary File System (IPFS)

- Linux (pipe)
  - Distribution (/etc/*-release)
    - Debian → Ubuntu
    - Fedora → Red Hat → CentOS
    - Android
  - [Shell command](https://docs.cs.cf.ac.uk/notes/linux-shell-commands/) ([Explain shell](https://www.explainshell.com/)): [Wildcards](http://www.ruanyifeng.com/blog/2018/09/bash-wildcards.html)
    - Files and directories: cat, touch, grep, find, mount
    - Manipulating data: cut, [awk](http://www.ruanyifeng.com/blog/2018/11/awk.html), sort, uniq, wc, sed, tr, paste
    - File editors: [vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)
    - Compressed files: tar
    - Information: man
    - Status: ps, top, netstat
    - Messages between users
    - Networking: scp, curl, ssh
    - Job scheduler: cron, crontab

### Network

- Internet Protocol Suite
  1. Physical Layer: Hub → Bit
  2. Data Link Layer: Switch → Frame
      - Network Interface Card (NIC)
      - **MAC** (media access control) address
      - Address Resolution Protocol (ARP)
      - Bridging
  3. Network Layer: Router → Datagram
      - Internet Protocol (**IP**)
        - Network address translation (NAT)
          - Public IP (ISP: Internet service provider) vs Private IP (DHCP server / Router / LAN administrator)
      - Routing: Static routing & Dynamic routing
  4. Transport Layer → Segment
      - User Datagram Protocol (UDP)
      - [Transmission Control Protocol](http://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html) (**TCP**)
        - Round-trip delay (RTD)
      - Socket = IP + port
        - Port acts as an interface between the application process and transport layer of the OSI model (internal port vs external port)
        - Echo server
        - Socket Programming: connect, bind, listen, accept, send, recv
      - Reliable Data Protocol (RDP)
  7. Application Layer → Message
      - [HTTP](https://www.ruanyifeng.com/blog/2016/08/http.html) (TCP/IP): [HTTPS](http://www.ruanyifeng.com/blog/2016/08/migrate-from-http-to-https.html)
      - File Transfer Protocol (FTP)
      - Simple Mail Transfer Protocol (SMTP)
      - Domain Name System (DNS)
      - IP address
        - Static IP: IP + Subnet mask + Gateway + DNS
        - Dynamic IP: Dynamic Host Configuration Protocol (DHCP)

- Knowledge
  - Messaging pattern
    - request–response (in-out): HTTP, RPC
    - one-way (in-only): UDP
    - publish–subscribe: [WebSocket](https://www.ruanyifeng.com/blog/2017/05/websocket.html), Message Queuing Telemetry Transport (MQTT)
  - Network model
    - client–server
    - peer-to-peer: Extensible Messaging and Presence Protocol (XMPP)

- The Hypertext Transfer Protocol (HTTP): stateless
  - [Message](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)
    - Start line - [Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) - Body
  - Status response codes
    - 1xx (Informational)
    - 2xx (Success): The request was successfully received, understood and accepted
      - 200 - OK
      - 201 - Created
    - 3xx (Redirection): Further action needs to be taken in order to complete the request
      - 301 - Moved permanently
      - 302 - Moved temporarily
      - 304 - Not modified (cached version)
    - 4xx (Client error): The request contains bad syntax or cannot be fulfilled
      - 400 - Bad request
      - 401 - Unauthorized
      - 404 - Not found
    - 5xx (Server error): The server failed to fulfill an apparently valid request
      - 500 - Interval server error
  - Security
    - [Content security policy](http://www.ruanyifeng.com/blog/2016/09/csp.html) (CSP)
    - [Same-origin policy](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html): [Cross-origin resource sharing](http://www.ruanyifeng.com/blog/2016/04/cors.html) (CORS)
    - [Cross-site request forgery](https://www.ruanyifeng.com/blog/2019/09/cookie-samesite.html) (CSRF)
  - A typical HTTP [session](https://developer.mozilla.org/en-US/docs/Web/HTTP/Session)
  - Cookie: HTTP state management mechanism (first party cookie vs third party cookie)
    - Intelligent Tracking Prevention (ITP)
    - Server side (HTTP Set-Cookie header) - Client side (JavaScript document.cookie)
  - Applications
    - Proxy (server): Filter requests (IP address blocking, decrease request latency), Cache (optimize request traffic)
    - Web cache: reduce server lag
    - Gateway: perform protocol conversions to connect networks with different network protocol technologies, usually also act as a proxy server and a firewall
      - Protocol gateway
      - Resource gateway
        - Common Gateway Interface (CGI)
    - Tunnel & Relay

- What happens when type in a URL?
  1. Capacitive touchscreen → CPU → OS kernel → OS GUI → Browser
  2. Browser:
      - **DNS resolution**: cache (browser, OS, router)/DNS server → IP address
      - **TCP three-way handshake**
      - **HTTP request**
  3. Browser → NIC → Wifi router → Global IP Network (Internet) → NIC → Host server
  4. Host server:
      - Load balancing ([Consistent hashing](https://vitalflux.com/wtf-consistent-hashing-databases/): using virtual nodes to create better key distribution in a hash ring)
        - Inverse proxy (HTTP)
      - Web application firewall (WAF)
      - [Web server](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview): Apache
      - Application server: Servlet container
  5. Host server → Host client:
      - **The server handles the request and sends back an HTTP response**
      - **The browser displays the HTML content**
        - The browser sends a request to the web server to retrieve a HTML document
        - The document is an annotated source code file and needs to be parsed to construct a parsed node tree (DOM: Document Object Model)
        - Use the constructed DOM and CSSOM (turn CSS into the CSS Object Model) to create a render tree which contains only the nodes required to render the page
        - The DOM is then rendered as a web page and can be viewed in the browser window, it also provides an interface for interacting with the elements in the tree
          - Layout the render tree (i.e. computes the exact position and size of each object)
          - Paint the render tree (i.e. takes in the final render tree and renders the pixels to the screen)
          - [HTML DOM 事件](https://www.runoob.com/jsref/dom-obj-event.html)
      - **TCP four-way handshake**
  6. Browser → LCD screen

- Security
  - Cryptography
    - Cryptographic hash function
      - Common functions: MD5 (rainbow table), bcrypt (salt), Secure Hash Algorithm (SHA)
      - MAC functions: Hash-based message authentication code (HMAC)
    - Symmetric-key algorithm
    - Public-key cryptography
      - Integer factorization: RSA, Rabin
      - Discrete logarithm: ElGamal
      - Digital signature (Electronic signature: DocuSign)
      - Public key infrastructure (PKI)
        - Certificate authority (CA)
  - Authentication and authorization
  - Protocols
    - Central Authentication Service (CAS): single sign-on (SSO)
    - [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)
    - OpenID
    - [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)
    - Kerberos
  - Secure Communication
    - SSH
    - [SSL/TLS](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html)
      - OpenSSL
      - Network security services (NSS)
    - Virtual Private Network (VPN)
  - [OWASP Top 10](https://owasp.org/www-project-top-ten/)

- References
  - [一个 TCP 连接上面能发多少个 HTTP 请求](https://zhuanlan.zhihu.com/p/61423830)

### Wiki

| Power  | Exact value  | Approximate value  | Bytes |
|---|---|---|---|
| 7  | 128  |   |   |
| 8  | 256  |   |   |
| 10  | 1024  | thousand  | 1K  |
| 16  | 65 536  |   | 64K  |
| 20  | 1 048 576  | million  | 1MB  |
| 30  | 1 073 741 824  | billion  | 1GB  |
| 32  | 4 294 967 296  |   | 4GB  |
| 40  |   | trillion  | 1TB  |

```
Latency Comparison Numbers
--------------------------
L1 cache reference                           0.5 ns
Branch mispredict                            5   ns
L2 cache reference                           7   ns                      14x L1 cache
Mutex lock/unlock                           25   ns
Main memory reference                      100   ns                      20x L2 cache, 200x L1 cache
Compress 1K bytes with Zippy            10,000   ns       10 us
Send 1 KB bytes over 1 Gbps network     10,000   ns       10 us
Read 4 KB randomly from SSD*           150,000   ns      150 us          ~1GB/sec SSD
Read 1 MB sequentially from memory     250,000   ns      250 us
Round trip within same datacenter      500,000   ns      500 us
Read 1 MB sequentially from SSD*     1,000,000   ns    1,000 us    1 ms  ~1GB/sec SSD, 4X memory
Disk seek                           10,000,000   ns   10,000 us   10 ms  20x datacenter roundtrip
Read 1 MB sequentially from 1 Gbps  10,000,000   ns   10,000 us   10 ms  40x memory, 10X SSD
Read 1 MB sequentially from disk    30,000,000   ns   30,000 us   30 ms 120x memory, 30X SSD
Send packet CA->Netherlands->CA    150,000,000   ns  150,000 us  150 ms
```

&emsp;(1) [Falsehoods CS Students (Still) Believe Upon Graduating](https://www.netmeister.org/blog/cs-falsehoods.html)  
&emsp;(2) [記号と読み方](https://memotec.net/etc/mark.html)  
