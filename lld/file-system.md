# In-Memory File System

Model Node, File, Directory, Path, Metadata, and FileSystem service. Directories
own children; normalize paths and define rename/delete semantics. Choose locking
granularity and prevent cycles or moves into descendants. Test root behavior,
missing paths, conflicts, recursive deletion, concurrent reads/writes, and quotas.

