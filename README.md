# captain
Easy to use distributed event bus similar to Kafka

# Features (work in progress)

1. 开箱即用，易于配置，确保数据不丢失
Chukcha 提供简洁的默认配置，用户无需复杂设置即可确保数据的持久性和可靠性。

2. 分布式设计，默认支持异步复制
系统内置分布式架构，数据在多个节点之间进行异步复制，提升系统的高可用性和扩展性。

3. 明确的数据读取确认机制
读者在成功读取数据后需显式确认，确保数据被可靠处理，防止数据丢失或重复处理。

# Design (work in progress)

1. 数据分割与存储
数据被拆分成多个块（chunks）并作为文件存储在磁盘上。这些文件会被复制到不同的节点，以确保数据的高可用性和容错性。

2. 读者确认与偏移管理
读者在读取数据后需显式确认已读取的数据。读者负责从适当的偏移量开始读取数据块，确保数据的有序和完整读取。

# TODOs:

1. 最大消息大小限制为 1 MiB
为了确保系统能够从磁盘中以 1 MiB 的块读取数据，限制单条消息的最大大小为 1 MiB。超过此限制的消息将无法被正确处理。

2. 编写更细粒度的磁盘格式测试
为了确保数据在磁盘上的存储格式正确且可靠，需编写更细致的测试用例，覆盖各种边界条件和潜在的故障情况。
