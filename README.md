# NexusDB

A complete relational database management system implementation in Go, based on the architectural principles from **"Architecture of a Database System"** by Joseph M. Hellerstein, Michael Stonebraker, and James Hamilton.

## Overview

NexusDB is a ground-up implementation of a modern DBMS that follows the proven architectural patterns detailed in one of the most influential papers on database system design. This project demonstrates how academic research translates into production database systems.

### Why NexusDB?

- **Educational**: Learn database internals by implementing them
- **Modern**: Built in Go with modern systems programming practices
- **Architectural**: Follows the proven design patterns from industry leaders
- **Extensible**: Modular design allows for easy extension and experimentation

## Architecture

NexusDB implements the five core components identified in the Hellerstein paper:

```
┌─────────────────────────────────────────────────────┐
│           Client Communications Manager             │
├─────────────────────────────────────────────────────┤
│  Process Manager  │       Query Processor           │
│                   │                                 │
│  • Admission      │  • Parser & Authorization       │
│  • Control        │  • Query Optimizer              │
│  • Threading      │  • Query Executor               │
│                   │  • Access Methods               │
├─────────────────────────────────────────────────────┤
│              Transactional Storage Manager          │
│                                                     │
│  • Lock Manager      • Log Manager                  │
│  • Buffer Pool       • Recovery System              │
├─────────────────────────────────────────────────────┤
│                 Shared Components                   │
│                                                     │
│  • Catalog Manager   • Memory Allocator             │
│  • Utilities         • Administration Tools         │
└─────────────────────────────────────────────────────┘
```

### Core Features

- **ACID Transactions**: Full transaction support with ARIES recovery protocol
- **SQL Query Processing**: Complete SQL parser, optimizer, and executor
- **Concurrency Control**: Hierarchical locking with deadlock detection
- **Crash Recovery**: Write-ahead logging with point-in-time recovery
- **Indexing**: B+ trees and extensible index framework
- **Buffer Management**: Sophisticated buffer pool with multiple replacement policies

## Implementation Status

### Phase 1: Foundation Layer (IN PROGRESS)
- [ ] **TODO**: Core types and error handling
- [ ] **TODO**: Basic storage engine with pluggable backends
- [ ] **TODO**: Context-based memory allocator
- [ ] **TODO**: Page-oriented buffer pool
- [ ] **TODO**: System catalog bootstrap

### Phase 2: Query Processing Foundation (TODO)
- [ ] **TODO**: SQL parser and lexer
- [ ] **TODO**: Basic query execution (iterator model)
- [ ] **TODO**: B+ tree access methods
- [ ] **TODO**: Simple query plans

### Phase 3: Transaction System (TODO)
- [ ] **TODO**: Lock manager with hierarchical locking
- [ ] **TODO**: Write-ahead logging (WAL)
- [ ] **TODO**: ARIES recovery protocol
- [ ] **TODO**: Concurrency control

### Phase 4: Query Optimization (TODO)
- [ ] **TODO**: Cost-based query optimizer
- [ ] **TODO**: Statistics collection
- [ ] **TODO**: Join algorithm implementations
- [ ] **TODO**: Query plan caching

### Phase 5: Advanced Features (TODO)
- [ ] **TODO**: Parallel query processing
- [ ] **TODO**: Advanced access methods
- [ ] **TODO**: Complex SQL features
- [ ] **TODO**: Data warehousing support

### Phase 6: Enterprise Features (TODO)
- [ ] **TODO**: Replication and high availability
- [ ] **TODO**: Administration and monitoring tools
- [ ] **TODO**: Security framework
- [ ] **TODO**: Performance tuning utilities

### Phase 7: Distributed Features (TODO)
- [ ] **TODO**: Shared-nothing clustering
- [ ] **TODO**: Cloud-native features
- [ ] **TODO**: Modern workload support

## Getting Started

### Prerequisites

- Go 1.21 or later
- Make
- golangci-lint (for linting)

### Building

```bash
# Clone the repository
git clone https://github.com/bharathrabin/nexusdb.git
cd nexusdb

# Build all components
make build

# Run tests
make test

# Run linter
make lint
```

### Running

```bash
# Start the database server
./bin/nexusdb-server --data-dir ./data

# Connect with the client
./bin/nexusdb-client
```

## Development

### Project Structure

```
nexusdb/
├── types/           # Core types and interfaces
├── storage/         # Storage engine implementations  
├── buffer/          # Buffer pool manager
├── catalog/         # System catalog
├── memory/          # Memory allocator
├── query/           # Query processing components
├── transaction/     # Transaction and concurrency control
├── cmd/            # CLI tools and executables
├── internal/       # Internal implementation details
├── tests/          # Integration tests
└── docs/           # Documentation
```

### Coding Standards

- Follow standard Go conventions and idioms
- Use context.Context for cancellation and timeouts
- Prefer explicit error handling over panics
- Write comprehensive tests for all components
- Document all public APIs

### Contributing

1. Fork the repository
2. Create a feature branch
3. Write tests for your changes
4. Ensure all tests pass and code is formatted
5. Submit a pull request

## Performance Goals

Our implementation aims to achieve:

- **TPC-C Performance**: Within 2x of commercial systems
- **Concurrency**: Support 1000+ concurrent connections  
- **Recovery Time**: Database restart under 2 minutes for 100GB database
- **Query Performance**: Sub-second response for simple queries on million-row tables

## References

- [Architecture of a Database System](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf) - Hellerstein, Stonebraker & Hamilton (2007)
- [ARIES Recovery Algorithm](https://cs.stanford.edu/people/chrismre/cs345/rl/aries.pdf) - Mohan et al.
- [System R Papers](https://people.eecs.berkeley.edu/~brewer/cs262/SystemR.pdf) - Original relational database research

## License

MIT License - see LICENSE file for details.

## Acknowledgments

This implementation is inspired by decades of database systems research and the comprehensive architectural overview provided by Hellerstein, Stonebraker, and Hamilton. We're standing on the shoulders of giants.