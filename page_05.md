&emsp;&emsp;类似于在区块链中，每一个新的块都要确认之前所有的块（以及其中的交易），在DAG中，每一个新的子单元都要确认其父母单元，父母单元的所有父母单元，父母单元的父母单元的父母单元等。如果一个人试图编辑一个存储单元，他就会改变了这个单元的哈希值。不可避免地，这将会破坏所有引用这个单元哈希值的子单元，因为子单元的哈希值依赖于父单元的哈希值。因此，不可能在未与其他子单元达成合作或窃取到子单元的私钥的情况下，修改这个单元。子单元也不可能再未合作的情况下修改他们的单元（原单元的孙子单元），等等。一旦一个单元广播到网络中，其他用户就开始在这个单元上开始构建他们自己的单元（引用这个单元作为父单元），修改这个单元所需的二次修改难度就如同雪球一样增长。这就是我们为什么称之为字节雪球(Byteball)，我们的雪花就是数据中的字节。

&emsp;&emsp;与“发布一个块是一个稀缺的事件，并且只有特权用户（矿工）才可以在实际中有这种行为”的区块链不同，在Byteball中，存储单元发布后，立即开始积累确认，并且确认可以来自任何人在任何时候发布的另一个新单元。这里不区分普通用户和矿工两套系统。取而代之的是，用户互相帮助：通过添加一个新的单元，发布者也确认了之前的所有单元。

&emsp;&emsp;与尝试修改过去的交易需要大量计算工作的比特币不同，尝试修改直接雪球过去的记录，需要大量且越来越多的其他用户协助配合，其中大部分是匿名的陌生人。因此过去记录的不变性是基于与如此大量的陌生人协助的复杂性相关，这些人难以达成一致，对合作没有兴趣，并且每个人都可以否决修改。

&emsp;&emsp;通过引用一个父母单元，一个单元包含父单元。但它不包括父母单元的全部内容；相反，它的内容取决于父单元的哈希值。同样，单元间接依赖于并因此包含祖父单元，曾祖单元等，并且每个单元最终包含创世单元。

&emsp;&emsp;协议有个规则就是单元不能引用冗余的父母单元 —— 那就是这些父母单元不能是一个父单元包含另一个单元。例如，如果单元B引用单元A，则单元C不能同时引用单元A和B。A已经以某种方式包含在B中了。如果此规则去除，将不能向DAG中添加任何新的有效连通性的链接。

### 3、天然货币：Bytes
接下来，为了防止无用的垃圾信息进入这个去中心化的数据库，我们需要引入一些摩擦力。入口的屏障应该大致反映出用户的存储效用和网络的存储成本。对于这两者而言最简单的方法是测量存储单元的大小。因此，为了把你的数据存储到这个全球的去中心化的数据库中，你需要支付一定费用的货币，这种系统内部的货币叫 *字节币* ，您支付的金额与你所需存储的数据大小相等（包括所有头部和签名信息等）。就如同首次推出时等于一磅银的英镑，货币的名称直接反映了它的价值。