# PG Forge Database Lab Roadmap

## 1. Основы PostgreSQL и relational database systems

### 001. Исследовать relational model

Разобрать relations, tuples, attributes, keys, predicates и ограничения relational model.

### 002. Исследовать SQL execution lifecycle

Проследить путь запроса от parser и analyzer до planner, executor и возврата результата.

### 003. Исследовать архитектуру PostgreSQL

Разобрать postmaster, backend processes, shared memory, background workers и auxiliary processes.

### 004. Исследовать process-per-connection model

Определить влияние отдельного backend process на memory usage, connection limits и scalability.

### 005. Исследовать PostgreSQL memory architecture

Разобрать shared_buffers, work_mem, maintenance_work_mem, local memory и operating-system cache.

### 006. Исследовать PostgreSQL storage hierarchy

Разобрать cluster, database, tablespace, relation, fork, segment, page и tuple.

### 007. Исследовать system catalogs

Определить назначение `pg_class`, `pg_attribute`, `pg_type`, `pg_index`, `pg_constraint` и других catalogs.

### 008. Исследовать information_schema

Сравнить standard-compatible metadata views с PostgreSQL-specific system catalogs.

### 009. Исследовать PostgreSQL extensions

Разобрать extension lifecycle, control files, SQL migrations и dependency management.

### 010. Исследовать PostgreSQL configuration hierarchy

Разобрать `postgresql.conf`, `ALTER SYSTEM`, database-level, role-level и session-level settings.

### 011. Исследовать transaction processing

Определить роль transactions, atomicity, consistency, isolation и durability.

### 012. Исследовать MVCC

Разобрать видимость tuple versions без блокировки обычных readers и writers.

### 013. Исследовать query optimization

Определить роль statistics, cost model, selectivity и plan alternatives.

### 014. Исследовать durability

Разобрать WAL, checkpoints, fsync, full-page writes и crash recovery.

### 015. Исследовать concurrency control

Разобрать snapshots, locks, deadlocks, predicate locking и serialization failures.

### 016. Исследовать database normalization

Разобрать functional dependencies и нормальные формы от 1NF до BCNF.

### 017. Исследовать denormalization

Определить случаи осознанного дублирования данных ради чтения и аналитических запросов.

### 018. Исследовать OLTP и OLAP workloads

Сравнить patterns запросов, transaction size, indexing и storage requirements.

### 019. Исследовать PostgreSQL release lifecycle

Определить major versions, minor updates, compatibility и upgrade requirements.

### 020. Зафиксировать цели лаборатории

Документировать набор исследуемых internals, production scenarios и критерии проверки результатов.

## 2. Локальная среда и инструменты

### 021. Создать структуру репозитория

Разделить schema, migrations, experiments, benchmarks, scripts, reports и documentation.

### 022. Подготовить Docker Compose

Развернуть PostgreSQL, PgBouncer, Prometheus exporter и Grafana.

### 023. Зафиксировать версию PostgreSQL

Использовать конкретный major release и документировать отличия от соседних версий.

### 024. Настроить persistent storage

Сохранять `PGDATA` между перезапусками и позволить отдельные сценарии полного сброса cluster.

### 025. Настроить custom postgresql.conf

Подключить отдельный конфигурационный файл с параметрами для experiments.

### 026. Настроить pg_hba.conf

Создать явные правила local, application, replication и administration connections.

### 027. Создать database roles

Разделить migration, application, read-only, monitoring и replication roles.

### 028. Настроить psql

Добавить `.psqlrc`, expanded output, timing и удобное отображение query plans.

### 029. Подключить pg_stat_statements

Собирать нормализованную статистику SQL-запросов.

### 030. Подключить auto_explain

Автоматически логировать plans медленных запросов.

### 031. Подключить pageinspect

Исследовать содержимое heap и index pages.

### 032. Подключить pgstattuple

Измерять live tuples, dead tuples и bloat.

### 033. Подключить amcheck

Проверять физическую целостность B-tree indexes.

### 034. Подключить pg_buffercache

Исследовать содержимое shared buffer cache.

### 035. Подключить pg_prewarm

Управлять предварительной загрузкой relations в cache.

### 036. Подключить hypopg

Создавать hypothetical indexes без фактического построения.

### 037. Подключить pg_trgm

Исследовать trigram indexes и fuzzy search.

### 038. Подготовить генератор тестовых данных

Создавать reproducible datasets разного размера и распределения.

### 039. Создать сценарии сброса лаборатории

Автоматизировать удаление и повторное создание schema, data и statistics.

### 040. Создать шаблон отчёта experiment

Фиксировать hypothesis, setup, SQL, measurements, plan и conclusions.

## 3. Физическое хранение и страницы

### 041. Исследовать database cluster layout

Разобрать назначение `base`, `global`, `pg_wal`, `pg_tblspc` и других directories.

### 042. Исследовать relation files

Определить связь relation OID, relfilenode и physical files.

### 043. Исследовать relation forks

Разобрать main, free space map, visibility map и initialization forks.

### 044. Исследовать relation segmentation

Проверить разбиение больших relations на segment files.

### 045. Исследовать PostgreSQL pages

Разобрать fixed-size page, page header, line pointers и tuple data.

### 046. Исследовать heap page layout

Использовать `pageinspect` для анализа tuple placement.

### 047. Исследовать tuple header

Разобрать `xmin`, `xmax`, `ctid`, infomask и null bitmap.

### 048. Исследовать item pointers

Определить роль line pointer и tuple relocation.

### 049. Исследовать CTID

Проверить изменение physical tuple location после UPDATE и VACUUM FULL.

### 050. Исследовать free space map

Проверить, как PostgreSQL находит pages со свободным местом.

### 051. Исследовать visibility map

Разобрать all-visible и all-frozen bits.

### 052. Исследовать fillfactor

Измерить влияние свободного пространства pages на UPDATE и bloat.

### 053. Исследовать TOAST

Разобрать compression, out-of-line storage и TOAST tables.

### 054. Исследовать TOAST thresholds

Проверить момент перехода больших values в compressed или external storage.

### 055. Исследовать varlena representation

Разобрать хранение variable-length values.

### 056. Исследовать tuple alignment

Определить влияние порядка columns на padding и row size.

### 057. Сравнить порядок columns

Измерить physical row size для разных вариантов schema.

### 058. Исследовать page splits

Проверить split behavior B-tree pages при случайных и последовательных inserts.

### 059. Исследовать relation extension

Проверить выделение новых pages при росте table.

### 060. Исследовать table rewrites

Определить operations, вызывающие полную физическую перезапись table.

### 061. Исследовать unlogged tables

Сравнить performance, WAL generation и crash behavior.

### 062. Исследовать temporary tables

Разобрать session scope, catalog overhead и storage behavior.

### 063. Исследовать tablespaces

Создать отдельный tablespace и переместить relation.

### 064. Исследовать data checksums

Проверить назначение page checksums и ограничения их включения.

### 065. Исследовать relation size functions

