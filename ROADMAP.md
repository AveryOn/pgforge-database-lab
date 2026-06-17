# PG Forge Database Lab Roadmap

## 1. PostgreSQL and relational database systems fundamentals

### 001. Research the relational model

Analyze relations, tuples, attributes, keys, predicates, and constraints of the relational model.

### 002. Research the SQL execution lifecycle

Trace the query path from the parser and analyzer to the planner, executor, and result return.

### 003. Research PostgreSQL architecture

Analyze the postmaster, backend processes, shared memory, background workers, and auxiliary processes.

### 004. Research the process-per-connection model

Determine the impact of a separate backend process on memory usage, connection limits, and scalability.

### 005. Research PostgreSQL memory architecture

Analyze shared_buffers, work_mem, maintenance_work_mem, local memory, and the operating-system cache.

### 006. Research the PostgreSQL storage hierarchy

Analyze cluster, database, tablespace, relation, fork, segment, page, and tuple.

### 007. Research system catalogs

Determine the purpose of `pg_class`, `pg_attribute`, `pg_type`, `pg_index`, `pg_constraint`, and other catalogs.

### 008. Research information_schema

Compare standard-compatible metadata views with PostgreSQL-specific system catalogs.

### 009. Research PostgreSQL extensions

Analyze the extension lifecycle, control files, SQL migrations, and dependency management.

### 010. Research the PostgreSQL configuration hierarchy

Analyze `postgresql.conf`, `ALTER SYSTEM`, database-level, role-level, and session-level settings.

### 011. Research transaction processing

Determine the role of transactions, atomicity, consistency, isolation, and durability.

### 012. Research MVCC

Analyze visibility of tuple versions without blocking ordinary readers and writers.

### 013. Research query optimization

Determine the role of statistics, the cost model, selectivity, and plan alternatives.

### 014. Research durability

Analyze WAL, checkpoints, fsync, full-page writes, and crash recovery.

### 015. Research concurrency control

Analyze snapshots, locks, deadlocks, predicate locking, and serialization failures.

### 016. Research database normalization

Analyze functional dependencies and normal forms from 1NF to BCNF.

### 017. Research denormalization

Determine cases of intentional data duplication for reads and analytical queries.

### 018. Research OLTP and OLAP workloads

Compare query patterns, transaction size, indexing, and storage requirements.

### 019. Research the PostgreSQL release lifecycle

Determine major versions, minor updates, compatibility, and upgrade requirements.

### 020. Record the laboratory goals

Document the set of internals being researched, production scenarios, and criteria for verifying results.

## 2. Local environment and tools

### 021. Create the repository structure

Separate schema, migrations, experiments, benchmarks, scripts, reports, and documentation.

### 022. Prepare Docker Compose

Deploy PostgreSQL, PgBouncer, Prometheus exporter, and Grafana.

### 023. Fix the PostgreSQL version

Use a specific major release and document differences from adjacent versions.

### 024. Configure persistent storage

Preserve `PGDATA` between restarts and allow separate scenarios for a complete cluster reset.

### 025. Configure a custom postgresql.conf

Connect a separate configuration file with parameters for experiments.

### 026. Configure pg_hba.conf

Create explicit rules for local, application, replication, and administration connections.

### 027. Create database roles

Separate migration, application, read-only, monitoring, and replication roles.

### 028. Configure psql

Add `.psqlrc`, expanded output, timing, and convenient query-plan display.

### 029. Enable pg_stat_statements

Collect normalized SQL query statistics.

### 030. Enable auto_explain

Automatically log plans of slow queries.

### 031. Enable pageinspect

Research the contents of heap and index pages.

### 032. Enable pgstattuple

Measure live tuples, dead tuples, and bloat.

### 033. Enable amcheck

Check the physical integrity of B-tree indexes.

### 034. Enable pg_buffercache

Research the contents of the shared buffer cache.

### 035. Enable pg_prewarm

Manage preloading of relations into the cache.

### 036. Enable hypopg

Create hypothetical indexes without actually building them.

### 037. Enable pg_trgm

Research trigram indexes and fuzzy search.

### 038. Prepare a test data generator

Create reproducible datasets of different sizes and distributions.

### 039. Create laboratory reset scenarios

Automate deletion and recreation of schema, data, and statistics.

### 040. Create an experiment report template

Record hypothesis, setup, SQL, measurements, plan, and conclusions.

## 3. Physical storage and pages

### 041. Research the database cluster layout

Analyze the purpose of `base`, `global`, `pg_wal`, `pg_tblspc`, and other directories.

### 042. Research relation files

Determine the relationship between relation OID, relfilenode, and physical files.

### 043. Research relation forks

Analyze main, free space map, visibility map, and initialization forks.

### 044. Research relation segmentation

Check the splitting of large relations into segment files.

### 045. Research PostgreSQL pages

Analyze the fixed-size page, page header, line pointers, and tuple data.

### 046. Research heap page layout

Use `pageinspect` to analyze tuple placement.

### 047. Research the tuple header

Analyze `xmin`, `xmax`, `ctid`, infomask, and the null bitmap.

### 048. Research item pointers

Determine the role of a line pointer and tuple relocation.

### 049. Research CTID

Check changes in physical tuple location after UPDATE and VACUUM FULL.

### 050. Research the free space map

Check how PostgreSQL finds pages with free space.

### 051. Research the visibility map

Analyze the all-visible and all-frozen bits.

### 052. Research fillfactor

Measure the impact of free space in pages on UPDATE and bloat.

### 053. Research TOAST

Analyze compression, out-of-line storage, and TOAST tables.

### 054. Research TOAST thresholds

Check when large values move to compressed or external storage.

### 055. Research varlena representation

Analyze storage of variable-length values.

### 056. Research tuple alignment

Determine the impact of column order on padding and row size.

### 057. Compare column order

Measure physical row size for different schema variants.

### 058. Research page splits

Check B-tree page split behavior with random and sequential inserts.

### 059. Research relation extension

Check allocation of new pages as a table grows.

### 060. Research table rewrites

Determine operations that cause a complete physical rewrite of the table.

### 061. Research unlogged tables

Compare performance, WAL generation, and crash behavior.

### 062. Research temporary tables

Analyze session scope, catalog overhead, and storage behavior.

### 063. Research tablespaces

Create a separate tablespace and move a relation.

### 064. Research data checksums

