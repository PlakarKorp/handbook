## Plakar / Kloset – New developer catch-up checklist

### 0) Day-0 before we start

* [ ] We hold working sessions on Discord vocal channels: make sure you have your webcam, headphones and microphones configured (get good ones, we will provide)
* [ ] We join the Koffee Machine room anywhere between 9am-9:30am for tchit-tchat but we hold our daily from 9:30 to 10:00, so it's good practice to be there a bit earlier.


### 1) Day-0 setup

* [ ] Install the Go toolchain + your editor tooling (linting, formatting, debugging)
* [ ] Install plakar with go install
* [ ] Run a “hello snapshot” locally (create a repo, run a backup, list/browse, restore a file, launch a UI)
* [ ] Dig through subcommands to get a broad view of what is available (not how they work yet)
* [ ] Clone the plakar repository, build from source and run a "hello snapshot" again from there

---

### 2) Mental model of the system (the “big picture”)

* [ ] Clone the kloset repository
* [ ] Understand what *Kloset* is (the storage engine behind Plakar) and its promises: deduplication, encryption, integrity, indexing/navigation, portable storage, extensible APIs. 
* [ ] Memorize the ingestion pipeline stages (you should be able to explain them on a whiteboard):

  * [ ] Snapshot creation and the creation of internal **VFS* abstractions
  * [ ] Chunking + source-side dedup (CAS) 
  * [ ] Compression 
  * [ ] Encryption at the source (zero-knowledge posture) 
  * [ ] Immutable writes into the store
  * [ ] Reconstruction of data upon accesses and restores

---

### 3) Core concepts you should be fluent in

#### CDC (Content-Defined Chunking)

* [ ] Know *why* CDC (data shifts, not fixed blocks; dedup across time/snapshots)
* [ ] Locate the CDC implementation/library used by Plakar/Kloset (and skim its README + tests)
* [ ] Write a small piece of code that chunkifies input data and computes a checksum of each chunk
* [ ] Know *how* this ties into a CAS (Content-Addressed Storage)

#### VFS (Virtual Filesystem)

* [ ] Understand how the snapshot maps sources into directories/files and builds a browsable tree on top of CAS. 
* [ ] Be able to explain snapshot read/write at a high level:

  * [ ] Snapshot commit stores a header + **root VFS id** 
  * [ ] Browsing/listing = iterating nodes; reading a file = traversing nodes to locate its descriptor 
  * [ ] Reconstruction = fetch blocks, decrypt + decompress in sequence 

#### B+Tree indexing

* [ ] Know *what* is indexed with the B+Tree and why (logarithmic access, selective reads at scale). 
* [ ] Identify the boundaries: what lives “in the store” vs what is “in the index” vs what is “derived in-memory”.

#### CAS + crypto posture

* [ ] Internalize “content-addressed storage” and that objects are addressed by cryptographic fingerprints. 
* [ ] Understand why encryption/integrity is non-negotiable in the pipeline (and what guarantees are expected).  

---

### 4) Formats and “things on disk”

* [ ] Learn the repository/store layout at a practical level (what files/dirs exist, what is immutable, what is append-only, what is derived).
* [ ] Understand PTAR as a portable archive form factor (random-access vs classic tar mental model). 

---

### 5) Extensibility: connectors, SDK, and “how to add a new thing”

* [ ] Know what kinds of integrations exist (ingestion connectors, storage backends, restore/export paths). 
* [ ] Skim the Go SDK story (what it abstracts away; what a connector author must provide). 

---

### 6) Hands-on exercises (with peer)

* [ ] Run a backup twice with small edits in between; observe dedup effectiveness (confirm fewer new objects).
* [ ] Trace a single file restore end-to-end:

  * [ ] locate file in VFS
  * [ ] resolve its chunks/objects
  * [ ] decrypt + decompress + reassemble

* [ ] Pick one subsystem and read it “top-down” with a note:

  * [ ] chunking (CDC integration point)
  * [ ] VFS construction + traversal
  * [ ] btree index usage
  * [ ] pack/object storage I/O paths

* [ ] Add (or improve) one test that asserts a core invariant (immutability behavior, deterministic restore, VFS traversal correctness, etc.).

---

### 7) Quick “definition of done” for being onboarded

* [ ] You can explain the ingestion pipeline + where dedup happens. 
* [ ] You can explain what the VFS root is and how reads navigate from it. 
* [ ] You can explain why CDC is required (and point to the implementation). 
* [ ] You can point to where indexing (B+Tree) plugs into browsing/selective access. 
* [ ] You have shipped at least one small PR (tests/docs/perf) that touches one of: CDC, VFS, btree, store I/O.
* [ ] You have successfully merged a PR to improve plakar and a PR to improve kloset.
