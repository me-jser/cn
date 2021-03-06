# 创建容器镜像

**前提条件**

 - 注册京东云账号并激活、认证账号，可分别访问[注册京东云](https://accounts.jdcloud.com/p/regPage?source=jdcloud%26ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3d//www.jdcloud.com/)、[登录京东云](https://console.jdcloud.com/overview)、[实名认证](https://uc.jdcloud.com/account/verify)进行操作；
 - 若您需要创建按配置计费实例，您需要保证您的余额不低于50元，若当前余额不足请进行[充值](https://uc.jdcloud.com/cost/capital/recharge)；
 - 关于地域及可用区的信息，请参考[地域及可用区](https://docs.jdcloud.com/cn/virtual-machines/regions-and-availabilityzones)

**操作步骤**

**一、创建注册表**

 1. 打开控制台，选择[弹性计算-容器镜像仓库-注册表](https://cns-console.jdcloud.com/host/containerregistry/list)，选择创建按钮  
    ![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Container-Registry/创建注册表页面.png)  
 2. 选择地域，支持华北-北京、华东-上海、华南-广州  
 3. 填写名称，名称全局唯一且不支持修改；长度大于3个字符，且不能超过32字符；以小写字母数字开始和结尾，支持使用小写字母、数字、中划线(-)  
 4. 描述非必填项，描述不能超过256个字符，不支持修改  
 5. 注册表URI自动生成，规则为：注册表名称-地域缩写.jcr.service.jdcloud.com  
 6. 点击确定  

**二、创建镜像仓库**

 1. 打开[弹性计算-容器镜像仓库-镜像仓库](https://cns-console.jdcloud.com/host/containerrepository/list)，选择创建按钮  
 ![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Container-Registry/新建镜像仓库.png)  
 2. 选择地域，支持华北-北京、华东-上海、华南-广州  
 3. 选择所属注册表  
 4. 填写名称，名称大于3个字符且不超过255个字符，同一注册表下名称唯一且不可修改；支持使用多级命名空间，命名空间以/分隔，各级命名空间不可为空，以小写字母数字开始和结尾，支持使用小写字母、数字、中划线(-)，下划线（ _ ）  
 5. 描述非必填项，描述不能超过256个字符，不支持修改  
 6. 镜像仓库URI自动生成，注册表URI/镜像仓库名称  
 7. 点击确定  

**三、获取临时令牌**

 1. 打开[弹性计算-容器镜像仓库-注册表](https://cns-console.jdcloud.com/host/containerregistry/list)，点击获取临时令牌，您可以使用临时令牌完成Docker客户端的授权认证；一个小时内最多申请5个临时令牌  
 ![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Container-Registry/获取临时令牌.png)   
 2. 设置临时令牌的有效期：默认为12小时；范围为1~24小时的整数。点击确定  
 3. 弹窗“下载临时令牌”，单击“下载.xlsx文件”，将临时令牌下载到本地，文件名“registry名称-token.xlsx”。或者复制保存信息。  
![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Container-Registry/下载临时令牌.png)  
**注：关闭后，无法再次获取临时令牌的Docker客户端登录命令**

**四、上传、下载镜像**

 1. 安装最新版的[京东云CLI](https://docs.jdcloud.com/cn/cli/introduction)和[Docker](https://docs.docker.com/install/)
 
 2. 例：注册表为myregistry，镜像仓库为myrepo，镜像版本号为latest，地域选择华北-北京为cn-north-1。用户可根据具体情况修改。
 
    使用京东云CLI获取登录指定注册表的临时令牌或在控制台获取临时令牌：  
    `jdc cr get-authorization-token --region-id cn-north-1 --registry-name myregistry`
 3. 使用临时令牌，登录到京东云的注册表；如您使用京东云CLI获取临时令牌，请输入返回的Docker客户端登录命令：  
    `docker login -u jdcloud -p ********* myregistry-cn-north-1.jcr.service.jdcloud.com `
 4. 将镜像推送到京东云镜像仓库，本地镜像例为ubuntu:latest  
    标记待推送到京东云镜像仓库中的本地镜像：  
    `
    docker tag ubuntu:latest myregistry-cn-north-1.jcr.service.jdcloud.com/myrepo:latest
    `  
    将已标记的镜像推送到京东云镜像仓库：  
    `
    docker push myregistry-cn-north-1.jcr.service.jdcloud.com/myrepo:latest
    `
 5. 从京东云镜像仓库拉取镜像：  
    `
    docker pull myregistry-cn-north-1.jcr.service.jdcloud.com/myrepo:latest
    `
