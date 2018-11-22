### 第一步：下载gitbook编辑工具

[MAC版本下载地址（点击下载）](https://legacy.gitbook.com/editor)

### 第二步：注册github账户

[注册地址（点击跳转注册链接）](https://github.com/)  
完成注册，将github账户用户名发送给海峰，他会将你的github账户添加到电子书仓储，这个账号将获得提交权限。

### 第三步：同步电子书仓储

* 运行gitbook编辑工具

![](/assets/1_copy.png)

* 点击\[Do that later\]进入电子书列表

![](/assets/2_copy.png)

* 点击\[New Book\]添加本地书本，进入电子书编辑![](/assets/4_copy.png)
* 关联github仓储  
  刚才新建的电子书其实是存储在本地的，需要与github仓储上的电子书进行关联，需要用到上步注册的github账号

点击右上角【Async】按钮
![](/assets/async.png)
提示输入github仓储地址，输入：https://github.com/worktile/wt-doc.git
![](/assets/github_repository.png)
点击【Async】确认会提示输入github账户密码（因为是公开仓储，此时已经把仓储上的电子书文档同步到本地）
![](/assets/github_account.png)
输入完成后点击【Async】完成同步，这个步骤完成的前提需要你的账号加入了这个仓储并且获取提交权限。
### 编辑文档
完成以上步骤，就可以通过gitbook编辑电子书，每次编辑完后点击【Save】保存然后点击【Async】同步到github仓储。