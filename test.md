### 背景
* 1.目前从gitlab拉取python项目代码后，需要手动执行pip install命令一个个安装依赖的第三方模块，对于不熟悉项目的成员，存在容易漏装或安装错版本等问题。

* 2.同时后续框架扩展，用到其他第三方模块或更新版本，readme.md说明文档也要手动更新，存在文档不能及时更新的问题。
![](https://tva1.sinaimg.cn/large/008eGmZEgy1gp7h6c5klqj31fa0p278z.jpg)
* 3.基于以上两个问题，建议将项目所有依赖的第三方模块版本信息都导出到一个requirements.txt清单文件中，后续只需要执行一个命令即可批量安装所需的所有第三方模块。
    * 同时如果使用pycharm作为代码编辑器，pycharm也会自动识别requirements.txt文件，自动下载安装。且在pycharm安装requirements插件后，后续第三方模块有更新，pycharm也会提示模块的最新版本，点击upgrade即可更新到对应的版本
![](https://gblobscdn.gitbook.com/assets%2F-MVAn263L1T9kc8mRyfj%2F-MXP83FtUkWhtfynOqux%2F-MXPIYLXN2h8OxaNAGtH%2F%E6%88%AA%E5%B1%8F2021-04-04%20%E4%B8%8A%E5%8D%888.35.00.png?alt=media&token=88778e06-6740-46a2-9a77-71af1be3c38f)
### 操作步骤
* 1.在已安装所有依赖的第三方模块前提下，在项目根目录下，执行命令
```bash
# 每次新增或更新第三方，可使用以下命令导出清单文件
pip freeze > requirements.txt
```
* 2.在项目根目录下，执行命令批量安装第三方模块
```bash
# 安装所需的第三方模块
pip install -r requirements.txt
```
* 3.可在pycharm的【File】-【Settings】-【Plugins】中搜索requirements，选择安装requirements文件管理插件。
![](https://gblobscdn.gitbook.com/assets%2F-MVAn263L1T9kc8mRyfj%2F-MXP83FtUkWhtfynOqux%2F-MXPK-JP8P0-_X0oyYVx%2F%E6%88%AA%E5%B1%8F2021-04-04%20%E4%B8%8A%E5%8D%888.38.53.png?alt=media&token=254658fe-889e-416a-9391-45d92ba85a3f)