Check the purpose of page checksums and the limitations of enabling them.

### 065. Research relation size functions

Use `pg_relation_size`, `pg_table_size`, and `pg_total_relation_size`.

### 066. Research block reads

Compare logical and physical reads for a relation.

### 067. Research cache warming

Compare cold-cache and warm-cache execution.

### 068. Research the operating-system page cache

Determine the interaction between shared_buffers and the filesystem cache.

### 069. Research direct I/O limitations

Analyze PostgreSQL's traditional dependence on the operating-system cache.

### 070. Document storage internals

Create a diagram of the physical storage hierarchy and tuple lifecycle.

## 4. Data types

### 071. Research integer types

Compare `smallint`, `integer`, and `bigint` by range and storage size.

### 072. Research numeric

Analyze arbitrary precision, scale, storage, and computational cost.

### 073. Compare numeric and floating-point

Check the precision and performance of `numeric`, `real`, and `double precision`.

### 074. Research monetary representation

Compare integer minor units and `numeric` for monetary values.

### 075. Research character types

Compare `text`, `varchar`, and `char`.

### 076. Check varchar constraints

Determine when a length constraint provides business value.

### 077. Research collations

Analyze locale-aware comparison and sorting.

### 078. Research deterministic collations

Determine the impact of deterministic mode on equality and indexing.

### 079. Research ICU collations

Create and check an ICU collation.

### 080. Research case-insensitive text

Compare normalized text, a functional index, and `citext`.

### 081. Research boolean

Record the correct use of `boolean` instead of nullable status flags.

### 082. Research date and time types

Compare `date`, `time`, `timestamp`, and `timestamptz`.

### 083. Research timestamp semantics

Check storage and display of `timestamp with time zone`.

### 084. Research intervals

Analyze months, days, microseconds, and calendar arithmetic.

### 085. Research timezone behavior

Check the session timezone and daylight-saving transitions.

### 086. Research UUID

Compare UUID versions, generation, and index locality.

### 087. Research sequential identifiers

Compare `serial`, identity columns, UUID, and ULID-like identifiers.

### 088. Research sequences

Analyze caching, gaps, concurrency, and transaction independence.

### 089. Research identity columns

Compare `GENERATED ALWAYS` and `GENERATED BY DEFAULT`.

### 090. Research enum types

Determine advantages, migration limitations, and alternative lookup tables.

### 091. Research domains

Create a reusable constrained domain type.

### 092. Research composite types

Use a user-defined composite type and determine its limitations.

### 093. Research arrays

Analyze storage, operators, indexing, and normalization trade-offs.

### 094. Research JSON

Compare textual JSON and binary JSONB.

### 095. Research JSONB storage

Check normalization, key ordering, and duplicate keys.

### 096. Research JSONB operators

Use containment, extraction, and path queries.

### 097. Research range types

Apply `int4range`, `daterange`, and `tstzrange`.

### 098. Research multirange types

Store sets of non-overlapping ranges.

### 099. Research network types

Use `inet`, `cidr`, and network operators.

### 100. Research binary data

Compare `bytea`, large objects, and external object storage.

### 101. Research full-text types

Analyze `tsvector`, `tsquery`, and dictionaries.

### 102. Research geometric types

Check built-in point, box, and path types.

### 103. Research generated columns

Create a stored generated column and measure the write/read trade-off.

### 104. Research null semantics

Analyze three-valued logic and `IS DISTINCT FROM`.

### 105. Create a type selection guide

Document rules for selecting PostgreSQL data types for a production schema.


## 5. Schema design

### 106. Design a demonstration domain

Create a schema for customers, organizations, projects, orders, payments, and events.

### 107. Define primary keys

Choose natural or surrogate keys for each entity.

### 108. Research natural keys

Evaluate the stability, size, and propagation of business identifiers.

### 109. Research surrogate keys

Evaluate simplicity of joins, migrations, and distributed generation.

### 110. Implement normalization to 3NF

Eliminate repeating groups, partial dependencies, and transitive dependencies.

### 111. Research BCNF

Find a relation where 3NF is insufficient to eliminate anomalies.

### 112. Research a denormalized read model

Create a separate table to accelerate a complex read path.

### 113. Compare an entity table and a JSONB blob

Measure queryability, validation, and indexing.

### 114. Design a one-to-one relation

Choose a shared primary key or a unique foreign key.

### 115. Design a one-to-many relation

Configure the foreign key and indexes for parent-child access.

### 116. Design a many-to-many relation

Create a join table with composite uniqueness.

### 117. Design hierarchical data

Compare adjacency list, materialized path, nested sets, and closure table.

### 118. Implement an adjacency list

Create recursive queries through `WITH RECURSIVE`.

### 119. Implement a materialized path

Use `ltree` or a textual path representation.

### 120. Implement a closure table

Support fast search for ancestors and descendants.

### 121. Design polymorphic relations

Compare nullable foreign keys, association tables, and a shared parent entity.

### 122. Avoid a generic entity-attribute-value model

Show the typing, constraint, and query-planning problems of EAV.

### 123. Design a status model

Compare an enum, lookup table, and state transition table.

### 124. Design temporal data

Store valid-time and system-time intervals.

### 125. Implement append-only history

Store entity changes as separate immutable records.

### 126. Implement an audit snapshot model

Store before and after representations with metadata.

### 127. Design soft deletion

Add `deleted_at` and determine its impact on uniqueness and indexes.

### 128. Design an archival model

Move historical data to separate partitions or tables.

### 129. Design a multi-tenant schema

Add a tenant key to all tenant-owned relations.

### 130. Add composite tenant constraints

Prevent cross-tenant references at the database level.

## 6. Constraints and data integrity

### 131. Implement primary key constraints

Check automatic creation of a unique B-tree index.

### 132. Implement foreign key constraints

Check referential integrity on insert, update, and delete.

### 133. Research foreign key indexes

Show that PostgreSQL does not create an index on the referencing column automatically.

### 134. Research foreign key actions

Compare `NO ACTION`, `RESTRICT`, `CASCADE`, `SET NULL`, and `SET DEFAULT`.

### 135. Research deferred foreign keys

Defer constraint checking until commit.

### 136. Implement unique constraints

Enforce business uniqueness at the database level.

### 137. Research nulls in unique constraints

Check the behavior of multiple NULL values.

### 138. Use NULLS NOT DISTINCT