Использовать `pg_relation_size`, `pg_table_size` и `pg_total_relation_size`.

### 066. Исследовать block reads

Сопоставить logical и physical reads для relation.

### 067. Исследовать cache warming

Сравнить cold-cache и warm-cache execution.

### 068. Исследовать operating-system page cache

Определить взаимодействие shared_buffers и filesystem cache.

### 069. Исследовать direct I/O ограничения

Разобрать традиционную зависимость PostgreSQL от operating-system cache.

### 070. Документировать storage internals

Создать схему physical storage hierarchy и tuple lifecycle.

## 4. Типы данных

### 071. Исследовать integer types

Сравнить `smallint`, `integer` и `bigint` по range и storage size.

### 072. Исследовать numeric

Разобрать arbitrary precision, scale, storage и computational cost.

### 073. Сравнить numeric и floating-point

Проверить precision и performance `numeric`, `real` и `double precision`.

### 074. Исследовать monetary representation

Сравнить integer minor units и `numeric` для денежных значений.

### 075. Исследовать character types

Сравнить `text`, `varchar` и `char`.

### 076. Проверить ограничения varchar

Определить, когда length constraint даёт business value.

### 077. Исследовать collations

Разобрать locale-aware comparison и sorting.

### 078. Исследовать deterministic collations

Определить влияние deterministic mode на equality и indexing.

### 079. Исследовать ICU collations

Создать и проверить ICU collation.

### 080. Исследовать case-insensitive text

Сравнить normalized text, functional index и `citext`.

### 081. Исследовать boolean

Зафиксировать корректное использование `boolean` вместо nullable status flags.

### 082. Исследовать date и time types

Сравнить `date`, `time`, `timestamp` и `timestamptz`.

### 083. Исследовать timestamp semantics

Проверить хранение и отображение `timestamp with time zone`.

### 084. Исследовать intervals

Разобрать months, days, microseconds и calendar arithmetic.

### 085. Исследовать timezone behavior

Проверить session timezone и daylight-saving transitions.

### 086. Исследовать UUID

Сравнить UUID versions, generation и index locality.

### 087. Исследовать sequential identifiers

Сравнить `serial`, identity columns, UUID и ULID-like identifiers.

### 088. Исследовать sequences

Разобрать caching, gaps, concurrency и transaction independence.

### 089. Исследовать identity columns

Сравнить `GENERATED ALWAYS` и `GENERATED BY DEFAULT`.

### 090. Исследовать enum types

Определить преимущества, ограничения migrations и alternative lookup tables.

### 091. Исследовать domains

Создать reusable constrained domain type.

### 092. Исследовать composite types

Использовать user-defined composite type и определить его ограничения.

### 093. Исследовать arrays

Разобрать storage, operators, indexing и normalization trade-offs.

### 094. Исследовать JSON

Сравнить textual JSON и binary JSONB.

### 095. Исследовать JSONB storage

Проверить normalization, key ordering и duplicate keys.

### 096. Исследовать JSONB operators

Использовать containment, extraction и path queries.

### 097. Исследовать range types

Применить `int4range`, `daterange` и `tstzrange`.

### 098. Исследовать multirange types

Хранить наборы непересекающихся ranges.

### 099. Исследовать network types

Использовать `inet`, `cidr` и network operators.

### 100. Исследовать binary data

Сравнить `bytea`, large objects и external object storage.

### 101. Исследовать full-text types

Разобрать `tsvector`, `tsquery` и dictionaries.

### 102. Исследовать geometric types

Проверить встроенные point, box и path types.

### 103. Исследовать generated columns

Создать stored generated column и измерить write/read trade-off.

### 104. Исследовать null semantics

Разобрать three-valued logic и `IS DISTINCT FROM`.

### 105. Создать руководство выбора типов

Документировать правила выбора PostgreSQL data types для production schema.

## 5. Проектирование schema

### 106. Спроектировать демонстрационный domain

Создать схему customers, organizations, projects, orders, payments и events.

### 107. Определить primary keys

Выбрать natural или surrogate keys для каждой entity.

### 108. Исследовать natural keys

Оценить stability, size и propagation business identifiers.

### 109. Исследовать surrogate keys

Оценить простоту joins, migrations и distributed generation.

### 110. Реализовать normalization до 3NF

Устранить repeating groups, partial и transitive dependencies.

### 111. Исследовать BCNF

Найти relation, где 3NF недостаточна для устранения anomalies.

### 112. Исследовать denormalized read model

Создать отдельную таблицу для ускорения сложного read path.

### 113. Сравнить entity table и JSONB blob

Измерить queryability, validation и indexing.

### 114. Спроектировать one-to-one relation

Выбрать shared primary key или unique foreign key.

### 115. Спроектировать one-to-many relation

Настроить foreign key и indexes для parent-child access.

### 116. Спроектировать many-to-many relation

Создать join table с composite uniqueness.

### 117. Спроектировать hierarchical data

Сравнить adjacency list, materialized path, nested sets и closure table.

### 118. Реализовать adjacency list

Создать recursive queries через `WITH RECURSIVE`.

### 119. Реализовать materialized path

Использовать `ltree` или textual path representation.

### 120. Реализовать closure table

Поддержать быстрый поиск ancestors и descendants.

### 121. Спроектировать polymorphic relations

Сравнить nullable foreign keys, association tables и shared parent entity.

### 122. Избежать generic entity-attribute-value model

Показать проблемы typing, constraints и query planning EAV.

### 123. Спроектировать status model

Сравнить enum, lookup table и state transition table.

### 124. Спроектировать temporal data

Хранить valid-time и system-time intervals.

### 125. Реализовать append-only history

Сохранять изменения сущности отдельными immutable records.

### 126. Реализовать audit snapshot model

Хранить before и after representation с metadata.

### 127. Спроектировать soft deletion

Добавить `deleted_at` и определить влияние на uniqueness и indexes.

### 128. Спроектировать archival model

Перемещать historical data в отдельные partitions или tables.

### 129. Спроектировать multi-tenant schema

Добавить tenant key во все tenant-owned relations.

### 130. Добавить composite tenant constraints

Исключить cross-tenant references на database level.

## 6. Constraints и целостность данных

### 131. Реализовать primary key constraints

Проверить автоматическое создание unique B-tree index.

### 132. Реализовать foreign key constraints

Проверить referential integrity при insert, update и delete.

### 133. Исследовать foreign key indexes

Показать, что PostgreSQL не создаёт index на referencing column автоматически.

### 134. Исследовать foreign key actions

Сравнить `NO ACTION`, `RESTRICT`, `CASCADE`, `SET NULL` и `SET DEFAULT`.

### 135. Исследовать deferred foreign keys

Отложить проверку constraint до commit.

### 136. Реализовать unique constraints

Зафиксировать business uniqueness на database level.

### 137. Исследовать nulls в unique constraints

Проверить поведение нескольких NULL values.

### 138. Использовать NULLS NOT DISTINCT

Запретить несколько NULL values в unique constraint.

### 139. Реализовать composite uniqueness

