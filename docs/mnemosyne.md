# Mnemosyne

## Goals
- User mode access
- Consistent updates
- Conventional hardware


## API

- Persistent regions
  - persistent variable declaration
  - persistent heap
- 'persistent' pointer annotation
- Consistency updates
  - single variable updates(e.g. inc, dec)
  - append updates(e.g. vector)
  - shadow updates(e.g. linked list)
  - in-place updates(any operations, similar to transactions)


## Implementation
- Persistent regions
  - __attribute__("persistent")
  - __attribute__(address_space(1))
  - region manager(modifying Linux kernel to allocate constant addresses)
  - mapping SCM memory to backing files
- Compiler checking
- Hardware primitives on cache(e.g. CLFLUSH) and transactional logging
