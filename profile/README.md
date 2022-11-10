# Black Mirror组

绿色电力交易平台优化

## 简介
1. 定位：绿色电力交易平台（用电企业直接对接光伏、风电等发电企业，以充分市场化的方式购买绿色电能，并获得相应的绿色电力消费认证）
2. 主要创新点 
  - 绿色交易全记录：无需通过绿证等方式调控，政府直接根据平台记录发放补贴
  - 竞价交易：以挂牌出价替代以往的协商方式，提升交易效率
  - 跨省跨境点对点交易：过去跨省需要两地电网公司代理，可以绕开
  - 政府监管更便利：所有挂牌需求、供应和交易集成看板，供政府监测调度

## 功能

1. 基本功能：
    1. 注册、登录、查看个人信息【售电企业、购电企业、政府】
2. 购电企业：
    1. “电力”商品浏览【售电企业挂牌表、购物车】
进入“优质电力”页面，浏览商品，可以点击进入商品详情页面查看详细信息。
    2. 购物车【售电企业挂牌表、购物车】
        1. 加入购物车：在商品详情页面可以将商品加入购物车。
        2. 删除购物车商品：在购物车页面，选中欲删除的商品可以删除。
        3. 购物车结算：可以在购物车选中商品进行结算，跳转“确定订单”页面。
            1. 点击确定，进行数字签名确认；
            2. 点击取消，跳出弹窗“确认是否取消”；
                1. 点击确认取消，跳转回商品页面；
                2. 点击不取消，弹窗退出，返回“确定订单”页面。
    3. 下单结算：【购物车、出价表、交易信息表】
进入商品页面或商品详情页面，点击“立即下单”，跳转“确定订单”页面；
    4. 订单管理【交易信息表】
进入订单管理页面；
        1. 查看订单：选择想要查看的订单，跳转订单详情页面，可以查看交易信息，点击挂牌/出价，也可以进一步查看具体挂牌情况和出价情况。
        2. 完成订单：
        3. 取消订单
3. 售电企业：售电企业登录，进入主页面
    1. “电力”商品上架：【售电企业挂牌表、发电项目、发电流程溯源表】
进入商品上架页面，填入挂牌信息，发电项目和发电流程溯源表（可选），点击提交，弹出弹窗，商品上架成功。
    2. 商品管理【售电企业挂牌表、发电项目、发电流程溯源表】
进入商品管理页面，选择想要查看的商品，跳转商品信息页面。
        1. 查看商品
        2. 修改商品：（含撤销商品：修改挂牌表中的挂牌状态为“无效”）
修改对应的数据项，点击“提交”，弹出弹窗提示修改项及内容；
            1. 点击“已确认无误，提交”，提交成功。
            2. 点击“返回修改页面”，回到修改页面。
    3. 订单管理【交易信息表】
        1. 查看订单
    4. 购电企业出价单浏览【购电企业出价表】