Закрепить uniqueness внутри tenant или parent resource.

### 140. Реализовать partial uniqueness

Использовать partial unique index для active records.

### 141. Реализовать check constraints

Закрепить ranges, status combinations и invariants.

### 142. Исследовать check constraint limitations

Показать, почему check не должен зависеть от других rows.

### 143. Реализовать exclusion constraint

Запретить пересекающиеся ranges через GiST.

### 144. Исследовать NOT NULL

Сравнить column-level NOT NULL и equivalent CHECK.

### 145. Добавить constraints через NOT VALID

Подготовить low-lock rollout constraint на большой table.

### 146. Выполнить VALIDATE CONSTRAINT

Проверить existing rows отдельно от короткой metadata operation.

### 147. Исследовать constraint locking

Измерить locks при добавлении и validation constraints.

### 148. Создать domain constraints

Переиспользовать validation через custom domain.

### 149. Реализовать transition constraints

Использовать trigger только для invariants, не выражаемых declarative constraints.

### 150. Исследовать assertions absence

Разобрать отсутствие standard SQL ASSERTION в PostgreSQL.

### 151. Реализовать immutable column protection

Запретить изменение business identifier через trigger.

### 152. Реализовать cross-row invariant

Создать transaction-safe механизм для ограничения между несколькими rows.

### 153. Проверить race condition SELECT-then-INSERT

Показать, почему application-side uniqueness недостаточна.

### 154. Использовать INSERT ON CONFLICT

Реализовать atomic upsert на основе unique constraint.

### 155. Исследовать ON CONFLICT concurrency

Проверить поведение competing inserts.

### 156. Использовать RETURNING

Получать данные изменённых rows без дополнительного SELECT.

### 157. Реализовать generated defaults

Использовать database-generated identifiers и timestamps.

### 158. Запретить invalid state combinations

Добавить composite check constraints.

### 159. Создать integrity test suite

Намеренно нарушать constraints и проверять ожидаемые SQLSTATE.

### 160. Документировать ownership constraints

Зафиксировать invariants, гарантируемые database, application и external systems.

## 7. B-tree indexes

### 161. Исследовать B-tree structure

Разобрать root, internal, leaf pages и sibling links.

### 162. Создать single-column B-tree index

Измерить влияние на equality и range query.

### 163. Исследовать index tuple layout

Разобрать key data, TID и included columns.

### 164. Исследовать B-tree operator classes

Определить связь operators и index ordering.

### 165. Исследовать ascending и descending indexes

Проверить backward scan и mixed-order multicolumn index.

### 166. Исследовать NULLS FIRST и NULLS LAST

Проверить использование index для сортировки nullable values.

### 167. Создать multicolumn index

Исследовать leftmost prefix rule.

### 168. Исследовать skip scan

Проверить возможность использования позднего column multicolumn index.

### 169. Измерить selectivity первого column

Сравнить порядок columns при разных query patterns.

### 170. Создать covering index

Использовать INCLUDE для index-only scan.

### 171. Исследовать INCLUDE limitations

Определить влияние included columns на index size и uniqueness.

### 172. Создать partial index

Индексировать только active или frequently queried rows.

### 173. Проверить predicate matching

Показать, когда planner не может доказать соответствие WHERE partial index predicate.

### 174. Создать expression index

Индексировать `lower(email)` или вычисляемое выражение.

### 175. Проверить expression equivalence

Показать влияние casts и function wrapping на index usage.

### 176. Исследовать immutable functions

Определить требования к expressions в index.

### 177. Создать unique expression index

Закрепить case-insensitive uniqueness.

### 178. Исследовать index deduplication

Проверить уменьшение B-tree при повторяющихся keys.

### 179. Исследовать index fillfactor

Измерить page splits и free space.

### 180. Исследовать index correlation

Связать physical heap order и planner cost.

### 181. Использовать CLUSTER

Перестроить table в порядке index и измерить range scans.

### 182. Проверить degradation после CLUSTER

Показать потерю physical ordering при последующих writes.

### 183. Использовать REINDEX

Перестроить повреждённый или bloated index.

### 184. Использовать REINDEX CONCURRENTLY

Перестроить index с минимальной блокировкой writes.

### 185. Исследовать duplicate indexes

Найти indexes, покрывающие одинаковые column prefixes.

### 186. Исследовать unused indexes

Использовать `pg_stat_user_indexes` и учитывать reset statistics.

### 187. Измерить write amplification

Сравнить INSERT и UPDATE performance при разном числе indexes.

### 188. Измерить index size

Использовать `pg_relation_size` и `pgstattuple`.

### 189. Исследовать index bloat

Создать churn workload и измерить growth.

### 190. Проверить B-tree integrity

Использовать `amcheck`.

### 191. Исследовать concurrent index build

Проверить phases и invalid index states.

### 192. Обработать failed CREATE INDEX CONCURRENTLY

Найти и удалить invalid index.

### 193. Исследовать lock behavior index DDL

Измерить locks обычного и concurrent index creation.

### 194. Создать index naming convention

Зафиксировать стабильные и понятные names.

### 195. Документировать B-tree decision rules

Составить руководство выбора single, composite, partial, expression и covering indexes.

## 8. Другие index access methods

### 196. Исследовать Hash indexes

Сравнить equality lookups, WAL support и ограничения.

### 197. Создать Hash index

Измерить размер и performance относительно B-tree.

### 198. Исследовать GiST

Разобрать generalized search tree и extensible operator classes.

### 199. Создать GiST range index

Ускорить overlap и containment queries.

### 200. Создать GiST geometric index

Проверить spatial operators.

### 201. Исследовать SP-GiST

Разобрать space-partitioned search trees.

### 202. Создать SP-GiST index

Проверить prefix или geometric workload.

### 203. Исследовать GIN

Разобрать inverted index для composite values.

### 204. Создать GIN JSONB index

Ускорить containment queries.

### 205. Сравнить jsonb_ops и jsonb_path_ops

Измерить размер, supported operators и performance.

### 206. Создать GIN array index

Ускорить containment и overlap.

### 207. Создать GIN full-text index

Ускорить `tsvector` search.

### 208. Исследовать GIN pending list

Разобрать fastupdate и deferred index maintenance.

### 209. Измерить GIN write cost

Сравнить inserts с `fastupdate` enabled и disabled.

### 210. Исследовать BRIN

Разобрать block range summaries.

### 211. Создать BRIN index

Применить его к large append-only time-series table.

### 212. Измерить влияние correlation на BRIN

Сравнить ordered и randomized data.

### 213. Исследовать BRIN pages_per_range

Подобрать granularity и index size.

### 214. Использовать BRIN autosummarize

Проверить автоматическое summarization новых ranges.

### 215. Исследовать Bloom indexes

Подключить extension и проверить multicolumn equality workload.

### 216. Сравнить B-tree и Bloom

Оценить false positives, size и workload applicability.

### 217. Исследовать trigram GIN

Ускорить `LIKE`, `ILIKE` и similarity search.

