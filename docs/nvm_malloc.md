# nvm_malloc

## Challenges
- persistency
- write reordering
- recovery


## API
- nvm_initialize(path, recover)
- nvm_reserve(id, size)
- nvm_activate(id)
- nvm_free(id)
