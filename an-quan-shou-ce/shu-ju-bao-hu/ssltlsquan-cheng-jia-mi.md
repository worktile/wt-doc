#### 1.4 SSL/TLS全程加密
##### Worktile数据传输过程中全程使用SSL/TLS（Secure Sockets Layer，详情请参考RFC5246及RFC6176），在不采用SSL/TLS前数据存在传输存在以下风险：  

* 1）    窃听风险（eavesdropping）：第三方可以获知通信内容
* 2）    篡改风险（tampering）：第三方可以修改通信内容
* 3）    冒充风险（pretending）：第三方可以冒充他人身份参与通信

##### 而采用SSL/TLS后，这些风险都可以规避：
* 1）    所有信息都是加密传播，第三方无法窃听
* 2）    具有校验机制，一旦被篡改，通信双方会立刻发现
* 3）    配备身份证书，防止身份被冒充

##### Worktile中SSL/TLS证书如下：

# ![](/assets/02.jpg)

##### Worktile SSL证书通过权威评测机构的证书测试，QUALYS SSL LABS的A级认证。

# ![](/assets/03.jpg)



