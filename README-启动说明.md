# Bridgend Antiques 当前本地版本

这是给项目使用者的 LOCAL REVIEW SOURCE PACKAGE，包含当前8767版本的完整应用源码、样式、图片素材和282件商品的公开来源数据。保留最新字体、紧凑布局、双图店铺轮播、商品目录、咨询与管理后台。

## 启动
需要Python3.12及首次安装依赖时联网。在解压目录打开终端执行：

```sh
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.lock
.venv/bin/python tools/import_source.py
.venv/bin/python run.py
```

打开 http://127.0.0.1:8767/ 。若该端口已有原预览运行，可用 `BRIDGEND_PORT=8769 .venv/bin/python run.py`，再打开8769。
Windows请用Python3.12创建环境，并将命令中的`.venv/bin/python`替换为`.venv\Scripts\python.exe`。

首次访问 `/admin/setup` 自己创建管理员账号。没有预设密码。咨询写入本地后台收件箱，不会发送外部邮件。运行后数据库与会话密钥创建于data/runtime；本包不含原运行数据库、账号、密钥、咨询记录或虚拟环境。

## 包含内容
- 65件在售、217件售出，28个分类；搜索、详情、分类和售出档案。
- 营业时间来源说明、服务、支付说明、评价来源入口和联系方式。
- 商品/分类管理，图片上传与撤回，咨询保存/处理，导出与备份恢复。
- 完整店内双图轮播，最新无衬线字体与紧凑排版。

## 当前已知状态
1,438张商品照片仅记录来源，尚未取得本次本地使用确认，所以包内不含这些照片。页面与当前预览保持一致；没有用替代图冒充真实商品。已用店铺照及概念视觉的来源见ASSET_PROVENANCE.json；本次给用户本地查看的打包不等于客户正式素材转让授权。

这是Python动态应用，不能直接作为纯静态Cloudflare Pages上传包。公网部署、域名/HTTPS、生产邮件配置和客户最终交付未包含在本次操作中，也没有实际执行。没有因此删减当前可见页面。

## 备份与恢复

```sh
.venv/bin/python tools/backup.py backup /绝对路径/data/runtime /绝对路径/新备份目录
.venv/bin/python tools/backup.py restore /绝对路径/新备份目录 /绝对路径/新恢复目录
```

目标目录须不存在。恢复会撤销旧登录会话。备份含业务数据与密码哈希，应妥善保管。

MANIFEST-SHA256.json记录包内文件校验值；ZIP旁的.sha256文件验证整个压缩包。