Prohibit multiple NULL values in a unique constraint.

### 139. Implement composite uniqueness

Enforce uniqueness within a tenant or parent resource.

### 140. Implement partial uniqueness

Use a partial unique index for active records.

### 141. Implement check constraints

Enforce ranges, status combinations, and invariants.

### 142. Research check constraint limitations

Show why a check should not depend on other rows.

### 143. Implement an exclusion constraint

Prohibit overlapping ranges through GiST.

### 144. Research NOT NULL

Compare column-level NOT NULL and an equivalent CHECK.

### 145. Add constraints through NOT VALID

Prepare a low-lock constraint rollout on a large table.

### 146. Execute VALIDATE CONSTRAINT

Check existing rows separately from the short metadata operation.

### 147. Research constraint locking

Measure locks during constraint addition and validation.

### 148. Create domain constraints

Reuse validation through a custom domain.

### 149. Implement transition constraints

Use a trigger only for invariants that cannot be expressed through declarative constraints.

### 150. Research the absence of assertions

Analyze the absence of standard SQL ASSERTION in PostgreSQL.

### 151. Implement immutable column protection

Prohibit changing a business identifier through a trigger.

### 152. Implement a cross-row invariant

Create a transaction-safe mechanism for a constraint spanning multiple rows.

### 153. Check the SELECT-then-INSERT race condition

Show why application-side uniqueness is insufficient.

### 154. Use INSERT ON CONFLICT

Implement an atomic upsert based on a unique constraint.

### 155. Research ON CONFLICT concurrency

Check the behavior of competing inserts.

### 156. Use RETURNING

Retrieve changed rows without an additional SELECT.

### 157. Implement generated defaults

Use database-generated identifiers and timestamps.

### 158. Prohibit invalid state combinations

Add composite check constraints.

### 159. Create an integrity test suite

Intentionally violate constraints and check expected SQLSTATE values.

### 160. Document ownership constraints

Record invariants guaranteed by the database, application, and external systems.

## 7. B-tree indexes

### 161. Research B-tree structure

Analyze root, internal, and leaf pages, and sibling links.

### 162. Create a single-column B-tree index

Measure its impact on equality and range queries.

### 163. Research index tuple layout

Analyze key data, TID, and included columns.

### 164. Research B-tree operator classes

Determine the relationship between operators and index ordering.

### 165. Research ascending and descending indexes

Check backward scans and mixed-order multicolumn indexes.

### 166. Research NULLS FIRST and NULLS LAST

Check index use for sorting nullable values.

### 167. Create a multicolumn index

Research the leftmost prefix rule.

### 168. Research skip scan

Check whether a later column of a multicolumn index can be used.

### 169. Measure the selectivity of the first column

Compare column order for different query patterns.

### 170. Create a covering index

Use INCLUDE for an index-only scan.

### 171. Research INCLUDE limitations

Determine the impact of included columns on index size and uniqueness.

### 172. Create a partial index

Index only active or frequently queried rows.

### 173. Check predicate matching

Show when the planner cannot prove correspondence with a partial-index WHERE predicate.

### 174. Create an expression index

Index `lower(email)` or a computed expression.

### 175. Check expression equivalence

Show the impact of casts and function wrapping on index usage.

### 176. Research immutable functions

Determine requirements for expressions in an index.

### 177. Create a unique expression index

Enforce case-insensitive uniqueness.

### 178. Research index deduplication

Check B-tree size reduction for repeated keys.

### 179. Research index fillfactor

Measure page splits and free space.

### 180. Research index correlation

Relate physical heap order to planner cost.

### 181. Use CLUSTER

Rebuild a table in index order and measure range scans.

### 182. Check degradation after CLUSTER

Show loss of physical ordering after subsequent writes.

### 183. Use REINDEX

Rebuild a corrupted or bloated index.

### 184. Use REINDEX CONCURRENTLY

Rebuild an index with minimal write blocking.

### 185. Research duplicate indexes

Find indexes covering the same column prefixes.

### 186. Research unused indexes

Use `pg_stat_user_indexes` and account for statistics resets.

### 187. Measure write amplification

Compare INSERT and UPDATE performance with different numbers of indexes.

### 188. Measure index size

Use `pg_relation_size` and `pgstattuple`.

### 189. Research index bloat

Create a churn workload and measure growth.

### 190. Check B-tree integrity

Use `amcheck`.

### 191. Research concurrent index build

Check phases and invalid index states.

### 192. Handle failed CREATE INDEX CONCURRENTLY

Find and remove an invalid index.

### 193. Research lock behavior of index DDL

Measure locks of regular and concurrent index creation.

### 194. Create an index naming convention

Record stable and understandable names.

### 195. Document B-tree decision rules

Create a guide for choosing single, composite, partial, expression, and covering indexes.

## 8. Other index access methods

### 196. Research Hash indexes

Compare equality lookups, WAL support, and limitations.

### 197. Create a Hash index

Measure size and performance relative to B-tree.

### 198. Research GiST

Analyze generalized search trees and extensible operator classes.

### 199. Create a GiST range index

Accelerate overlap and containment queries.

### 200. Create a GiST geometric index

Check spatial operators.

### 201. Research SP-GiST

Analyze space-partitioned search trees.

### 202. Create an SP-GiST index

Check a prefix or geometric workload.

### 203. Research GIN

Analyze the inverted index for composite values.

### 204. Create a GIN JSONB index

Accelerate containment queries.

### 205. Compare jsonb_ops and jsonb_path_ops

Measure size, supported operators, and performance.

### 206. Create a GIN array index

Accelerate containment and overlap.

### 207. Create a GIN full-text index

Accelerate `tsvector` search.

### 208. Research the GIN pending list

Analyze fastupdate and deferred index maintenance.

### 209. Measure GIN write cost

Compare inserts with `fastupdate` enabled and disabled.

### 210. Research BRIN

Analyze block range summaries.

### 211. Create a BRIN index

Apply it to a large append-only time-series table.

### 212. Measure the impact of correlation on BRIN

Compare ordered and randomized data.

### 213. Research BRIN pages_per_range

Select granularity and index size.

### 214. Use BRIN autosummarize

Check automatic summarization of new ranges.

### 215. Research Bloom indexes

Enable the extension and check a multicolumn equality workload.

### 216. Compare B-tree and Bloom

Evaluate false positives, size, and workload applicability.

