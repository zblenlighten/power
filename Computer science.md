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
  5. Hash table
      - [Collision](http://www.ruanyifeng.com/blog/2018/09/hash-collision-and-birthday-attack.html): Open addressing, Separate chaining, 2-choice hashing
      - [Perfect hash function](https://en.wikipedia.org/wiki/Perfect_hash_function)
      - Bloom Filter

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
  - Java (JVM heap)
    - Young Generation: minor GC
      - Eden
      - From (Survivor)
      - To
    - Old Generation: major GC
    - Permanent Generation: full GC
    - Collector: G1 (Serial, Parallel, CMS)
  - Python
    - Reference counting
    - Tracing: Mark-and-sweep, Generational GC

- Process & Thread (task execution)
  - Inter process communication (IPC)
    - Remote procedure call (RPC)
  - Concurrency
    - Process (fork, exec, waitpid, IPC)
    - I/O multiplexing
    - Multithreading
    - Can be achieved via context-switching in a single core, and parallelism in a multi-core
    - Deadlock: Mutual exclusion, Hold and wait or resource holding, No preemption, Circular wait
    - Time-sharing: CPU
    - Sharding: RAM

- I/O
  - Blocking (vs: Non-blocking)：connection is blocked until there is some data to read or the data is fully written
    - Possible causes: I/O, lock, network request, database connection
  - Synchronous (vs: Asynchronous)：code executing in sequence (one at a time)
  - File
    - Regular file
    - Directory
      - Linking: Static library (.lib) & Dynamic-link library (.dll)
    - Socket

- Linux
  - [User space vs. Kernel space](http://www.ruanyifeng.com/blog/2016/12/user_space_vs_kernel_space.html)
  - [Pipe](https://www.geeksforgeeks.org/piping-in-unix-or-linux/)
  - [Shell command](https://docs.cs.cf.ac.uk/notes/linux-shell-commands/) ([命令大全](https://man.linuxde.net/), [Explain shell](https://www.explainshell.com/))
    - Files and Directories: cat, grep
    - Manipulating data: wc, sed, sort, uniq, [awk](http://www.ruanyifeng.com/blog/2018/11/awk.html)
    - File Editors
    - Compressed files
    - Information
    - Status
    - Messages between Users
    - Networking
    - [Wildcards](http://www.ruanyifeng.com/blog/2018/09/bash-wildcards.html)

### Network

#### Internet Protocol Suite

1. Physical Layer: Hub
2. Data Link Layer: Switch
    - **MAC** address
    - Network Interface Card (NIC)
3. Network Layer: Router
    - Internet Protocol (**IP**)
      - Network address translation (NAT)
    - Address Resolution Protocol (ARP)
4. Transport Layer
    - Socket: IP + port
      - Transmission Control Protocol ([TCP](http://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html))
      - User Datagram Protocol (UDP)
      - Call: connect, bind, listen, accept, send, recv
      - Echo server
    - [SSL/TLS](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html)
      - OpenSSL
      - Network security services (NSS)
7. Application Layer
    - [HTTP](https://www.ruanyifeng.com/blog/2016/08/http.html) (TCP/IP): request & response
      - HTTP/2
      - [HTTPS](http://www.ruanyifeng.com/blog/2016/08/migrate-from-http-to-https.html)
      - Web server: Common Gateway Interface (CGI)
      - Client IP: X-Real-IP Header, X-Forwarded-For Header, remote_addr
    - RESTful ([API](http://www.ruanyifeng.com/blog/2014/05/restful_api.html))
      - Resources: Uniform Resource Identifier (URI)
      - Representation: [MIME type / content type](https://en.wikipedia.org/wiki/Media_type)
      - State Transfer: request methods
    - File Transfer Protocol (FTP)
    - Dynamic Host Configuration Protocol (DHCP)
    - Communication
      - client → server: pull/get
      - server/publisher → client: push ([WebSocket](https://www.ruanyifeng.com/blog/2017/05/websocket.html))

#### What happens when type in a URL?

1. Capacitive touchscreen → CPU → OS kernel → OS GUI → Browser
2. Browser:
    - **DNS resolution**: cache (browser, OS, router)/DNS server → IP address
    - **TCP three-way handshake**
    - **HTTP request**
      - Request message: request line, request header fields, empty line, message body
3. Browser → NIC → Wifi router → Global IP Network (Internet) → NIC → Host server
4. Host server:
    - Inverse proxy
    - Load balancer ([Consistent hashing](https://en.wikipedia.org/wiki/Consistent_hashing): using virtual nodes to create better key distribution in a hash ring)
      - Nginx (epoll)
    - Web framework
      - MVC: Model, View, Controller
5. Host server → Host client:
    - **The server handles the request and sends back an HTTP response**
      - HTTP status
        - 2xx (Successful): The request was successfully received, understood and accepted
        - 3xx (Redirection): Further action needs to be taken in order to complete the request
        - 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
        - 5xx (Server Error): The server failed to fulfill an apparently valid request
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
    - Public-key cryptography
    - Cryptographic hash function
      - Common functions: MD5 (rainbow table), Secure Hash Algorithm (SHA)
      - MAC functions: Hash-based message authentication code (HMAC)
  - Authentication (verifies you are who you say you are)
    - Login form
    - HTTP authentication
  - Authorization (decides if you have permission to access a resource)
    - URL access controls
    - Access control list (ACL)
      - Filesystem ACL
      - Networking ACL
      - SQL ACL
  - Protocols
    - Central Authentication Service (CAS): single sign-on (SSO)
    - [JSON Web Token](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html) (JWT)
    - [OAuth 2.0](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)
    - ~~OpenID~~
    - Kerberos (kinit, rlogin, ...)

- References
  - systemd: [一](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html), [二](https://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html), [三](http://www.ruanyifeng.com/blog/2018/03/systemd-timer.html)
  - curl(client + url): [指南1](http://www.ruanyifeng.com/blog/2011/09/curl.html), [指南2](https://www.ruanyifeng.com/blog/2019/09/curl-reference.html)
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

&emsp;(1) [技術情報Wiki](https://www.sangyo-rock.com/tech/index.php)  
&emsp;(2) [記号と読み方](https://memotec.net/etc/mark.html)  
&emsp;(3) [Falsehoods CS Students (Still) Believe Upon Graduating](https://www.netmeister.org/blog/cs-falsehoods.html)
