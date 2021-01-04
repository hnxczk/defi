# defi
  大家好，本次我们通过ChainIDE在BSC币安智能链上部署一个简单的Defi智能合约项目。<br>
  本次项目中包含了2种基于ERC20的代币，我们暂时把这两种代币称之为ChainToken以及RevenueToken（之后简称为CT和RT），CT是用于模拟用户自身持有的数字货币，而RT是用户质押CT之后所获得的利息。整个Defi项目的工作流程是由一个Farm合约执行，用户将自己所持有的数字货币质押进Farm合约，合约按照用户质押的数量等比生成RT作为利息返还给用户。<br>
  <br>
  <br>
  
  项目中使用的工具 <br>
1.IDE  BinanceIDE  https://binanceide.com/project/welcome <br>
2.Metamask(连接至BSC币安智能链)
<br>
<br>
  连接方法:<br>
  2.1 打开metamask小狐狸并选择自定义RPC选项<br>
  ![Image text](https://github.com/wkq1991zmc/defi/blob/master/%E6%95%99%E7%A8%8B%E5%9B%BE%E7%89%871.png)<br>
  2.2 输入内容如下:<br>
    Network Name: BSC Testnet<br>
    New RPC URL: https://data-seed-prebsc-1-s1.binance.org:8545/<br>
    Chain ID:97<br>
    Currency Symbol和Block Explorer URL为选填项，可以不填
  
<br>
<br>


  

