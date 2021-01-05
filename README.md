# defi

大家好，本次我们通过 ChainIDE 在 BSC 币安智能链上部署一个简单的 Defi 智能合约项目。<br>
本次项目中包含了 2 种基于 ERC20 的代币，我们暂时把这两种代币称之为 ChainToken 以及 RevenueToken（之后简称为 CT 和 RT），CT 是用于模拟用户自身持有的数字货币，而 RT 是用户质押 CT 之后所获得的利息。整个 Defi 项目的工作流程是由一个 Farm 合约执行，用户将自己所持有的数字货币质押进 Farm 合约，合约按照用户质押的数量等比生成 RT 作为利息返还给用户。<br>
<br>

### 项目中使用的工具 <br>

1.IDE BinanceIDE https://binanceide.com/project/welcome <br>
2.Metamask(连接至 BSC 币安智能链)
<br>
<br>

### 连接方法:<br>

2.1 打开 metamask 小狐狸并选择自定义 RPC 选项<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B14.png)<br>
<br>
2.2 输入内容如下:<br>
Network Name: BSC Testnet<br>
New RPC URL: https://data-seed-prebsc-1-s1.binance.org:8545/<br>
Chain ID:97<br>
Currency Symbol 和 Block Explorer URL 为选填项，可以不填<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B15.png)
<br>
<br>

## 操作流程<br>

1.点击 BinanceIDE 的首页中的 Defi Demo 案例<br>
（配图）<br>
<br> 2.在左侧的目录中我们已经准备好了上述的三份智能合约，其中 ChainToken 和 Revenue 是基于 ERC20 发行代币的智能合约，合约中声明了数字货币的名称，发行总量以及包含了验证、转账和第三方转账等方法。Farm 合约的代码实现了我们整体 defi 项目的运作逻辑，其中 stakeToken 方法是质押 CT 到此合约中，untakeTokens 是将质押的数字货币取出，issueToken 则是根据质押的 CT 生成 RT 利息。<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E6%95%99%E7%A8%8B%E5%9B%BE%E7%89%874.png)<br>
<br> 3.下面我们将这三份合约部署到币安智能链上，首先在右上角选择编译器，0.5.x 的任意版本<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B5.png)
<br> 4.点击 compile 之后可以在控制台看见编译结果<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B6.png)<br>
<br> 5.部署合约（设置 value 以及 gwei），这一步需要将三份编译好的合约分别部署，在 Compiled Contracts 当中首先部署 ChainToken 以及 RevenueToken，最后在部署 Farm 合约时传入前两个合约的地址(前两个合约的地址可以在 output 控制台中查看，例如"contractAddress":"0x79a377715E31D5F9eE736f8087aC0Ca230F8C48e")<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B7.png)<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B8.png)
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B9.png)
<br> 6.在所有合约部署完成之后，由 Farm 合约实现数字货币的质押功能（stakeToken），这个方法的本质是调用了 chainToken 合约当中 TransferFrom 函数，将用户账户中的 chaintoken 转账到 Farm 合约当中，在此之前我们需要 approve 账户中拥有足够的数字货币。
<br>
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B10.jpg)
<br>
<br>
7.Approve 完成之后进行质押操作（填入想要质押的数量）
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B11.png)
<br> 8.接下来把 RevenueToken 转移到 Farm 合约当中用于生成分红,参数传入 Farm 合约地址以及需要转移的数字货币数量
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B11.png)
<br> 9.最后一步调用 Farm 合约中的 issueToken 函数为已经质押的用户生成分红
<br>
![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E5%9B%BE%E7%89%87%E6%95%99%E7%A8%8B13.png)
<br>
