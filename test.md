### 背景
* 1.目前从gitlab拉取python项目代码后，需要手动执行pip install命令一个个安装依赖的第三方包，对于不熟悉项目的成员，存在容易漏装或安装错版本等问题。

* 2.同时后续框架扩展，用到其他第三方包或更新版本，readme.md说明文档也要手动更新，存在文档不能及时更新的问题。
![](https://tva1.sinaimg.cn/large/008eGmZEgy1gp7h6c5klqj31fa0p278z.jpg)
* 3.1.基于以上两个问题，
    1. 建议1:将项目所有依赖的第三方模块版本信息都导出到一个requirements.txt清单文件中，后续只需要执行一个命令即可批量安装所需的所有第三方模块。
        * 同时如果使用pycharm作为代码编辑器，pycharm也会自动识别requirements.txt文件，自动下载安装。且在pycharm安装requirements插件后，后续第三方模块有更新，pycharm也会提示模块的最新版本，点击upgrade即可更新到对应的版本
        ![](https://gblobscdn.gitbook.com/assets%2F-MVAn263L1T9kc8mRyfj%2F-MXP83FtUkWhtfynOqux%2F-MXPIYLXN2h8OxaNAGtH%2F%E6%88%AA%E5%B1%8F2021-04-04%20%E4%B8%8A%E5%8D%888.35.00.png?alt=media&token=88778e06-6740-46a2-9a77-71af1be3c38f)
        
    2. 建议2:给每个项目单独配置虚拟环境。
        * what： 
            * virtualenv就相当于是把python解释器、pip包安装工具和第三方包都统一放在一个目录下，运行项目的时候，把python解释器和包搜索路径配置为虚拟环境的目录即可。
            ![](https://tva1.sinaimg.cn/large/008eGmZEgy1gp8obkvr2cj306m0eq0t5.jpg)
            ![](https://tva1.sinaimg.cn/large/008eGmZEgy1gp8ohk1ppjj304y0d940c.jpg)
        * why：
            * 在相同操作系统的不同主机之间，可复用python运行环境，激活并指定使用的虚拟环境后，就可以直接使用别人安装好的第三方包。
        * 缺点：
            * Windows和Linux环境中生成的虚拟环境有所差别，不能复用。从开发环境部署到测试环境的时候，需要再创建虚拟环境。
            * 增加了项目代码的总体积，上传和下载代码时增加耗时。
### 操作步骤
#### 导出依赖清单
* 1.在已安装所有依赖的第三方模块前提下，在项目根目录下，执行命令
```bash
# 每次新增或更新第三方，可使用以下命令导出清单文件
pip freeze > requirements.txt
```
#### 批量安装第三方包
* 1.在项目根目录下，执行命令批量安装第三方模块
```bash
pip install -r requirements.txt
```
#### pycharm的requirements插件
* 3.可在pycharm的【File】-【Settings】-【Plugins】中搜索requirements，选择安装requirements文件管理插件。
![](https://gblobscdn.gitbook.com/assets%2F-MVAn263L1T9kc8mRyfj%2F-MXP83FtUkWhtfynOqux%2F-MXPK-JP8P0-_X0oyYVx%2F%E6%88%AA%E5%B1%8F2021-04-04%20%E4%B8%8A%E5%8D%888.38.53.png?alt=media&token=254658fe-889e-416a-9391-45d92ba85a3f)
#### 配置虚拟环境
* 以Windows为例，
```bash
# 安装virtualenv
pip install virtualenv
# 使用virtualenv创建虚拟环境
virtualenv autotest_env
# 执行虚拟环境中的activate脚本，激活虚拟环境
autotest_env\Scripts\activate.bat
# 使用虚拟环境下的pip来批量安装第三方包
autotest_env\Scripts\pip install -r requirements.txt
```
* Linux也类似的配置，只是python解释器和pip等工具在bin目录中
