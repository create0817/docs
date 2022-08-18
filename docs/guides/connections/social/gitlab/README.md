# GitLab

<LastUpdated />

## 场景介绍

- **概述**：GitLab 社会化登录是用户以 GitLab 为身份源安全登录第三方应用或者网站。在 {{$localeConfig.brandName}} 中配置并开启 GitLab 的社会化登录，即可实现通过 {{$localeConfig.brandName}} 快速获取 GitLab 基本开放的信息和帮助用户实现免密登录功能。
- **应用场景**：PC 网站
- **终端用户预览图**：

![](./images/login.jpg)

## 注意事项

- 如果您还没有 GitLab 账号，请先前往 [GitLab.com](https://gitlab.com/users/sign_up/)注册账号
- 如果您未开通 {{$localeConfig.brandName}} 控制台账号，请先前往 [{{$localeConfig.brandName}} 控制台](https://authing.cn/) 注册开发者账号

## 步骤 1：在 {{$localeConfig.brandName}} 控制台配置 GitLab 的唯一标识

1.1 请在 {{$localeConfig.brandName}} 控制台的「社会化身份源」页面，点击「创建社会化身份源」按钮，进入「选择社会化身份源」页面。
![Snipaste_2022-08-18_11-03-02](https://user-images.githubusercontent.com/89245397/185283887-f91ac8a3-4dff-4ec6-b552-9a3e64da2588.png)



1.2 在「选择社会化身份源」页面，点击「GitLab」卡片。
![Snipaste_2022-08-18_11-04-06](https://user-images.githubusercontent.com/89245397/185283957-f2b84c53-84d9-403d-9997-61db66f506b3.png)


1.3 在「GitLab」配置页面，设置唯一标识
![Snipaste_2022-08-18_10-49-10](https://user-images.githubusercontent.com/89245397/185282171-34e9a891-06cc-4d93-bcfc-b0cba4accb94.png)


1.4 记录下根据唯一标识自动生成的回调地址,之后要用到。先将此页面搁置，之后再来配置其他信息。
![Snipaste_2022-08-18_10-46-02](https://user-images.githubusercontent.com/89245397/185282056-edf81728-324e-4c9e-a1a9-efe88aa28f2f.png)



## 步骤 2：在 GitLab（或者你的 GitLab 实例）创建一个应用

2.1 点击右上角个人头像然后点击「**Edit Profile**」
![Snipaste_2022-08-18_11-22-24](https://user-images.githubusercontent.com/89245397/185286118-abf358a9-3b27-4bee-a916-02f226be8bdb.png)



2.2 点击左边栏中「**Application**」：
![Snipaste_2022-08-18_11-25-01](https://user-images.githubusercontent.com/89245397/185286592-133f39c3-0635-4668-96c2-438214f80f1c.png)

2.3 配置应用名称
![Snipaste_2022-08-18_11-29-05](https://user-images.githubusercontent.com/89245397/185286817-7ed40864-bd19-4fa1-8a64-523d8c7124c1.png)


2.4 配置Redirect URI，将刚才记录的回调地址填写上去
![Snipaste_2022-08-18_11-31-02](https://user-images.githubusercontent.com/89245397/185287083-968e3152-fab1-4bec-8087-9db135b36411.png)


2.5 Scopes：**勾选 `read_user` 和 `api`**
![Snipaste_2022-08-18_11-32-08](https://user-images.githubusercontent.com/89245397/185287248-598676b8-78fb-43fb-b96f-9c4b22fbb882.png)


2.6 点击「**Save Application**」，创建完成之后，记录下`Application ID`和`Secret`，下一步需要用到。
![Snipaste_2022-08-18_11-32-59](https://user-images.githubusercontent.com/89245397/185287372-8bb4af81-d048-4972-a800-12473fa04250.png)



## 步骤 3：在控制台将Gitlab其他信息配置完成

3.1 将刚才记录的`Application ID`和`Secret`填写上去。
![Snipaste_2022-08-18_10-59-16](https://user-images.githubusercontent.com/89245397/185283492-0a6a60c0-1c15-4baf-a457-4fa9b99ec20c.png)

3.2 （可选）选择修改其他信息,如选择不修改，则使用默认选项
![Snipaste_2022-08-18_11-34-48](https://user-images.githubusercontent.com/89245397/185288251-a9957cde-1230-4328-9d7f-f90ca5847fa2.png)


| 字段           | 描述                                                                                                                                                         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 唯一标识       | a. 唯一标识由小写字母、数字、- 组成，且长度小于 32 位。<br />b. 这是此连接的唯一标识，设置之后不能修改。                                                     |
| 显示名称       | 这个名称会显示在终端用户的登录界面的按钮上。                                                                                                                 |
| Base URL       | 默认情况下会使用 GitLab.com 作为认证端点，你也可以指定任意私有的 GitLab 实例，如 https://gitlab.example.com/。                                               |
| Application ID | 上一步获取的 GitLab 应用 ID。                                                                                                                                |
| Secret         | 上一步获取的 GitLab 应用密钥。                                                                                                                               |
| 登录模式       | 开启「仅登录模式」后，只能登录既有账号，不能创建新账号，请谨慎选择。                                                                                         |
| 账号身份关联   | 不开启「账号身份关联」时，用户通过身份源登录时默认创建新用户。开启「账号身份关联」后，可以允许用户通过「字段匹配」或「询问绑定」的方式直接登录到已有的账号。 |

3.3 配置完成后，点击「创建」或者「保存」按钮完成创建。


## 步骤 4：开发接入

- **推荐开发接入方式**：使用托管登录页
- **优劣势描述**：运维简单，由 {{$localeConfig.brandName}} 负责运维。每个用户池有一个独立的二级域名；如果需要嵌入到你的应用，需要使用弹窗模式登录，即：点击登录按钮后，会弹出一个窗口，内容是 {{$localeConfig.brandName}} 托管的登录页面，或者将浏览器重定向到 {{$localeConfig.brandName}} 托管的登录页。
- **详细接入方法**：

  4.1 在 {{$localeConfig.brandName}} 控制台创建一个应用，详情查看：[如何在 {{$localeConfig.brandName}} 创建一个应用](/guides/app/create-app.md)

  4.2 在已经创建好的「GitLab」身份源连接详情页面，开启并关联一个在 {{$localeConfig.brandName}} 控制台创建的应用
  ![Snipaste_2022-08-18_11-34-48](https://user-images.githubusercontent.com/89245397/185288410-6b267c1e-a455-4b5d-9625-77ba099fe352.png)

  4.3 点击 {{$localeConfig.brandName}} 控制台的应用「体验登录」按钮，在弹出的登录窗口体验「GitLab」登录
  ![Snipaste_2022-08-18_11-43-57](https://user-images.githubusercontent.com/89245397/185288779-5bacfd22-52f2-4e6c-be51-eaec80c8b93a.png)

  ![Snipaste_2022-08-18_11-45-48](https://user-images.githubusercontent.com/89245397/185288887-0e4e5dc9-f91b-463e-bfe2-a7e53b3a6d48.png)