### 217. Research trigram GIN

Accelerate `LIKE`, `ILIKE`, and similarity search.

### 218. Research trigram GiST

Compare it with GIN for fuzzy matching.

### 219. Research full-text search configuration

Analyze the parser, dictionaries, lexemes, and weights.

### 220. Create a weighted tsvector

Assign different weights to title and body.

### 221. Create a generated tsvector column

Automatically maintain a searchable representation.

### 222. Research phrase search

Use phrase operators and positions.

### 223. Research custom operator classes

Analyze the relationship between access methods, strategy numbers, and support functions.

### 224. Research the index access method API

Study the basic structure of PostgreSQL index extensibility.

### 225. Create an index-type matrix

Map data type, operators, access method, and workload.


## 9. Query planner and statistics

### 226. Research the parser

Analyze transformation of SQL text into a parse tree.

### 227. Research the analyzer

Check resolution of relations, columns, types, and implicit casts.

### 228. Research the rewrite system

Analyze rules, views, and query-tree rewriting.

### 229. Research the planner

Determine path generation, cost comparison, and the final plan.

### 230. Research the executor

Analyze pull-based execution plan nodes.

### 231. Research the PostgreSQL cost model

Analyze startup cost, total cost, and arbitrary cost units.

### 232. Research seq_page_cost

Measure the impact of sequential I/O cost.

### 233. Research random_page_cost

Check index-scan selection with SSD-like configuration.

### 234. Research cpu_tuple_cost

Determine the impact of CPU cost on plan selection.

### 235. Research cpu_index_tuple_cost

Analyze the cost of index tuple processing.

### 236. Research cpu_operator_cost

Check the impact of expensive predicates.

### 237. Research effective_cache_size

Understand its role as a planner estimate rather than memory allocation.

### 238. Research table statistics

Analyze `reltuples`, `relpages`, and their approximate nature.

### 239. Research column statistics

Analyze null fraction, distinct count, and average width.

### 240. Research most common values

Check the MCV list for a skewed distribution.

### 241. Research histograms

Check selectivity of range predicates.

### 242. Research correlation statistics

Relate physical ordering to index-scan cost.

### 243. Research default_statistics_target

Measure estimate accuracy and ANALYZE cost.

### 244. Configure a per-column statistics target

Increase statistics for a skewed column.

### 245. Run ANALYZE

Check changes in cardinality estimates.

### 246. Research sampling

Understand why statistics are approximate.

### 247. Create extended statistics dependencies

Improve estimates for correlated columns.

### 248. Create extended statistics ndistinct

Improve GROUP BY and multicolumn estimates.

### 249. Create extended statistics MCV

Improve estimates for combinations of frequent values.

### 250. Research stale statistics

Show a poor plan after a large data change.

### 251. Research planner row estimates

Compare estimated and actual rows for each plan node.

### 252. Research equality selectivity

Check estimates for uniform and skewed values.

### 253. Research range selectivity

Check histogram boundaries.

### 254. Research LIKE selectivity

Check prefix and non-prefix patterns.

### 255. Research join selectivity

Check estimates for foreign-key and non-unique relations.

### 256. Research functional dependencies

Show improved estimates from extended statistics.

### 257. Research parameterized queries

Check the impact of an unknown parameter value on planning.

### 258. Research the generic plan

Determine conditions for a prepared statement to switch to a generic plan.

### 259. Research the custom plan

Compare plans for selective and non-selective parameters.

### 260. Configure plan_cache_mode

Force generic or custom planning.

### 261. Research prepared-statement invalidation

Check replanning after DDL or statistics changes.

### 262. Research implicit casts

Show loss of index usage because of a type mismatch.

### 263. Research function volatility

Analyze VOLATILE, STABLE, and IMMUTABLE.

### 264. Research planner constant folding

Check evaluation of immutable expressions during planning.

### 265. Research constraint exclusion

Check exclusion of relations by constraints.

### 266. Research partition pruning

Compare planning-time and execution-time pruning.

### 267. Research join-order search

Analyze dynamic programming and GEQO.

### 268. Configure join_collapse_limit

Check the impact on join reordering.

### 269. Configure from_collapse_limit

Check flattening of subqueries.

### 270. Research GEQO

Check planning of large join graphs.

## 10. Scan and join algorithms

### 271. Research Sequential Scan

Determine cases where Seq Scan is cheaper than index access.

### 272. Research Index Scan

Analyze heap fetches and random access.

### 273. Research Index Only Scan

Understand the role of the visibility map and heap fetches.

### 274. Research Bitmap Index Scan

Analyze construction of a bitmap of matching TIDs.

### 275. Research Bitmap Heap Scan

Check exact and lossy heap blocks.

### 276. Research TID Scan

Retrieve a tuple by CTID and determine the limitations.

### 277. Research Subquery Scan

Analyze materialized and inline subqueries.

### 278. Research Function Scan

Check a set-returning function in FROM.

### 279. Research Values Scan

Analyze execution of inline VALUES.

### 280. Research Nested Loop Join

Determine suitable workloads and parameterized inner scans.

### 281. Research Hash Join

Analyze the build and probe phases.

### 282. Research Hash Join batching

Check spilling to disk when work_mem is insufficient.

### 283. Research Merge Join

Understand requirements for sorted inputs.

### 284. Compare join algorithms

Measure performance with different cardinalities and indexes.

### 285. Research semi join

Analyze EXISTS and IN transformations.

### 286. Research anti join

Analyze NOT EXISTS and anti-join semantics.

### 287. Research lateral joins

Use a parameterized subquery for each outer row.

### 288. Research join removal

Check removal of an unnecessary join with foreign keys and uniqueness.

### 289. Research partition-wise join

Compare joins of partitioned tables.

### 290. Research parallel hash join

Check a shared hash table between workers.

### 291. Disable individual plan types

Use `enable_seqscan`, `enable_hashjoin`, and other settings for experiments.

### 292. Do not use planner toggles as a production fix

Document their role only for diagnostics and controlled tuning.

### 293. Research materialization

Check the Materialize plan node and repeated reading of the inner result.

### 294. Research Memoize

Check caching of parameterized scan results.

### 295. Create a join decision matrix

Record conditions for choosing Nested Loop, Hash Join, and Merge Join.

## 11. Sorting, aggregation, and parallel execution

### 296. Research the Sort node