进入电力需求页面（本页面显示出价表中挂牌id为空的出价），选择想要查看的需求，跳转需求详情页面。
    5. 对购电企业出价挂牌（报价/竞价）
     与购电企业下单流程类似
     ![image](https://user-images.githubusercontent.com/56627153/197407449-e13d0f63-dcbf-4786-8280-4c6e01398cea.png)
     ![image](https://user-images.githubusercontent.com/56627153/197407461-fa0792f3-2028-4aac-b71b-035944665282.png)
4. 政府：对数据进行可视化查看
    1. 按购电/输电企业所属省域、能源类型、时间切片查看交易量/交易量份额/成交价格（折线图、柱状图、饼图）
    2. 按时间、能源类型查看省间电力输送情况（地图上显示）

## 数据字典与数据结构
1. 数据字典
  

| **编号** | **数据项名** | **含义说明**       | **数据类型** | **长度** | **备注**                                            |
| -------- | ------------ | ------------------ | ------------ | -------- | --------------------------------------------------- |
| 1        | sno          | 售电企业编号       | Integer      | 4        | 非空，售电企业主码                                  |
| 2        | sname        | 售电企业名称       | Char         | 30       | 非空                                                |
| 3        | saddress     | 售电企业区块链地址 | Char         | 30       | 非空                                                |
| 4        | stime        | 认证绿色企业时间   | Date         | 3        | 非空                                                |
| 5        | scertificate | 绿证持有数量       | Integer      | 4        | 非空                                                |
| 6        | pno          | 发电项目编号       | Integer      | 4        | 非空，发电企业主码                                  |
| 7        | pname        | 发电项目名称       | Char         | 30       | 非空                                                |
| 8        | pamount      | 发电量（千瓦时）   | Float        | 4        | 非空                                                |
| 9        | ptype        | 发电类型           | Tinyint      | 1        | 非空，0、1、2分别代表风电、光电、水电               |
| 10       | bno          | 购电企业编号       | Integer      | 4        | 非空，购电企业主码                                  |
| 11       | bname        | 购电企业名称       | Char         | 30       | 非空                                                |
| 12       | baddress     | 购电企业区块链地址 | Char         | 30       | 非空                                                |
| 13       | btype        | 购电企业企业类型   | Tinyint      | 1        | 非空，0、1、2分别代表农业、制造业、服务业           |
| 14       | mno          | 输电企业编号       | Integer      | 4        | 非空，输电企业主码                                  |
| 15       | mname        | 输电企业名称       | Char         | 30       | 非空                                                |
| 16       | gno          | 政府用户编号       | Integer      | 4        | 非空，地方政府主码                                  |
| 17       | gname        | 政府用户名称       | Char         | 30       | 非空                                                |
| 18       | tno          | 交易编号           | Integer      | 4        | 非空，购电企业主码                                  |
| 19       | tstatus      | 交易状态           | Tinyint      | 1        | 非空，0、1、2分别代表交易成功、交易进行中、交易失败 |
| 20       | tamount      | 交易电量           | Float        | 4        | 非空                                                |
| 21       | tprice       | 购电价格           | Float        | 4        | 非空                                                |
| 22       | tperiod      | 供电周期           | Float        | 4        | 非空                                                |
| 23       | tdate        | 交易时间           | Date         | 3        | 非空                                                |
| 24       | tcredit      | 绿色积分           | Float        | 4        | 非空                                                |
| 25       | lno          | 挂牌编号           | Integer      | 4        | 非空，出价表主码                                    |
| 26       | lstatus      | 挂牌状态           | Tinyint      | 1        | 非空，0、1分别代表挂牌、未挂牌                      |
| 27       | lamount      | 库存电量           | Float        | 4        | 非空                                                |
| 28       | lprice       | 挂牌绿色交易价格   | Float        | 4        | 非空                                                |
| 29       | lstart       | 挂牌发起时间       | Date         | 3        | 非空                                                |
| 30       | lend         | 挂牌结算时间       | Date         | 3        | 非空                                                |
| 31       | cartno       | 购物车项目编号     | Integer      | 4        | 非空，出价表主码                                    |
| 32       | cartdate     | 加入购物车时间     | Date         | 3        | 非空                                                |

2. 数据结构

| **编号** | **数据结构**                | **含义说明**   | **组成**                                                     |
| -------- | --------------------------- | -------------- | ------------------------------------------------------------ |
| 1        | Seller User Information     | 售电企业信息表 | sno  sname  saddress  stime  scertificate *pno gno*          |
| 2        | Buyer User Information      | 购电企业信息表 | bno  bname  baddress  btype  *gno*                           |
| 3        | Middle User Information     | 输电企业信息表 | mno  mname  gno                                              |
| 4        | Government User Information | 政府信息表     | gno  gname                                                   |
| 5        | Production Information      | 发电项目信息表 | pno  pname  pamount  ptype                                   |
| 6        | Transaction Information     | 交易信息表     | tno  tstatus  tamount  tprice  tperiod  tdate  tcredit  *mno  bno  pno  sno* |
| 7        | Listing Information         | 出价表         | lno  lstatus  lamount  lprice  lstart  lend  *sno mno pno*   |
| 8        | Bidding Information         | 竞价表         | *bno*  *pno*  *lno*  *sno*                                   |
| 9        | Shopping Cart Information   | 购物车信息表   | cartno cartdate bno lno                                      |

## 系统架构

![01 系统架构设计](https://user-images.githubusercontent.com/45125710/201157245-dd0ce04d-64b5-44e9-a395-cb96b3af8ffa.svg)

## 技术栈

1. 前端
   1. React.js
   2. Ant Design
2. 后端
   1. Python
   2. Flask
   3. SQLite
3. 区块链网络
   1. 平台：FISCO-BCOS
   2. 预编译合约
      * C++
      * Rust FFI
      * [mcl](https://github.com/herumi/mcl)
      * [winterfell](https://github.com/novifinancial/winterfell)
   3. 合约
      * Solidity
   4. 存储
      * IPFS

## 流程


## 部署流程

1. 部署区块链网络
   1. 从GitHub下载FISCO-BCOS部署脚本

       ```bash
       sudo apt install -y openssl
       cd ~
       mkdir fisco && cd fisco
       wget https://raw.githubusercontent.com/FISCO-BCOS/FISCO-BCOS/master-2.0/tools/build_chain.sh
       chmod +x ./build_chain.sh
       ./build_chain.sh -l 127.0.0.1:4 -p 30300,20200,8545
       ```

   2. 从GitHub下载Python SDK

       ```bash
       cd ~
       git clone https://github.com/FISCO-BCOS/python-sdk
       ```

   3. 将节点的密钥复制到Python SDK中

       ```bash
       cp nodes/127.0.0.1/sdk/* python-sdk/bin
       ```

   4. 下载用于编译合约的Solidity

       ```bash
       wget https://github.com/ethereum/solidity/releases/download/v0.4.24/solc-static-linux -O python-sdk/solc
       sudo chmod +x python-sdk/solc
       ```

   5. 配置Python SDK Console，需要修改`python-sdk/client_config.py`中的以下部分：
      * `account_keyfile`与`account_password`：需要提前执行`python3 ./console2.py newaccount`，然后`bin/accounts`目录下会出现对应的`.keystore`文件。
      * `solc_path`：对应下载得到的solc binary（即`solc`）

2. 前端
    1. 从GitHub下载源代码

       ```bash
       git clone https://github.com/FinTechathon-Chain/frontend.git
       ```

    2. 进入`frontend-implementation`目录并安装依赖

       ```bash
       cd frontend-implementation
       npm install .
       ```

    3. 启动

       ```bash
       npm run build
       ```