### 218. Исследовать trigram GiST

Сравнить с GIN для fuzzy matching.

### 219. Исследовать full-text search configuration

Разобрать parser, dictionaries, lexemes и weights.

### 220. Создать weighted tsvector

Назначить разный вес title и body.

### 221. Создать generated tsvector column

Автоматически поддерживать searchable representation.

### 222. Исследовать phrase search

Использовать phrase operators и positions.

### 223. Исследовать custom operator classes

Разобрать связь access method, strategy numbers и support functions.

### 224. Исследовать index access method API

Изучить базовую структуру extensibility PostgreSQL indexes.

### 225. Создать matrix index types

Сопоставить data type, operators, access method и workload.

## 9. Query planner и statistics

### 226. Исследовать parser

Разобрать преобразование SQL text в parse tree.

### 227. Исследовать analyzer

Проверить resolution relations, columns, types и implicit casts.

### 228. Исследовать rewrite system

Разобрать rules, views и query tree rewriting.

### 229. Исследовать planner

Определить generation paths, cost comparison и final plan.

### 230. Исследовать executor

Разобрать pull-based execution plan nodes.

### 231. Исследовать PostgreSQL cost model

Разобрать startup cost, total cost и arbitrary cost units.

### 232. Исследовать seq_page_cost

Измерить влияние стоимости sequential I/O.

### 233. Исследовать random_page_cost

Проверить выбор index scan при SSD-like configuration.

### 234. Исследовать cpu_tuple_cost

Определить влияние CPU cost на plan selection.

### 235. Исследовать cpu_index_tuple_cost

Разобрать стоимость index tuple processing.

### 236. Исследовать cpu_operator_cost

Проверить влияние expensive predicates.

### 237. Исследовать effective_cache_size

Понять его роль как planner estimate, а не memory allocation.

### 238. Исследовать table statistics

Разобрать `reltuples`, `relpages` и их approximate nature.

### 239. Исследовать column statistics

Разобрать null fraction, distinct count и average width.

### 240. Исследовать most common values

Проверить MCV list для skewed distribution.

### 241. Исследовать histograms

Проверить selectivity range predicates.

### 242. Исследовать correlation statistics

Связать physical ordering и index scan cost.

### 243. Исследовать default_statistics_target

Измерить точность estimates и ANALYZE cost.

### 244. Настроить per-column statistics target

Увеличить statistics для skewed column.

### 245. Запустить ANALYZE

Проверить изменение cardinality estimates.

### 246. Исследовать sampling

Понять, почему statistics являются approximate.

### 247. Создать extended statistics dependencies

Улучшить estimates коррелирующих columns.

### 248. Создать extended statistics ndistinct

Улучшить GROUP BY и multicolumn estimates.

### 249. Создать extended statistics MCV

Улучшить estimates комбинаций frequent values.

### 250. Исследовать stale statistics

Показать плохой plan после массового изменения данных.

### 251. Исследовать planner row estimates

Сравнить estimated и actual rows для каждого plan node.

### 252. Исследовать selectivity equality

Проверить estimates для uniform и skewed values.

### 253. Исследовать selectivity ranges

Проверить histogram boundaries.

### 254. Исследовать selectivity LIKE

Проверить prefix и non-prefix patterns.

### 255. Исследовать selectivity joins

Проверить estimates при foreign key и non-unique relations.

### 256. Исследовать functional dependencies

Показать улучшение estimates extended statistics.

### 257. Исследовать parameterized queries

Проверить влияние неизвестного parameter value на planning.

### 258. Исследовать generic plan

Определить условия перехода prepared statement на generic plan.

### 259. Исследовать custom plan

Сравнить plans для selective и non-selective parameters.

### 260. Настроить plan_cache_mode

Принудительно использовать generic или custom planning.

### 261. Исследовать prepared statement invalidation

Проверить replan после DDL или statistics changes.

### 262. Исследовать implicit casts

Показать потерю index usage из-за type mismatch.

### 263. Исследовать function volatility

Разобрать VOLATILE, STABLE и IMMUTABLE.

### 264. Исследовать planner constant folding

Проверить вычисление immutable expressions во время planning.

### 265. Исследовать constraint exclusion

Проверить исключение relations по constraints.

### 266. Исследовать partition pruning

Сравнить planning-time и execution-time pruning.

### 267. Исследовать join order search

Разобрать dynamic programming и GEQO.

### 268. Настроить join_collapse_limit

Проверить влияние на join reordering.

### 269. Настроить from_collapse_limit

Проверить flattening subqueries.

### 270. Исследовать GEQO

Проверить planning больших join graphs.

## 10. Scan и join algorithms

### 271. Исследовать Sequential Scan

Определить случаи, когда Seq Scan дешевле index access.

### 272. Исследовать Index Scan

Разобрать heap fetches и random access.

### 273. Исследовать Index Only Scan

Понять роль visibility map и heap fetches.

### 274. Исследовать Bitmap Index Scan

Разобрать построение bitmap matching TIDs.

### 275. Исследовать Bitmap Heap Scan

Проверить exact и lossy heap blocks.

### 276. Исследовать TID Scan

Получить tuple по CTID и определить ограничения.

### 277. Исследовать Subquery Scan

Разобрать materialized и inline subqueries.

### 278. Исследовать Function Scan

Проверить set-returning function в FROM.

### 279. Исследовать Values Scan

Разобрать execution inline VALUES.

### 280. Исследовать Nested Loop Join

Определить подходящие workloads и parameterized inner scans.

### 281. Исследовать Hash Join

Разобрать build и probe phases.

### 282. Исследовать Hash Join batching

Проверить spill на disk при недостаточном work_mem.

### 283. Исследовать Merge Join

Понять требования к sorted inputs.

### 284. Сравнить join algorithms

Измерить performance при разных cardinalities и indexes.

### 285. Исследовать semi join

Разобрать EXISTS и IN transformations.

### 286. Исследовать anti join

Разобрать NOT EXISTS и anti-join semantics.

### 287. Исследовать lateral joins

Использовать parameterized subquery для каждой outer row.

### 288. Исследовать join removal

Проверить удаление ненужного join при foreign key и uniqueness.

### 289. Исследовать partition-wise join

Сравнить joins partitioned tables.

### 290. Исследовать parallel hash join

Проверить shared hash table между workers.

### 291. Отключить отдельные plan types

Использовать `enable_seqscan`, `enable_hashjoin` и другие settings для экспериментов.

### 292. Не использовать planner toggles как production fix

Документировать их роль только для diagnostics и controlled tuning.

### 293. Исследовать materialization

Проверить Materialize plan node и повторное чтение inner result.

### 294. Исследовать Memoize

Проверить caching parameterized scan results.

### 295. Создать decision matrix joins

Зафиксировать условия выбора Nested Loop, Hash Join и Merge Join.

## 11. Sorting, aggregation и parallel execution

### 296. Исследовать Sort node

Разобрать quicksort, top-N heapsort и external merge.

### 297. Исследовать sort spill