Analyze quicksort, top-N heapsort, and external merge.

### 297. Research sort spill

Check temporary files when work_mem is insufficient.

### 298. Research incremental sort

Use partially sorted input.

### 299. Research top-N sorting

Compare ORDER BY with and without LIMIT.

### 300. Research HashAggregate

Analyze hash-table grouping.

### 301. Research GroupAggregate

Use sorted input for aggregation.

### 302. Research MixedAggregate

Check a mixed strategy for grouping sets.

### 303. Research aggregate spill

Check batching when work_mem is insufficient.

### 304. Research DISTINCT

Compare Sort + Unique and HashAggregate.

### 305. Research window functions

Analyze WindowAgg and sorting requirements.

### 306. Research GROUPING SETS

Implement multiple aggregation levels with one query.

### 307. Research CTE inlining

Compare a regular CTE and `MATERIALIZED`.

### 308. Research NOT MATERIALIZED

Allow the planner to inline the CTE into the main query.

### 309. Research recursive CTE

Analyze Recursive Union and the working table.

### 310. Research parallel query

Determine parallel-safe operations and planner thresholds.

### 311. Research Gather

Analyze collection of tuples from parallel workers.

### 312. Research Gather Merge

Preserve sorted order from workers.

### 313. Configure max_parallel_workers_per_gather

Check scaling of one query.

### 314. Research parallel setup cost

Understand why small queries do not use parallelism.

### 315. Research parallel tuple cost

Check the cost of transferring tuples to the leader process.

### 316. Research parallel sequential scan

Measure a large-table scan with different numbers of workers.

### 317. Research parallel index scan

Check supported index access methods.

### 318. Research parallel aggregate

Analyze partial and finalize aggregation.

### 319. Research JIT compilation

Determine compilation, optimization, and expression-execution phases.

### 320. Measure JIT overhead

Compare short and CPU-intensive queries.

## 12. EXPLAIN and query diagnostics

### 321. Use EXPLAIN

Read the plan tree without executing the statement.

### 322. Use EXPLAIN ANALYZE

Compare estimates and actual execution.

### 323. Use BUFFERS

Measure shared hit, read, dirtied, and written blocks.

### 324. Use WAL

Measure WAL records, full-page images, and bytes.

### 325. Use TIMING

Determine per-node timing overhead.

### 326. Use SUMMARY

Retrieve planning and execution time.

### 327. Use SETTINGS

Record planner settings affecting the plan.

### 328. Use VERBOSE

View output columns and qualified object names.

### 329. Use FORMAT JSON

Retrieve a machine-readable query plan.

### 330. Create an EXPLAIN JSON parser

Extract nodes, estimates, timings, and buffer metrics.

### 331. Analyze loops

Correctly account for repeated execution of a plan node.

### 332. Analyze rows removed by filter

Determine wasted work after a scan.

### 333. Analyze heap fetches

Evaluate Index Only Scan efficiency.

### 334. Analyze lossy bitmap blocks

Determine insufficient work_mem and recheck overhead.

### 335. Analyze the sort method

Distinguish in-memory and external sorting.

### 336. Analyze hash batches

Determine a spilling Hash Join or HashAggregate.

### 337. Analyze planning time

Research complex join graphs and partitioned schemas.

### 338. Analyze execution time

Separate executor cost from client transfer.

### 339. Compare cold and warm plans

Run controlled experiments with cache state.

### 340. Create a query-plan analysis checklist

Record the sequence for checking estimates, scans, joins, memory, and I/O.


## 13. Transactions and MVCC

### 341. Research transaction boundaries

Compare implicit transactions, explicit BEGIN, and autocommit.

### 342. Research transaction IDs

Analyze XID allocation and visibility.

### 343. Research snapshots

Determine visible committed, in-progress, and aborted transactions.

### 344. Research xmin and xmax

Check tuple visibility for INSERT, UPDATE, and DELETE.

### 345. Research command IDs

Analyze visibility of changes within one transaction.

### 346. Research tuple version chains

Trace HOT and non-HOT update versions.

### 347. Research UPDATE as INSERT+DELETE

Check creation of a new tuple version.

### 348. Research DELETE

Show that a tuple physically remains until VACUUM.

### 349. Research transaction commit

Analyze the commit record in WAL and visibility.

### 350. Research rollback

Check preservation of aborted tuple versions until cleanup.

### 351. Research subtransactions

Use SAVEPOINT and ROLLBACK TO SAVEPOINT.

### 352. Research subtransaction overhead

Check a large number of savepoints.

### 353. Research transaction snapshots in READ COMMITTED

Obtain a new snapshot for each statement.

### 354. Research the snapshot in REPEATABLE READ

Preserve one transaction snapshot.

### 355. Research read-only transactions

Restrict mutations and use optimization opportunities.

### 356. Research deferrable transactions

Use a safe snapshot for serializable read-only workloads.

### 357. Research long-running transactions

Show retention of dead tuples and the impact on vacuum.

### 358. Research idle in transaction

Check locks, snapshots, and bloat risk.

### 359. Configure idle_in_transaction_session_timeout

Automatically terminate dangerous idle transactions.

### 360. Configure statement_timeout

Limit statement duration.

### 361. Configure transaction_timeout

Limit total transaction duration if supported by the selected version.

### 362. Research transaction read/write sets

Determine conflicting operations.

### 363. Research atomic counters

Implement a safe increment with one UPDATE.

### 364. Research the check-then-act race

Show why application-side transaction logic is incorrect without locks or constraints.

### 365. Implement a transactional outbox

Atomically store domain state and an event record.

### 366. Research the dual-write problem

Show the impossibility of atomically committing PostgreSQL and an external broker without a protocol.

### 367. Implement an idempotent transaction

Use a unique business key for a repeated command.

### 368. Research commit latency

Measure the impact of synchronous_commit and storage.

### 369. Research group commit

Check joint flushing of multiple transactions.

### 370. Document the MVCC lifecycle

Create a diagram of tuple versions, snapshots, commit, and vacuum.

## 14. Isolation levels and anomalies

### 371. Research READ UNCOMMITTED

Record that PostgreSQL treats it as READ COMMITTED.

### 372. Research READ COMMITTED

Check statement-level snapshots.

### 373. Reproduce a non-repeatable read

Show a result changing between statements.

### 374. Reproduce phantom-like behavior

Show new rows appearing between statements.

