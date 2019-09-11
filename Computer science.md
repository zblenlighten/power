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
| 2. Merge sort  | n·log(n)  | n·log(n)  | Yes  | Merging  |
| 3. Quick sort  | n·log(n)  | n^2  | Typical not  | Partitioning  |
| 4. Selection sort  | n^2  | n^2  | No  | Selection  |
| 5. Heap sort  | n·log(n)  | n·log(n)  | No  | Selection  |
| 6. Insertion sort  | n^2  | n^2  | Yes  | Insertion  |
| 7. Shell sort  |   |   | No  | Insertion  |
  8. External sort

- Data structure
  1. Arrays
  2. Linked lists
  3. Stack
  4. Queue
  5. Hash table ([perfect hash function](https://en.wikipedia.org/wiki/Perfect_hash_function))

- Trees
  1. Binary search trees
  2. Balanced search trees
      - AVL tree
      - Red-black tree
      - ...
  3. traversals: [preorder](https://leetcode.com/problems/binary-tree-preorder-traversal/), [inorder](https://leetcode.com/problems/binary-tree-inorder-traversal/), [postorder](https://leetcode.com/problems/binary-tree-postorder-traversal/), BFS, DFS

- Graph
  1. directed
  2. undirected
  3. adjacency matrix
  4. adjacency list
  5. traversals: BFS, DFS

- More knowledge
  1. Binary search
  2. Bitwise operations
  3. Tries
  4. Bitmap
  5. Backtracking
  6. Dynamic programing
  7. ...

- [Big-O](https://www.bigocheatsheet.com/)

### Operating system

- Process & Thread
- Deadlock
- The linking process exposed: Static library (.lib) & Dynamic-link library (.dll)
- [Inter process communication](https://en.wikipedia.org/wiki/Inter-process_communication) (IPC)
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

1. Physical Layer
2. Link Layer
    - MAC address
3. Network Layer
    - Internet Protocol (IP): IPv4, IPv6
      - [Network address translation (NAT)](https://en.wikipedia.org/wiki/Network_address_translation)
    - [Address Resolution Protocol (ARP)](https://en.wikipedia.org/wiki/Address_Resolution_Protocol)
4. Transport Layer
    - Socket: IP + port
    - Transmission Control Protocol (TCP)
5. Application Layer
    - HTTP (TCP/IP)
      - HTTP/2
      - [HTTPS](http://www.ruanyifeng.com/blog/2016/08/migrate-from-http-to-https.html)
    - <s>WebSocket</s>

#### What happens when type in a URL?

1. Capacitive touchscreen → CPU → OS kernel → OS GUI → browser
2. Browser:
    - <strong>DNS resolution</strong>: cache (browser, OS, router)/DNS server → IP address
    - <strong>TCP three-way handshake</strong>
    - <strong>HTTP request</strong>
      - Request message: request line, request header fields, empty line, message body

3. Network Interface Card (NIC) → Wifi router → Internet → Host
4. Host:
    - Inverse proxy: Nginx
      - Load balancer
      - Virtual IP
    - Web server: Apache, Tomcat, Node.js, Common Gateway Interface (CGI), etc.
      - MVC: Model, View, Controller
    - Web framework
5. Server → Client:
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

| Power of 2  | Accurate value  | Approximate value  | Size |
|---|---|---|---|
| 7  | 128  |   |   |
| 8  | 256  |   |   |
| 10  | 1024  | thousand  | 1K  |
| 16  | 65 536  |   | 64K  |
| 20  | 1 048 576  | million  | 1MB  |
| 30  | 1 073 741 824  | billion  | 1GB  |
| 32  | 4 294 967 296  |   | 4GB  |
| 40  |   | trillion  | 1TB  |

&emsp; [技術情報Wiki](https://www.sangyo-rock.com/tech/index.php)