Проверить temporary files при недостаточном work_mem.

### 298. Исследовать incremental sort

Использовать частично отсортированный input.

### 299. Исследовать top-N sorting

Сравнить ORDER BY с LIMIT и без LIMIT.

### 300. Исследовать HashAggregate

Разобрать hash table grouping.

### 301. Исследовать GroupAggregate

Использовать sorted input для aggregation.

### 302. Исследовать MixedAggregate

Проверить mixed strategy для grouping sets.

### 303. Исследовать aggregate spill

Проверить batching при недостаточном work_mem.

### 304. Исследовать DISTINCT

Сравнить Sort + Unique и HashAggregate.

### 305. Исследовать window functions

Разобрать WindowAgg и sorting requirements.

### 306. Исследовать GROUPING SETS

Реализовать несколько уровней aggregation одним запросом.

### 307. Исследовать CTE inlining

Сравнить обычный CTE и `MATERIALIZED`.

### 308. Исследовать NOT MATERIALIZED

Позволить planner встроить CTE в основной query.

### 309. Исследовать recursive CTE

Разобрать Recursive Union и working table.

### 310. Исследовать parallel query

Определить parallel-safe operations и planner thresholds.

### 311. Исследовать Gather

Разобрать сбор tuples от parallel workers.

### 312. Исследовать Gather Merge

Сохранить sorted order от workers.

### 313. Настроить max_parallel_workers_per_gather

Проверить масштабирование одного query.

### 314. Исследовать parallel setup cost

Понять, почему маленькие queries не используют parallelism.

### 315. Исследовать parallel tuple cost

Проверить cost передачи tuples leader process.

### 316. Исследовать parallel sequential scan

Измерить large-table scan с разным числом workers.

### 317. Исследовать parallel index scan

Проверить поддерживаемые index access methods.

### 318. Исследовать parallel aggregate

Разобрать partial и finalize aggregation.

### 319. Исследовать JIT compilation

Определить compilation, optimization и expression execution phases.

### 320. Измерить JIT overhead

Сравнить короткие и CPU-intensive queries.

## 12. EXPLAIN и диагностика запросов

### 321. Использовать EXPLAIN

Читать plan tree без выполнения statement.

### 322. Использовать EXPLAIN ANALYZE

Сравнивать estimates и фактическое выполнение.

### 323. Использовать BUFFERS

Измерять shared hit, read, dirtied и written blocks.

### 324. Использовать WAL

Измерять WAL records, full-page images и bytes.

### 325. Использовать TIMING

Определить overhead per-node timing.

### 326. Использовать SUMMARY

Получать planning и execution time.

### 327. Использовать SETTINGS

Фиксировать planner settings, влияющие на plan.

### 328. Использовать VERBOSE

Просматривать output columns и qualified object names.

### 329. Использовать FORMAT JSON

Получать machine-readable query plan.

### 330. Создать parser EXPLAIN JSON

Извлекать nodes, estimates, timings и buffer metrics.

### 331. Анализировать loops

Правильно учитывать repeated execution plan node.

### 332. Анализировать rows removed by filter

Определять wasted work после scan.

### 333. Анализировать heap fetches

Оценивать эффективность Index Only Scan.

### 334. Анализировать lossy bitmap blocks

Определять недостаток work_mem и recheck overhead.

### 335. Анализировать sort method

Различать in-memory и external sort.

### 336. Анализировать hash batches

Определять spill Hash Join или HashAggregate.

### 337. Анализировать planning time

Исследовать сложные join graphs и partitioned schemas.

### 338. Анализировать execution time

Отделять executor cost от client transfer.

### 339. Сравнивать cold и warm plans

Запускать controlled experiments с cache state.

### 340. Создать checklist анализа query plan

Зафиксировать последовательность проверки estimates, scans, joins, memory и I/O.

## 13. Transactions и MVCC

### 341. Исследовать transaction boundaries

Сравнить implicit transactions, explicit BEGIN и autocommit.

### 342. Исследовать transaction IDs

Разобрать XID allocation и visibility.

### 343. Исследовать snapshots

Определить visible committed, in-progress и aborted transactions.

### 344. Исследовать xmin и xmax

Проверить tuple visibility при INSERT, UPDATE и DELETE.

### 345. Исследовать command IDs

Разобрать видимость изменений внутри одной transaction.

### 346. Исследовать tuple version chains

Проследить HOT и non-HOT update versions.

### 347. Исследовать UPDATE как INSERT+DELETE

Проверить создание новой tuple version.

### 348. Исследовать DELETE

Показать, что tuple физически остаётся до VACUUM.

### 349. Исследовать transaction commit

Разобрать commit record в WAL и visibility.

### 350. Исследовать rollback

Проверить сохранение aborted tuple versions до cleanup.

### 351. Исследовать subtransactions

Использовать SAVEPOINT и ROLLBACK TO SAVEPOINT.

### 352. Исследовать subtransaction overhead

Проверить большое количество savepoints.

### 353. Исследовать transaction snapshots в READ COMMITTED

Получать новый snapshot для каждого statement.

### 354. Исследовать snapshot в REPEATABLE READ

Сохранять единый snapshot transaction.

### 355. Исследовать read-only transactions

Ограничить mutations и использовать optimization opportunities.

### 356. Исследовать deferrable transactions

Использовать safe snapshot для serializable read-only workloads.

### 357. Исследовать long-running transactions

Показать удержание dead tuples и влияние на vacuum.

### 358. Исследовать idle in transaction

Проверить locks, snapshots и bloat risk.

### 359. Настроить idle_in_transaction_session_timeout

Автоматически завершать опасные idle transactions.

### 360. Настроить statement_timeout

Ограничивать duration statement.

### 361. Настроить transaction_timeout

Ограничивать общую duration transaction, если поддерживается выбранной версией.

### 362. Исследовать transaction read/write sets

Определить конфликтующие operations.

### 363. Исследовать atomic counters

Реализовать безопасный increment одним UPDATE.

### 364. Исследовать check-then-act race

Показать ошибочность application-side transaction logic без locks или constraints.

### 365. Реализовать transactional outbox

Атомарно сохранить domain state и event record.

### 366. Исследовать dual-write problem

Показать невозможность атомарного commit PostgreSQL и external broker без protocol.

### 367. Реализовать idempotent transaction

Использовать unique business key для повторной команды.

### 368. Исследовать commit latency

Измерить влияние synchronous_commit и storage.

### 369. Исследовать group commit

Проверить совместное flush нескольких transactions.

### 370. Документировать MVCC lifecycle

Создать diagram tuple versions, snapshots, commit и vacuum.

## 14. Isolation levels и anomalies

### 371. Исследовать READ UNCOMMITTED

Зафиксировать, что PostgreSQL обрабатывает его как READ COMMITTED.

### 372. Исследовать READ COMMITTED

Проверить statement-level snapshots.

### 373. Воспроизвести non-repeatable read

Показать изменение результата между statements.

### 374. Воспроизвести phantom-like behavior

Показать появление новых rows между statements.