### 375. Research REPEATABLE READ

Check PostgreSQL snapshot-isolation semantics.

### 376. Reproduce write skew

Show a snapshot-isolation anomaly.

### 377. Research lost update

Check the behavior of competing read-modify-write transactions.

### 378. Protect against lost update

Use an atomic UPDATE, row lock, or optimistic version.

### 379. Research SERIALIZABLE

Analyze Serializable Snapshot Isolation.

### 380. Research predicate locks

Check `pg_locks` for SIReadLock.

### 381. Reproduce a serialization failure

Create a dangerous dependency structure.

### 382. Implement retries for SERIALIZABLE transactions

Retry the entire transaction after SQLSTATE `40001`.

### 383. Research false-positive serialization failures

Understand the conservative nature of SSI detection.

### 384. Compare isolation levels

Record anomalies, overhead, and use cases.

### 385. Create an isolation test harness

Run synchronized concurrent sessions.

### 386. Research read skew

Check inconsistent observations of multiple related rows.

### 387. Research write-skew mitigation

Use SERIALIZABLE or explicit locking.

### 388. Research phantom protection

Compare snapshots and predicate locking.

### 389. Research uniqueness conflicts

Check the behavior of concurrent inserts.

### 390. Research ON CONFLICT under READ COMMITTED

Analyze visibility of the conflicting row.

### 391. Research application retries

Determine retryable SQLSTATE values and a backoff policy.

### 392. Prohibit partial transaction retry

Retry the entire unit of work rather than an individual failed statement.

### 393. Research side effects during retry

Do not perform an irreversible external call inside a retried transaction.

### 394. Implement optimistic concurrency control

Add a version column and conditional UPDATE.

### 395. Implement pessimistic concurrency control

Use row-level locks.

## 15. Locks and deadlocks

### 396. Research table-level locks

Analyze PostgreSQL lock modes and the compatibility matrix.

### 397. Research ACCESS SHARE

Check the lock of a regular SELECT.

### 398. Research ROW EXCLUSIVE

Check locks of INSERT, UPDATE, and DELETE.

### 399. Research SHARE UPDATE EXCLUSIVE

Determine operations of autovacuum and concurrent index build.

### 400. Research ACCESS EXCLUSIVE

Check DDL that blocks all access.

### 401. Research row-level locks

Analyze FOR UPDATE, NO KEY UPDATE, SHARE, and KEY SHARE.

### 402. Use SELECT FOR UPDATE

Lock rows before mutation.

### 403. Use FOR NO KEY UPDATE

Reduce conflicts when the key is unchanged.

### 404. Use FOR SHARE

Analyze shared row-lock semantics.

### 405. Use FOR KEY SHARE

Protect a referenced key from deletion or key update.

### 406. Research NOWAIT

Immediately terminate the operation when a lock cannot be acquired.

### 407. Research SKIP LOCKED

Implement concurrent processing of a job queue.

### 408. Research lock queues

Check wait order and the impact of a long holder.

### 409. Research lock_timeout

Limit lock wait time.

### 410. Research fast-path locks

Analyze optimization of frequently used relation locks.

### 411. Research heavyweight locks

Check representation in the shared lock table.

### 412. Research lightweight locks

Analyze PostgreSQL internal synchronization primitives.

### 413. Research buffer pins

Understand their difference from SQL-visible locks.

### 414. Research advisory locks

Use session-level and transaction-level locks.

### 415. Create an advisory-lock namespace

Prevent collisions between different business resources.

### 416. Compare advisory and row locks

Record database enforcement and application responsibility.

### 417. Reproduce a deadlock

Create two transactions with reverse lock order.

### 418. Research deadlock detection

Check the impact of `deadlock_timeout`.

### 419. Analyze deadlock logs

Determine involved transactions, statements, and objects.

### 420. Eliminate deadlocks through lock ordering

Record a consistent order for acquiring resources.

### 421. Eliminate deadlocks by shortening the transaction

Minimize lock-holding time.

### 422. Implement deadlock retry

Retry the transaction after SQLSTATE `40P01`.

### 423. Research foreign-key locking

Check row locks when inserting a referencing row and deleting a referenced row.

### 424. Research DDL locking

Measure locks of ALTER TABLE operations.

### 425. Create a lock diagnostics query

Show blockers, waiters, queries, and transaction age.

## 16. HOT updates, VACUUM, and bloat

### 426. Research HOT update

Determine conditions for a heap-only tuple update.

### 427. Check HOT eligibility

Update a non-indexed column when space is available on the page.

### 428. Check HOT prevention

Update an indexed column or a page without free space.

### 429. Measure HOT statistics

Use `n_tup_hot_upd` and related counters.

### 430. Research pruning

Check cleanup of tuple chains during page access.

### 431. Research VACUUM

Analyze cleanup of the heap, indexes, FSM, and visibility map.

### 432. Research VACUUM ANALYZE

Update statistics together with cleanup.

### 433. Research VACUUM FULL

Check table rewrite, disk usage, and ACCESS EXCLUSIVE lock.

### 434. Research lazy vacuum

Analyze the phases of regular VACUUM.

### 435. Research the autovacuum launcher

Understand work distribution among workers.

### 436. Research autovacuum thresholds

Analyze the threshold and scale factor.

### 437. Configure per-table autovacuum

Select parameters for a high-churn table.

### 438. Research autovacuum_vacuum_cost_limit

Control background-vacuum aggressiveness.

### 439. Research autovacuum_naptime

Check how often tables requiring work are searched.

### 440. Research vacuum memory

Analyze maintenance_work_mem and autovacuum_work_mem.

### 441. Research vacuum progress

Use `pg_stat_progress_vacuum`.

### 442. Research analyze progress

Check progress views available in the selected version.

### 443. Research dead-tuple accumulation

Create an update/delete workload and measure growth.

### 444. Research table bloat

Compare logical data size and physical relation size.

### 445. Research index bloat

Measure unused space and duplicate index entries.

### 446. Use pgstattuple

Obtain an exact estimate of dead tuples and free space.

### 447. Compare approximate bloat queries

Evaluate limitations of catalog-based estimates.

### 448. Research freeze

Analyze frozen XIDs and tuple visibility.

### 449. Research transaction ID wraparound

Understand the critical importance of anti-wraparound vacuum.

### 450. Check relfrozenxid

Find the oldest unfrozen relations.

