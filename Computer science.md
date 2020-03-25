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
  5. Hash
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
      - ...
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
  10. ...

- Time complexity
  - General [Big-O](https://linux.cn/article-7480-1.html) ([Python](https://wiki.python.org/moin/TimeComplexity))

### Operating system

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
    - Reference counting
    - Tracing: Mark-and-sweep, Generational GC

- Process & Thread (task execution)
  - Process states: Running([User space vs Kernel space](http://www.ruanyifeng.com/blog/2016/12/user_space_vs_kernel_space.html)), Waiting, Blocked
  - Inter process communication (IPC)
    - Remote procedure call (RPC)
  - Concurrency
    - Achieved via context switching in a single core or parallelism in a multi-core
    - Construct concurrent programs
      - Process: each process has a separate memory address space
      - I/O multiplexing: event-driven server runs in the context of a single process
      - Multithreading: process + I/O multiplexing, shared variable synchronization error
    - Mutual exclusion: thread safety
      - Locks (mutexes)
      - Readers–writer locks
      - Reentrant mutexes (Recursive locks)
      - Semaphores
      - Possible causes of Deadlock: mutual exclusion, hold and wait or resource holding, no preemption, circular wait
    - Hardware
      - CPU: Time-sharing
      - RAM: Sharding
  - Scheduler

- I/O
  - Blocking (vs: Non-blocking): connection is blocked until there is some data to read or the data is fully written
    - Possible causes: I/O, lock, network request, database connection
  - Synchronous (vs: Asynchronous): code executing in sequence (one at a time)
  - File
    - Regular file
    - Directory
      - Linking: Static library (.lib) & Dynamic-link library (.dll)
    - Socket

- Linux (pipe)
  - Distribution
    - Debian → Ubuntu
    - Fedora → Red Hat → CentOS
    - Android
  - [Shell command](https://docs.cs.cf.ac.uk/notes/linux-shell-commands/) ([Explain shell](https://www.explainshell.com/)): [Wildcards](http://www.ruanyifeng.com/blog/2018/09/bash-wildcards.html)
    - Files and Directories: cat, touch, grep, find
    - Manipulating data: cut, [awk](http://www.ruanyifeng.com/blog/2018/11/awk.html), sort, uniq, wc, sed
    - File Editors: [vim](http://www.ruanyifeng.com/blog/2018/09/vimrc.html)
    - Compressed files: tar
    - Information
    - Status
    - Messages between Users
    - Networking: scp, curl

### Network

- Internet Protocol Suite
  1. Physical Layer: Hub → Bit
  2. Data Link Layer: Switch → Frame
      - Network Interface Card (NIC)
      - **MAC** (media access control) address
      - Address Resolution Protocol (ARP)
      - LTE random access procedure
  3. Network Layer: Router → Datagram
      - Internet Protocol (**IP**)
        - Network address translation (NAT): public IP address - private IP address
      - Routing: Static routing & Dynamic routing
  4. Transport Layer → Segment
      - [Transmission Control Protocol](http://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html) (TCP)
        - [SSL/TLS](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html)
          - OpenSSL
          - Network security services (NSS)
      - User Datagram Protocol (UDP)
      - Reliable Data Protocol (RDP)
      - Socket = IP + port (act as an interface between the application process and transport layer of the OSI model)
        - Call: connect, bind, listen, accept, send, recv
        - Echo server
  7. Application Layer → Message
      - [HTTP](https://www.ruanyifeng.com/blog/2016/08/http.html) (TCP/IP): [HTTPS](http://www.ruanyifeng.com/blog/2016/08/migrate-from-http-to-https.html)
      - File Transfer Protocol (FTP)
      - Simple Mail Transfer Protocol (SMTP)
      - Domain Name System (DNS)
      - IP address
        - Static IP: IP + Subnet mask + Gateway + DNS
        - Dynamic IP: Dynamic Host Configuration Protocol (DHCP)
      - Communication
        - client → server: pull/get
        - push server/publisher → client: push ([WebSocket](https://www.ruanyifeng.com/blog/2017/05/websocket.html))

- The Hypertext Transfer Protocol (HTTP)
  - [REST API](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
    - Resources: Uniform Resource Identifier (URI) = URL + URN
      - URL = &lt;**scheme**>://&lt;user>:&lt;password>@&lt;**host**>:&lt;port>/&lt;**path**>;&lt;params>?&lt;query>#&lt;fragment>
    - Representation: MIME type
    - State Transfer: request methods
  - A typical HTTP [session](https://developer.mozilla.org/en-US/docs/Web/HTTP/Session)
  - [Message](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages): start line, [header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers), body
    - Transaction: inbound, outbound
    - Methods
    - Status response codes
      - 2xx (Successful): The request was successfully received, understood and accepted
      - 3xx (Redirection): Further action needs to be taken in order to complete the request
      - 4xx (Client error): The request contains bad syntax or cannot be fulfilled
      - 5xx (Server error): The server failed to fulfill an apparently valid request
  - Applications
    - Proxy: server + client
    - Web cache: reduce server lag
    - Gateway: perform protocol conversions to connect networks with different network protocol technologies, usually also act as a proxy server and a firewall
      - Protocol gateway
      - Resource gateway
        - Common Gateway Interface (CGI)
    - Tunnel & Relay
  - Cookie: HTTP state management mechanism
  - URL redirection
  - Security
    - [Content security policy](http://www.ruanyifeng.com/blog/2016/09/csp.html) (CSP)
    - [Same-origin policy](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html): [Cross-origin resource sharing](http://www.ruanyifeng.com/blog/2016/04/cors.html) (CORS)
    - [Cross-site request forgery](https://www.ruanyifeng.com/blog/2019/09/cookie-samesite.html) (CSRF)

- What happens when type in a URL?
  1. Capacitive touchscreen → CPU → OS kernel → OS GUI → Browser
  2. Browser:
      - **DNS resolution**: cache (browser, OS, router)/DNS server → IP address
      - **TCP three-way handshake**
      - **HTTP request**
  3. Browser → NIC → Wifi router → Global IP Network (Internet) → NIC → Host server
  4. Host server:
      - Inverse proxy
      - Load balancer ([Consistent hashing](https://en.wikipedia.org/wiki/Consistent_hashing): using virtual nodes to create better key distribution in a hash ring)
      - Web application firewall (WAF)
      - [Web server](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview)
      - Web framework
  5. Host server → Host client:
      - **The server handles the request and sends back an HTTP response**
      - **The browser displays the HTML content**: [Chromium](https://www.chromium.org/developers/design-documents/multi-process-architecture)
        - Parsing HTML to construct the DOM tree
        - Turning CSS into the CSS Object Model
        - Use the constructed DOM and CSSOM to create a render tree (contains only the nodes required to render the page)
        - Layout the render tree (computes the exact position and size of each object)
        - Paint the render tree (takes in the final render tree and renders the pixels to the screen)
      - **TCP four-way handshake**
  6. Browser → LCD screen

- Network security
  - Cryptography
    - Symmetric-key algorithm
    - Public-key cryptography: RSA, Rabin, ElGamal, ...
    - Cryptographic hash function
      - Common functions: MD5 (rainbow table), bcrypt (salt), Secure Hash Algorithm (SHA)
      - MAC functions: Hash-based message authentication code (HMAC)
  - Authentication (verifies you are who you say you are)
    - Basic authentication & Digest authentication
    - Login form, HTTP authentication, ...
    - Key management (cryptographic keys)
  - Authorization (decides if you have permission to access a resource)
    - Role-based access control (RBAC)
    - URL access controls, ...
    - Access control list (ACL)
      - Filesystem ACL
      - Networking ACL
      - SQL ACL
  - Protocols
    - Central Authentication Service (CAS): single sign-on (SSO)
    - [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)
    - [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)
    - OpenID
    - Kerberos (kinit, rlogin, ...)

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
&emsp;(3) [技術情報Wiki](https://www.sangyo-rock.com/tech/index.php)  
