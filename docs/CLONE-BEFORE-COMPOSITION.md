# CLONE BEFORE COMPOSITION — Source Preservation Protocol

**Mandatory integration rule.**

1. Identify the source repository, owner, branch/ref and exact commit.
2. Inventory source paths and retrieve original content without modifying the source.
3. Record source blob SHA, path, size, license/attribution and retrieval status.
4. Preserve a source snapshot in an isolated lineage folder or immutable archive.
5. Verify copied content against source digests where technically possible.
6. Assess dependencies, secrets, licenses, security, tests, architecture and overlap before integration.
7. Compose only from a clone. Keep source snapshot unchanged.
8. Put integration work in a separate implementation path/branch; record every transformation and parent lineage.
9. Test copied code in isolation before adapting it to WII contracts.
10. Retain failures, missing files, incompatibilities and unresolved rights questions.

## Current initial source snapshot
- Repository: `Evank253/kcn-worldview-command-center`
- Ref: `Python-3`
- Commit: `2261e9344a079d2f6d622d944c5b0a431bac1aa1`
- Preserved path: `source-clones/kcn-worldview-command-center/`
- Original source repository remains untouched.

The initial text snapshot is partial: selected application source, tests, build configuration and documentation have been copied. Binary globe textures and any files outside the recorded snapshot remain pending. This is not a complete repository clone or a verified build. A manifest records copied blob hashes and outstanding paths.