### 451. Research vacuum_freeze_min_age

Determine the point of early freezing.

### 452. Research vacuum_freeze_table_age

Configure an aggressive freeze scan.

### 453. Research autovacuum_freeze_max_age

Understand emergency autovacuum behavior.

### 454. Research multixact IDs

Analyze storage of shared row locks.

### 455. Research multixact wraparound

Check monitoring requirements.

### 456. Research the visibility map and index-only scan

Show degradation of index-only scans under churn.

### 457. Research vacuum truncation

Check returning empty end pages to the operating system.

### 458. Research replication slots and vacuum

Show retention of dead tuples by an old xmin.

### 459. Research the impact of a long snapshot

Relate an old snapshot to inability to clean up.

### 460. Create a vacuum-tuning runbook

Record diagnostics for dead tuples, autovacuum lag, and wraparound risk.


## 17. WAL, checkpoints, and crash recovery

### 461. Research Write-Ahead Logging

Analyze the rule of writing WAL before data pages.

### 462. Research WAL records

Check WAL generation for INSERT, UPDATE, DELETE, and index changes.

### 463. Research WAL segments

Analyze naming, size, and recycling.

### 464. Research WAL buffers

Understand intermediate storage of records before flush.

### 465. Research LSN

Use the Log Sequence Number for positions and replication.

### 466. Research full-page writes

Understand protection against torn pages after a checkpoint.

### 467. Measure full-page image overhead

Compare WAL volume immediately after a checkpoint and later.

### 468. Research wal_compression

Measure WAL size and CPU overhead.

### 469. Research synchronous_commit

Compare on, off, and remote durability modes.

### 470. Research fsync

Understand its impact on durability and the impossibility of safely disabling it in production.

### 471. Research wal_sync_method

Compare platform-specific flush methods.

### 472. Research checkpoints

Analyze dirty-buffer flushing and recovery distance.

### 473. Configure checkpoint_timeout

Check checkpoint frequency.

### 474. Configure max_wal_size

Manage checkpoint pressure.

### 475. Configure checkpoint_completion_target

Distribute checkpoint I/O over time.

### 476. Research checkpoint spikes

Observe latency and write throughput.

### 477. Research the background writer

Analyze cleaning of dirty buffers independently of checkpoints.

### 478. Research the WAL writer

Understand background WAL flush.

### 479. Research crash recovery

Terminate the PostgreSQL process and check WAL replay.

### 480. Analyze recovery logs

Trace redo start, end, and consistency point.

### 481. Research unlogged-table recovery

Check cleanup of an unlogged relation after a crash.

### 482. Research WAL archiving

Configure `archive_mode` and `archive_command`.

### 483. Check archive_command idempotency

Do not treat a repeated call as an error when the segment has already been stored.

### 484. Research archive backlog

Monitor unarchived WAL segments.

### 485. Configure WAL retention

Account for replication slots, archive, and standby requirements.

### 486. Research wal_level

Compare minimal, replica, and logical.

### 487. Research commit timestamp

Enable and check commit-time tracking when necessary.

### 488. Research WAL inspection

Use `pg_waldump` to analyze records.

### 489. Measure WAL amplification

Compare workloads with different numbers of indexes.

### 490. Document durability trade-offs

Record the impact of WAL, checkpoints, and commit settings.

## 18. Backup and Point-in-Time Recovery

### 491. Research logical backup

Compare `pg_dump`, `pg_dumpall`, and selective export.

### 492. Create a custom-format backup

Use parallel restore and selective loading of objects.

### 493. Research physical backup

Use `pg_basebackup`.

### 494. Configure a backup manifest

Check physical-backup integrity.

### 495. Configure continuous archiving

Store WAL for PITR.

### 496. Perform Point-in-Time Recovery

Restore the cluster to a moment before an erroneous DELETE.

### 497. Research recovery targets

Use a timestamp, transaction ID, LSN, and named restore point.

### 498. Create a restore point

Record a marker before a dangerous migration.

### 499. Check backup restore

Do not consider a backup valid without regular restoration.

### 500. Measure Recovery Point Objective

Determine possible data loss.

### 501. Measure Recovery Time Objective

Determine restoration duration.

### 502. Research parallel pg_restore

Select the number of jobs and assess the impact of indexes and constraints.

### 503. Research backup consistency

Understand snapshots for logical backup and WAL consistency for physical backup.

### 504. Separate schema and data restore

Restore pre-data, data, and post-data sections.

### 505. Research large-object backup

Check restoration of large objects.

### 506. Research role and privilege backup

Store global objects separately.

### 507. Create a backup retention policy

Define full backups, WAL, and expiration.

### 508. Encrypt backups

Protect data at rest and keys.

### 509. Create backup monitoring

Check age, size, completion, and restore tests.

### 510. Create a disaster-recovery runbook

Document complete restoration of a PostgreSQL cluster.

## 19. Migrations and zero-downtime schema changes

### 511. Create a migration framework

Store versioned SQL migrations and immutable applied history.

### 512. Separate transactional and non-transactional migrations

Account for `CREATE INDEX CONCURRENTLY` and other operations.

### 513. Implement migration locking

Do not run two migration processes simultaneously.

### 514. Implement migration checksums

Detect changes to already applied files.

### 515. Create a migration status command

Show applied, pending, and divergent versions.

### 516. Research ALTER TABLE locks

Measure the lock mode of each schema operation.

### 517. Add a nullable column

Check a metadata-only operation.

### 518. Add a column with a constant default

Check fast-default behavior in modern PostgreSQL versions.

### 519. Add a volatile default

Determine whether the operation causes a table rewrite.

### 520. Add NOT NULL safely

Use a validated check constraint and metadata transition.

### 521. Add a foreign key safely

Use `NOT VALID` and a separate `VALIDATE CONSTRAINT`.

### 522. Create an index concurrently

Do not block ordinary writes.

### 523. Drop an index concurrently

Minimize blocking impact.

### 524. Rename a column

Evaluate compatibility of application versions.

### 525. Perform an expand-contract migration

First add the new schema, then migrate the code and remove the old schema.

### 526. Implement dual write

Temporarily write old and new representations.

### 527. Implement backfill

Update rows in small batches.

### 528. Add resumable backfill

Store progress and safely continue after failure.

### 529. Add backfill throttling

Limit load by latency, replication lag, and lock pressure.

### 530. Use SKIP LOCKED for backfill

