介绍Map链验证人选举以及整个过程中验证人及投票的管理。

## 更新活动验证器集

在处理交易和 Epoch 奖励之后，通过在每个 epoch 的最后一个区块中运行选举来更新活动验证器集。

## 选举验证器

验证者必须至少拥有总票数的 0.001 比例才能考虑参加选举。所以验证者不能没有选票。
这样做的好处是避免烧毁 MAP 并将投票人数限制在1000人以内。
可选择的活跃验证器数量有最小目标 (1) 和最大上限 (100)。如果未达到最低目标，则选举将中止，并且不会对该 epoch 的验证器集进行任何更改。
示例：现在链上有四个验证者，他们是：

- 0x5d643dfb9ae372ce4fdbc80890156e2cd8290846
- 0xa53516d49a72019692ac69cb42641942597654f6
- 0x6acdc02223100189d82a958d888f54fa27d60e8a
- 0xea9efaa232a4567eac21c8c096f8bff84595a244

如果由于某些原因我们不选举验证器（有效验证器数量小于1），我们将继续使用上述验证器。如果我们选择最新的一组验证器（这意味着新验证器的数量大于
1 且小于 100），我们将用新验证器替换上述验证器。

## 执行


[Election](https://github.com/mapprotocol/atlas-contracts/blob/main/contracts/governance/Election.sol) 合约管理锁定 MAPO 投票和纪元奖励并运行验证者选举。