### 375. Исследовать REPEATABLE READ

Проверить snapshot isolation semantics PostgreSQL.

### 376. Воспроизвести write skew

Показать anomaly snapshot isolation.

### 377. Исследовать lost update

Проверить поведение competing read-modify-write transactions.

### 378. Защититься от lost update

Использовать atomic UPDATE, row lock или optimistic version.

### 379. Исследовать SERIALIZABLE

Разобрать Serializable Snapshot Isolation.

### 380. Исследовать predicate locks

Проверить `pg_locks` для SIReadLock.

### 381. Воспроизвести serialization failure

Создать опасную dependency structure.

### 382. Реализовать retry SERIALIZABLE transactions

Повторять всю transaction после SQLSTATE `40001`.

### 383. Исследовать false-positive serialization failures

Понять conservative nature SSI detection.

### 384. Сравнить isolation levels

Зафиксировать anomalies, overhead и use cases.

### 385. Создать isolation test harness

Запускать синхронизированные concurrent sessions.

### 386. Исследовать read skew

Проверить inconsistent observations нескольких related rows.

### 387. Исследовать write skew mitigation

Использовать SERIALIZABLE или explicit locking.

### 388. Исследовать phantom protection

Сравнить snapshots и predicate locking.

### 389. Исследовать uniqueness conflicts

Проверить behavior concurrent inserts.

### 390. Исследовать ON CONFLICT под READ COMMITTED

Разобрать visibility конфликтующей row.

### 391. Исследовать application retries

Определить retryable SQLSTATE и backoff policy.

### 392. Запретить частичный retry transaction

Повторять весь unit of work, а не отдельный failed statement.

### 393. Исследовать side effects при retry

Не выполнять irreversible external call внутри retried transaction.

### 394. Реализовать optimistic concurrency control

Добавить version column и conditional UPDATE.

### 395. Реализовать pessimistic concurrency control

Использовать row-level locks.

## 15. Locks и deadlocks

### 396. Исследовать table-level locks

Разобрать PostgreSQL lock modes и compatibility matrix.

### 397. Исследовать ACCESS SHARE

Проверить lock обычного SELECT.

### 398. Исследовать ROW EXCLUSIVE

Проверить locks INSERT, UPDATE и DELETE.

### 399. Исследовать SHARE UPDATE EXCLUSIVE

Определить operations autovacuum и concurrent index build.

### 400. Исследовать ACCESS EXCLUSIVE

Проверить DDL, блокирующий все accesses.

### 401. Исследовать row-level locks

Разобрать FOR UPDATE, NO KEY UPDATE, SHARE и KEY SHARE.

### 402. Использовать SELECT FOR UPDATE

Заблокировать rows перед mutation.

### 403. Использовать FOR NO KEY UPDATE

Ограничить конфликтность при неизменяемом key.

### 404. Использовать FOR SHARE

Разобрать shared row lock semantics.

### 405. Использовать FOR KEY SHARE

Защитить referenced key от delete или key update.

### 406. Исследовать NOWAIT

Немедленно завершать operation при невозможности получить lock.

### 407. Исследовать SKIP LOCKED

Реализовать конкурентную обработку job queue.

### 408. Исследовать lock queues

Проверить порядок ожидания и влияние long holder.

### 409. Исследовать lock_timeout

Ограничивать ожидание lock.

### 410. Исследовать fast-path locks

Разобрать оптимизацию часто используемых relation locks.

### 411. Исследовать heavyweight locks

Проверить representation в shared lock table.

### 412. Исследовать lightweight locks

Разобрать внутренние synchronization primitives PostgreSQL.

### 413. Исследовать buffer pins

Понять их отличие от SQL-visible locks.

### 414. Исследовать advisory locks

Использовать session-level и transaction-level locks.

### 415. Создать advisory lock namespace

Исключить collisions между различными business resources.

### 416. Сравнить advisory и row locks

Зафиксировать database enforcement и application responsibility.

### 417. Воспроизвести deadlock

Создать две transactions с обратным порядком locks.

### 418. Исследовать deadlock detection

Проверить влияние `deadlock_timeout`.

### 419. Анализировать deadlock logs

Определять involved transactions, statements и objects.

### 420. Устранить deadlock lock ordering

Зафиксировать единый порядок захвата resources.

### 421. Устранить deadlock сокращением transaction

Минимизировать время удержания locks.

### 422. Реализовать deadlock retry

Повторять transaction после SQLSTATE `40P01`.

### 423. Исследовать foreign key locking

Проверить row locks при insert referencing row и delete referenced row.

### 424. Исследовать DDL locking

Измерить блокировки ALTER TABLE operations.

### 425. Создать lock diagnostics query

Показывать blockers, waiters, queries и transaction age.

## 16. HOT updates, VACUUM и bloat

### 426. Исследовать HOT update

Определить условия heap-only tuple update.

### 427. Проверить HOT eligibility

Обновлять non-indexed column при наличии места на page.

### 428. Проверить HOT prevention

Обновлять indexed column или page без свободного места.

### 429. Измерить HOT statistics

Использовать `n_tup_hot_upd` и related counters.

### 430. Исследовать pruning

Проверить очистку tuple chains во время page access.

### 431. Исследовать VACUUM

Разобрать cleanup heap, indexes, FSM и visibility map.

### 432. Исследовать VACUUM ANALYZE

Обновить statistics вместе с cleanup.

### 433. Исследовать VACUUM FULL

Проверить table rewrite, disk usage и ACCESS EXCLUSIVE lock.

### 434. Исследовать lazy vacuum

Разобрать phases обычного VACUUM.

### 435. Исследовать autovacuum launcher

Понять распределение работы между workers.

### 436. Исследовать autovacuum thresholds

Разобрать threshold и scale factor.

### 437. Настроить per-table autovacuum

Подобрать параметры для high-churn table.

### 438. Исследовать autovacuum_vacuum_cost_limit

Управлять aggressiveness background vacuum.

### 439. Исследовать autovacuum_naptime

Проверить частоту поиска нуждающихся tables.

### 440. Исследовать vacuum memory

Разобрать maintenance_work_mem и autovacuum_work_mem.

### 441. Исследовать vacuum progress

Использовать `pg_stat_progress_vacuum`.

### 442. Исследовать analyze progress

Проверить доступные progress views выбранной версии.

### 443. Исследовать dead tuple accumulation

Создать update/delete workload и измерить growth.

### 444. Исследовать table bloat

Сравнить logical data size и physical relation size.

### 445. Исследовать index bloat

Измерить unused space и duplicate index entries.

### 446. Использовать pgstattuple

Получить точную оценку dead tuples и free space.

### 447. Сравнить approximate bloat queries

Оценить ограничения catalog-based estimates.

### 448. Исследовать freeze

Разобрать frozen XIDs и tuple visibility.

### 449. Исследовать transaction ID wraparound

Понять критичность anti-wraparound vacuum.

### 450. Проверить relfrozenxid

Найти oldest unfrozen relations.

