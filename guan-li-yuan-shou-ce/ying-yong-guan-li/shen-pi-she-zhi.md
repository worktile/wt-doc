### 3.7.1 基本设置

* 设置审批应用的可见范围。

#### 3.7.2 自定义审批表单

1) 创建审批表单

* 点击【创建审批表单】，你可以选择模板，然后在模板的基础上修改完成新表单创建，也可以直接进入Worktile审批表单设计器自行配置审批表单。

# ![](/assets/3.7.2自定义审批表单.png)

2) 修改表单属性

* 对表单的名称、描述、图标进行修改。

# ![](/assets/3.7.2修改表单属性.png)


3) 选择控件

* 你可以从左侧【可选控件】中选择需要的控件拖拽移动到表单内。可选控件主要包括文本、日期、数字等常用表单信息。

# ![](/assets/3.7.2选择控件.png)

4) 修改控件属性

* 在右侧【控件属性】对选中的控件修改其标题、提示文字等信息。

# ![](/assets/3.7.4修改控件属性.png)

5) 完成配置

* 点击【保存并启用】该表单将出现在审批模板列表中，并显示为启用状态，点击【保存】该表单也会显示在审批模板列表中，但显示为“禁用”状态。

# ![](/assets/3.7.5完成设置保存.png)

* 表单启用后，该表单会在前台主页的审批应用中显示在【提交审批】中，成员可以选择该表单并提交

# ![](/assets/3.7.5.2发起审批.png)

#### 3.7.3表单管理

# ![](/assets/3.7.6表单管理.png)

* 编辑按钮：对已经添加的审批进行二次编辑，可自定义审批流程是否允许申请人或审批人修改审批内容。

# ![](/assets/3.7.5编辑按钮.png)


• **预览按钮**：对表单样式进行预览。

•** 删除按钮**：删除审批表单，删除的表单将不可恢复。

• **上下移动**：调整审批表单排序。

• **禁用按钮**：开启／禁用该表单。禁用后，那么该表单不会出现在前台主页的审批应用的【提交审批】的表单列表中。

#### 3.7.4 设置审批流程

* 完成表单配置之后，管理员可以根据企业的工作场景，配置相应的审批流程。

# ![](/assets/3.7.4 设置审批人.png)
* 点击【审批人】，进入审批人和审批流程设置。

# ![](/assets/3.7.4 设置审批流程.png)

* 有三种审批流程可以选择，分别是：

1) **自由流程**：企业成员可自行添加审批人。

2) **固定流程**：企业成员需按照规定好的审批人流程进行审批；比如企业固定报销流程为“张三—李四”，设定固定流程后，企业成员填写审批单时，审批人已默认设置为“张三—李四”，且成员自己不能修改；

3) **分条件设置流程**：当表单包含以下类型字段时才可以使用分条件审批：【数字字段、【下拉选项】；申请人提交的表单会根据相应字段进入对应的审批流程。根据申请人提出的表单进入对应的审批流程。点击【设置审批条件】进行设置。例如根据招聘人数，设置区间。点击【确定】然后根据不同的条件设置对应的审批人。

# ![](/assets/3.7.6设置审批条件.png)

# ![](/assets/3.7.6添加审批人.png)

#### 3.7.5角色审批

* 角色审批可以帮助企业规范审批流程，提高流程处理速度，减轻管理员后台配置的负担。预置好审批角色后，工作流程可在审批流程中固定下来，人员离职变动等，流程也无需再单独修改。同事，因为审批流程已设置好，并且清晰直观，即使新人不熟悉流程，也可直接提交审批。

# ![](/assets/3.7.6审批角色.png)

> _Tips：
1) 若审批环节中某角色有多个成员，则到此角色审批环节时，会审批单会通知对角色中所有人。当角色中的任意一人同意或拒绝，则此审批环节完成；
2) 部门主管为特殊角色，多次点击时会按层级叠加显示。1级主管=申请人所在部门主管，2级部门主管=申请人所在部门的父部门的部门主管，以此类推。_

#### 3.7.6预置知会人

* 预置知会人可以设置该审批将会通知谁，类似于邮件的“抄送”。选择具体员工或者角色为知会人，如某些与财务相关的流程必须知会 法务【角色】或 财务【角色】。设置后，申请人提交此表单时，表单中会默认添加好后台预置的知会人，无需申请者手动添加。这样，即使相关流程知会人的职务发生变化时，流程也无需再维护修改。

* 知会的通知方式分为三种：仅全部同意后通知，仅发起时通知，发起时和全部同意后均通知，企业可根据需要自行设置调整
# ![](/assets/3.7.6知会人设置.png)

#### 3.7.7分组管理

* 可以将模板按照分组的方式排列管理，方便选择，同时支持修改分组的名称，也可以删除，并对其排序

# ![](/assets/3.7.7添加分组.png)
# ![](/assets/3.7.7修改分组.png)




