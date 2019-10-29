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
      - <strong>AVL tree</strong>
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
  - General [Big-O](https://www.bigocheatsheet.com/) ([Python](https://wiki.python.org/moin/TimeComplexity))

### Operating system

- Garbage Collection
  - Java (JVM heap parts)
    - Young Generation: minor GC
      - Eden
      - Survivor
      - semi-Spaces
    - Old or Tenured Generation: major GC
    - Permanent Generation
  - Python
    - Reference counting
    - Tracing: Mark-and-sweep, Generational GC
- Process & Thread (multithreading)
- Deadlock
- The linking process exposed: Static library (.lib) & Dynamic-link library (.dll)
- Inter process communication (IPC)
  - Remote procedure call (RPC)
- Linux
  - Log
  - [Shell](https://docs.cs.cf.ac.uk/notes/linux-shell-commands/)
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
    - MAC address
3. Network Layer: Router
    - Internet Protocol (IP): IPv4, IPv6
      - Network address translation (NAT)
    - Address Resolution Protocol (ARP)
4. Transport Layer
    - Socket: IP + port
    - Transmission Control Protocol ([TCP](http://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html))
7. Application Layer
    - HTTP (TCP/IP)
      - HTTP/2
      - [HTTPS](http://www.ruanyifeng.com/blog/2016/08/migrate-from-http-to-https.html)
    - DHCP (UDP)
    - <s>WebSocket</s>

#### What happens when type in a URL?

1. Capacitive touchscreen → CPU → OS kernel → OS GUI → Browser
2. Browser:
    - <strong>DNS resolution</strong>: cache (browser, OS, router)/DNS server → IP address
    - <strong>TCP three-way handshake</strong>
    - <strong>HTTP request</strong>
      - Request message: request line, request header fields, empty line, message body
3. Browser → Network Interface Card (NIC) → Wifi router → Internet → Host server
4. Host server:
    - Inverse proxy: Nginx
      - Load balancer ([Consistent hashing](https://en.wikipedia.org/wiki/Consistent_hashing): using virtual nodes to create better key distribution in a hash ring)
      - Virtual IP
    - Web server: Common Gateway Interface (CGI)...
    - Web framework
      - MVC: Model, View, Controller
5. Host server → Host client:
    - <strong>The server handles the request and sends back an HTTP response</strong>
      - HTTP status
        - 2xx (Successful): The request was successfully received, understood and accepted
        - 3xx (Redirection): Further action needs to be taken in order to complete the request
        - 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
        - 5xx (Server Error): The server failed to fulfill an apparently valid request
    - <strong>The browser displays the HTML content</strong>: [Chromium](https://www.chromium.org/developers/design-documents/multi-process-architecture)
      - Parsing HTML to construct the DOM tree
      - Turning CSS into the CSS Object Model
      - Use the constructed DOM and CSSOM to create a render tree (contains only the nodes required to render the page)
      - Layout the render tree (computes the exact position and size of each object)
      - Paint the render tree (takes in the final render tree and renders the pixels to the screen)
    - <strong>TCP four-way handshake</strong>
6. Browser → LCD screen

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

| Operation  | SQL  | HTTP  | RESTful WS  | DDS  |
|---|---|---|---|---|
| <strong>C</strong>reate | INSERT | PUT / POST | POST | write |
| <strong>R</strong>ead (Retrieve) | SELECT | GET | GET | read / take |
| <strong>U</strong>pdate (Modify) | UPDATE | PUT / POST / PATCH | PUT | write |
| <strong>D</strong>elete (Destroy) | DELETE | DELETE | DELETE | dispose |

&emsp; [技術情報Wiki](https://www.sangyo-rock.com/tech/index.php)  
&emsp; [記号と読み方](https://memotec.net/etc/mark.html)  