### 451. Исследовать vacuum_freeze_min_age

Определить момент ранней freeze.

### 452. Исследовать vacuum_freeze_table_age

Настроить aggressive freeze scan.

### 453. Исследовать autovacuum_freeze_max_age

Понять emergency autovacuum behavior.

### 454. Исследовать multixact IDs

Разобрать хранение shared row locks.

### 455. Исследовать multixact wraparound

Проверить monitoring requirements.

### 456. Исследовать visibility map и index-only scan

Показать ухудшение index-only scan при churn.

### 457. Исследовать vacuum truncation

Проверить возврат пустых end pages operating system.

### 458. Исследовать replication slots и vacuum

Показать удержание dead tuples старым xmin.

### 459. Исследовать long snapshot impact

Связать old snapshot и невозможность cleanup.

### 460. Создать vacuum tuning runbook

Зафиксировать диагностику dead tuples, autovacuum lag и wraparound risk.

## 17. WAL, checkpoints и crash recovery

### 461. Исследовать Write-Ahead Logging

Разобрать правило записи WAL до data pages.

### 462. Исследовать WAL records

Проверить WAL generation для INSERT, UPDATE, DELETE и index changes.

### 463. Исследовать WAL segments

Разобрать naming, size и recycling.

### 464. Исследовать WAL buffers

Понять промежуточное хранение records перед flush.

### 465. Исследовать LSN

Использовать Log Sequence Number для positions и replication.

### 466. Исследовать full-page writes

Понять защиту от torn pages после checkpoint.

### 467. Измерить full-page image overhead

Сравнить WAL volume сразу после checkpoint и позже.

### 468. Исследовать wal_compression

Измерить размер WAL и CPU overhead.

### 469. Исследовать synchronous_commit

Сравнить on, off и remote durability modes.

### 470. Исследовать fsync

Понять его влияние на durability и невозможность безопасного отключения в production.

### 471. Исследовать wal_sync_method

Сравнить platform-specific flush methods.

### 472. Исследовать checkpoints

Разобрать dirty buffer flushing и recovery distance.

### 473. Настроить checkpoint_timeout

Проверить frequency checkpoints.

### 474. Настроить max_wal_size

Управлять checkpoint pressure.

### 475. Настроить checkpoint_completion_target

Распределять I/O checkpoint во времени.

### 476. Исследовать checkpoint spikes

Наблюдать latency и write throughput.

### 477. Исследовать background writer

Разобрать очистку dirty buffers независимо от checkpoints.

### 478. Исследовать WAL writer

Понять background WAL flush.

### 479. Исследовать crash recovery

Прервать PostgreSQL process и проверить replay WAL.

### 480. Анализировать recovery logs

Проследить redo start, end и consistency point.

### 481. Исследовать unlogged table recovery

Проверить очистку unlogged relation после crash.

### 482. Исследовать WAL archiving

Настроить `archive_mode` и `archive_command`.

### 483. Проверить archive_command idempotency

Не считать повторный вызов ошибкой при уже сохранённом segment.

### 484. Исследовать archive backlog

Мониторить неархивированные WAL segments.

### 485. Настроить WAL retention

Учитывать replication slots, archive и standby requirements.

### 486. Исследовать wal_level

Сравнить minimal, replica и logical.

### 487. Исследовать commit timestamp

Включить и проверить tracking commit time при необходимости.

### 488. Исследовать WAL inspection

Использовать `pg_waldump` для анализа records.

### 489. Измерить WAL amplification

Сравнить workload с разным количеством indexes.

### 490. Документировать durability trade-offs

Зафиксировать влияние WAL, checkpoints и commit settings.

## 18. Backup и Point-in-Time Recovery

### 491. Исследовать logical backup

Сравнить `pg_dump`, `pg_dumpall` и selective export.

### 492. Создать custom-format backup

Использовать parallel restore и выборочную загрузку objects.

### 493. Исследовать physical backup

Использовать `pg_basebackup`.

### 494. Настроить backup manifest

Проверять целостность physical backup.

### 495. Настроить continuous archiving

Сохранять WAL для PITR.

### 496. Выполнить Point-in-Time Recovery

Восстановить cluster на момент до ошибочного DELETE.

### 497. Исследовать recovery targets

Использовать timestamp, transaction ID, LSN и named restore point.

### 498. Создать restore point

Зафиксировать marker перед опасной migration.

### 499. Проверить backup restore

Не считать backup валидным без регулярного восстановления.

### 500. Измерить Recovery Point Objective

Определить возможную потерю данных.

### 501. Измерить Recovery Time Objective

Определить длительность восстановления.

### 502. Исследовать parallel pg_restore

Подобрать число jobs и влияние indexes и constraints.

### 503. Исследовать backup consistency

Понять snapshots logical backup и WAL consistency physical backup.

### 504. Разделить schema и data restore

Восстанавливать pre-data, data и post-data sections.

### 505. Исследовать large-object backup

Проверить восстановление large objects.

### 506. Исследовать role и privilege backup

Сохранить global objects отдельно.

### 507. Создать backup retention policy

Определить full backups, WAL и expiration.

### 508. Шифровать backups

Защитить data at rest и keys.

### 509. Создать backup monitoring

Проверять age, size, completion и restore tests.

### 510. Создать disaster recovery runbook

Документировать полное восстановление PostgreSQL cluster.

## 19. Migrations и zero-downtime schema changes

### 511. Создать migration framework

Хранить versioned SQL migrations и immutable applied history.

### 512. Разделить transactional и non-transactional migrations

Учитывать `CREATE INDEX CONCURRENTLY` и другие operations.

### 513. Реализовать migration locking

Не запускать две migration processes одновременно.

### 514. Реализовать migration checksums

Обнаруживать изменение уже применённых files.

### 515. Создать migration status command

Показывать applied, pending и divergent versions.

### 516. Исследовать ALTER TABLE locks

Измерить lock mode каждой schema operation.

### 517. Добавить nullable column

Проверить metadata-only operation.

### 518. Добавить column с constant default

Проверить fast default behavior современных версий PostgreSQL.

### 519. Добавить volatile default

Определить, вызывает ли operation table rewrite.

### 520. Добавить NOT NULL безопасно

Использовать validated check constraint и metadata transition.

### 521. Добавить foreign key безопасно

Использовать `NOT VALID` и отдельный `VALIDATE CONSTRAINT`.

### 522. Создать index concurrently

Не блокировать обычные writes.

### 523. Удалить index concurrently

Минимизировать blocking impact.

### 524. Переименовать column

Оценить compatibility application versions.

### 525. Выполнить expand-contract migration

Сначала добавить новую schema, затем перевести код и удалить старую.

### 526. Реализовать dual write

Временно записывать old и new representations.

### 527. Реализовать backfill

Обновлять rows небольшими batches.

### 528. Добавить resumable backfill

Сохранять progress и безопасно продолжать после failure.

### 529. Добавить throttling backfill

Ограничивать load по latency, replication lag и lock pressure.

### 530. Использовать SKIP LOCKED для backfill