Distribute batches among multiple workers.

### 531. Use keyset pagination

Do not use OFFSET for large migration batches.

### 532. Implement an idempotent migration

Allow safe repetition of the operation.

### 533. Research a table-rewrite migration

Measure disk space, WAL, and lock requirements.

### 534. Change a data type without a rewrite

Check binary-compatible conversions.

### 535. Change a data type with USING

Control conversion and invalid data.

### 536. Separate constraint creation and validation

Minimize the duration of a blocking lock.

### 537. Rebuild a large table

Compare a shadow table, logical replication, and a maintenance window.

### 538. Research view-based compatibility

Preserve the old API schema through a compatibility view.

### 539. Research trigger-based migration

Synchronize old and new tables while accounting for complexity.

### 540. Check migration rollback

Separate a reversible schema change and an irreversible data transformation.

### 541. Create preflight checks

Check disk space, locks, invalid data, and replication lag.

### 542. Create a migration timeout policy

Use `lock_timeout` and `statement_timeout`.

### 543. Observe migration progress

Use progress views and custom backfill metrics.

### 544. Create a migration dry run

Run against a copy of production-like schema and data distribution.

### 545. Test mixed application versions

Check backward compatibility during rolling deployment.

### 546. Create schema-drift detection

Compare expected migrations and the actual database schema.

### 547. Create a migration audit

Record version, operator, duration, and result.

### 548. Create failed-migration recovery

Document cleanup of invalid indexes and partial backfills.

### 549. Create a production migration checklist

Check locks, WAL, storage, backups, and rollback.

### 550. Create a zero-downtime migration scenario

Execute the complete expand-backfill-switch-contract sequence.

## 20. Partitioning

### 551. Research declarative partitioning

Analyze a partitioned table and child partitions.

### 552. Create range partitioning

Partition a time-series table by month.

### 553. Create list partitioning

Partition data by region or category.

### 554. Create hash partitioning

Distribute tenants among a fixed number of partitions.

### 555. Create multilevel partitioning

Combine range and hash.

### 556. Research partition-key design

Choose a key based on pruning, retention, and write distribution.

### 557. Research partition constraints

Check automatic bounds constraints.

### 558. Research partition pruning

Check the plan with a constant predicate.

### 559. Research runtime pruning

Check a parameterized nested loop and prepared statement.

### 560. Research the default partition

Handle rows outside existing bounds.

### 561. Create future partitions

Automate partition creation in advance.

### 562. Implement partition retention

Delete historical data through `DROP` or `DETACH PARTITION`.

### 563. Compare DELETE and DROP PARTITION

Measure locks, WAL, and duration.

### 564. Research ATTACH PARTITION

Attach a preloaded table with a validated constraint.

### 565. Research DETACH PARTITION CONCURRENTLY

Minimize blocking during archiving.

### 566. Research indexes on partitioned tables

Create corresponding indexes on partitions.

### 567. Research unique constraints in partitioning

Understand the requirement to include the partition key.

### 568. Research foreign keys in partitioning

Check supported directions and operational cost.

### 569. Research partition-wise aggregate

Perform aggregation separately by partition.

### 570. Research partition-wise join

Use aligned partitioning.

### 571. Measure planning overhead

Check a large number of partitions.

### 572. Research partition metadata locks

Check DDL and concurrent queries.

### 573. Research partitioned autovacuum

Configure parameters for individual child tables.

### 574. Research partitioned statistics

Check parent and child statistics.

### 575. Research the absence of global indexes

Analyze uniqueness limitations across partitions.

### 576. Implement tenant partitioning

Compare hash partitioning and a shared table with composite indexes.

### 577. Research skewed partitions

Check uneven data and hot partitions.

### 578. Implement partition rebalancing

Redistribute hash buckets or tenants.

### 579. Create a partition-maintenance job

Automate create, detach, archive, and drop.

### 580. Document the partitioning decision

Record cases where partitioning is beneficial or complicates the system.


## 21. Replication and High Availability

### 581. Research physical replication

Analyze WAL streaming and a byte-identical standby.

### 582. Configure primary and standby

Create a streaming-replication environment.

### 583. Create a replication role

Restrict privileges and pg_hba rules.

### 584. Research replication slots

Prevent deletion of WAL required by a standby.

### 585. Monitor slot retention

Prevent disk exhaustion caused by an inactive slot.

### 586. Research asynchronous replication

Measure replication lag and possible loss of committed transactions.

### 587. Research synchronous replication

Configure waiting for standby confirmation.

### 588. Research synchronous_standby_names

Check priority and quorum modes.

### 589. Research hot standby

Execute read-only queries on a replica.

### 590. Research recovery conflicts

Check cancellation of standby queries because of WAL replay.

### 591. Configure hot_standby_feedback

Compare reduced conflicts and increased bloat on the primary.

### 592. Configure max_standby_streaming_delay

Manage the balance between query duration and replay lag.

### 593. Research replication-lag metrics

Compare write, flush, replay LSN, and time lag.

### 594. Perform a planned switchover

Promote the standby and redirect clients.

### 595. Perform an unplanned failover

Lose the primary and evaluate data loss.

### 596. Research split-brain risk

Record the need for fencing and consensus.

### 597. Research timeline history

Understand new timelines after promotion.

### 598. Research pg_rewind

Return the old primary to the new cluster.

### 599. Research cascading replication

Connect a standby to another standby.

### 600. Research logical replication

Analyze publications, subscriptions, and logical decoding.

### 601. Create a publication

Publish selected tables and operations.

### 602. Create a subscription

Synchronize initial data and changes.

### 603. Research replica identity

Configure UPDATE and DELETE when a suitable primary key is absent.

### 604. Research logical-replication conflicts

Handle duplicate keys and schema mismatch.

### 605. Research the sequence-replication gap

Record that sequence state is not replicated as table data.

### 606. Research logical-replication DDL

Document the need for separate schema synchronization.

### 607. Implement selective data replication

Replicate a subset of tables or rows according to the capabilities of the selected version.

### 608. Research a major-version upgrade

Compare `pg_upgrade` and logical replication.

### 609. Create HA failure scenarios

Check primary crash, network partition, lagging standby, and slot failure.

### 610. Prepare a production readiness checklist

Record schema, indexes, planner, transactions, vacuum, WAL, backups, replication, monitoring, and recovery requirements.