Распределять batches между несколькими workers.

### 531. Использовать keyset pagination

Не применять OFFSET для больших migration batches.

### 532. Реализовать idempotent migration

Позволить безопасный повтор operation.

### 533. Исследовать table rewrite migration

Измерить disk space, WAL и lock requirements.

### 534. Изменить data type без rewrite

Проверить binary-compatible conversions.

### 535. Изменить data type с USING

Контролировать conversion и invalid data.

### 536. Разделить constraint creation и validation

Минимизировать длительность blocking lock.

### 537. Перестроить large table

Сравнить shadow table, logical replication и maintenance window.

### 538. Исследовать view-based compatibility

Сохранить старый API schema через compatibility view.

### 539. Исследовать trigger-based migration

Синхронизировать old и new tables с учётом complexity.

### 540. Проверить rollback migration

Разделить reversible schema change и irreversible data transformation.

### 541. Создать preflight checks

Проверять disk space, locks, invalid data и replication lag.

### 542. Создать migration timeout policy

Использовать `lock_timeout` и `statement_timeout`.

### 543. Наблюдать migration progress

Использовать progress views и custom backfill metrics.

### 544. Создать migration dry run

Запускать copy production-like schema и data distribution.

### 545. Тестировать mixed application versions

Проверить backward compatibility rolling deployment.

### 546. Создать schema drift detection

Сравнивать expected migrations и actual database schema.

### 547. Создать migration audit

Фиксировать version, operator, duration и result.

### 548. Создать failed migration recovery

Документировать cleanup invalid indexes и partial backfills.

### 549. Создать production migration checklist

Проверять locks, WAL, storage, backups и rollback.

### 550. Создать zero-downtime migration scenario

Выполнить полную expand-backfill-switch-contract последовательность.

## 20. Partitioning

### 551. Исследовать declarative partitioning

Разобрать partitioned table и child partitions.

### 552. Создать range partitioning

Разделить time-series table по месяцам.

### 553. Создать list partitioning

Разделить data по region или category.

### 554. Создать hash partitioning

Распределить tenants между фиксированным числом partitions.

### 555. Создать multilevel partitioning

Комбинировать range и hash.

### 556. Исследовать partition key design

Выбрать key по pruning, retention и write distribution.

### 557. Исследовать partition constraints

Проверить автоматические bounds constraints.

### 558. Исследовать partition pruning

Проверить plan при constant predicate.

### 559. Исследовать runtime pruning

Проверить parameterized nested loop и prepared statement.

### 560. Исследовать default partition

Обработать rows вне существующих bounds.

### 561. Создать future partitions

Автоматизировать создание partitions заранее.

### 562. Реализовать partition retention

Удалять historical data через `DROP` или `DETACH PARTITION`.

### 563. Сравнить DELETE и DROP PARTITION

Измерить locks, WAL и duration.

### 564. Исследовать ATTACH PARTITION

Подключать preloaded table с validated constraint.

### 565. Исследовать DETACH PARTITION CONCURRENTLY

Минимизировать blocking при архивировании.

### 566. Исследовать indexes на partitioned tables

Создавать corresponding indexes на partitions.

### 567. Исследовать unique constraints partitioning

Понять требование включения partition key.

### 568. Исследовать foreign keys partitioning

Проверить supported directions и operational cost.

### 569. Исследовать partition-wise aggregate

Выполнять aggregation отдельно по partitions.

### 570. Исследовать partition-wise join

Использовать aligned partitioning.

### 571. Измерить planning overhead

Проверить большое количество partitions.

### 572. Исследовать partition metadata locks

Проверить DDL и concurrent queries.

### 573. Исследовать partitioned autovacuum

Настроить параметры для отдельных child tables.

### 574. Исследовать partitioned statistics

Проверить parent и child statistics.

### 575. Исследовать global-index absence

Разобрать ограничения uniqueness между partitions.

### 576. Реализовать tenant partitioning

Сравнить hash partitioning и shared table с composite indexes.

### 577. Исследовать skewed partitions

Проверить uneven data и hot partitions.

### 578. Реализовать partition rebalancing

Перераспределить hash buckets или tenants.

### 579. Создать partition maintenance job

Автоматизировать create, detach, archive и drop.

### 580. Документировать partitioning decision

Зафиксировать случаи, когда partitioning приносит пользу или усложняет систему.

## 21. Replication и High Availability

### 581. Исследовать physical replication

Разобрать WAL streaming и byte-identical standby.

### 582. Настроить primary и standby

Создать streaming replication environment.

### 583. Создать replication role

Ограничить privileges и pg_hba rules.

### 584. Исследовать replication slots

Предотвратить удаление нужного standby WAL.

### 585. Мониторить slot retention

Не допускать заполнения disk из-за inactive slot.

### 586. Исследовать asynchronous replication

Измерить replication lag и возможную потерю committed transactions.

### 587. Исследовать synchronous replication

Настроить ожидание standby confirmation.

### 588. Исследовать synchronous_standby_names

Проверить priority и quorum modes.

### 589. Исследовать hot standby

Выполнять read-only queries на replica.

### 590. Исследовать recovery conflicts

Проверить отмену standby queries из-за WAL replay.

### 591. Настроить hot_standby_feedback

Сравнить уменьшение conflicts и рост bloat primary.

### 592. Настроить max_standby_streaming_delay

Управлять балансом query duration и replay lag.

### 593. Исследовать replication lag metrics

Сравнить write, flush, replay LSN и time lag.

### 594. Выполнить planned switchover

Продвинуть standby и перенаправить clients.

### 595. Выполнить unplanned failover

Потерять primary и оценить data loss.

### 596. Исследовать split-brain risk

Зафиксировать необходимость fencing и consensus.

### 597. Исследовать timeline history

Понять новые timelines после promotion.

### 598. Исследовать pg_rewind

Вернуть старый primary в новый cluster.

### 599. Исследовать cascading replication

Подключить standby к другому standby.

### 600. Исследовать logical replication

Разобрать publications, subscriptions и logical decoding.

### 601. Создать publication

Публиковать выбранные tables и operations.

### 602. Создать subscription

Синхронизировать initial data и changes.

### 603. Исследовать replica identity

Настроить UPDATE и DELETE при отсутствии suitable primary key.

### 604. Исследовать logical replication conflicts

Обработать duplicate keys и schema mismatch.

### 605. Исследовать sequence replication gap

Зафиксировать, что sequence state не реплицируется как table data.

### 606. Исследовать logical replication DDL

Документировать необходимость отдельной schema synchronization.

### 607. Реализовать selective data replication

Реплицировать subset tables или rows согласно возможностям выбранной версии.

### 608. Исследовать major-version upgrade

Сравнить `pg_upgrade` и logical replication.

### 609. Создать HA failure scenarios

Проверить primary crash, network partition, lagging standby и slot failure.

### 610. Подготовить production readiness checklist

Зафиксировать schema, indexes, planner, transactions, vacuum, WAL, backups, replication, monitoring и recovery requirements.
