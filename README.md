# Cocoapods-Spec-Started-
### 如何将自己的成果做成Pod库供别人使用
#### 看网上的介绍多多少少都不全，这里只针对一种情况作阐述，目的是让想把自己成果分享给大家的思密达们少走弯路
#### 本文以项目已经在github上托管，想把项目中某些文件做成Pod库的情况为例来阐述
##### step1 fork Specs files
首先进入官方（https://github.com/CocoaPods/Specs），fork一份podSpecs，此过程估计时间较长，耐心等待，如图![image］(https://ss)
fork完成之后clone到本地（本文是桌面Desktop）或直接下载到本地，解压后如图![image](https://ss)
##### step2 create podspec file
打开终端进入Specs-Matser->Specs你会看到好多别人已经提交的Specs
`$ mkdir 你想创建的Pod的名字` eg.NHEnDecryptor
进入文件夹NHEnDecryptor
`$ mkdir 你想创建的版本` eg. 0.0.3
进入0.0.3文件夹 执行创建podspec文件的命令
`$ pod spec create NHEnDecryptor`
创建完成后如图![image](https://ss)
##### step3 Edit podSpec file
```
Pod::Spec.new do |s|

  s.name         = "NHEnDecryptor"
  s.version      = "0.0.3"
  s.summary      = "NHEnDecryptor is an Objc Wrapper for SSL."
  s.homepage     = "https://github.com/iFindTA"
  s.description  = "SSL En/Decrypt warpper by Objc Include AES/RSA signature and verify data for ios"
  s.license      = "MIT(LICENSE)"
  s.author             = { "nanhujiaju" => "nanhujiaju@163.com" }
  s.platform     = :ios, "7.0"
  s.source       = { :git => "https://github.com/iFindTA/NHEnDecryptPro.git", :tag => "0.0.3" }
  s.source_files  = "NHEnDecryptPro/Security/*.{h,a}"
  s.public_header_files = "NHEnDecryptPro/Security/*.h"

  s.framework  = "UIKit","Foundation","Security"
  # s.frameworks = "SomeFramework", "AnotherFramework"

  s.requires_arc = true
  # s.dependency "JSONKit", "~> 1.4"
  @end

```
关于这段的设置代码很简单易懂 实在不懂或有其他需求可上网查一下
退出保存

##### step4 verify podspec file
验证你的设置和github上的代码是否正确，执行代码：
`pod spec lint NHEnDecryptor.podspec ` 
这是比较关键的一步，确保没有错误和警告，如果验证成功你将看到下边的提示：
```
Analyzed 1 podspec.

NHEnDecryptor.podspec passed validation.

```
如果提示错误和警告请回到step3检查podspec文件

##### step5 Register CocoaPods Session
`$ pod trunk register name@example.org 'Your Name' --description='macbook pro'`
然后你会在邮箱中收到一封验证邮件，点击验证链接，然后回到终端
##### step6 push podspec file
`pod trunk push NHEnDecryptor.podspec`
接下来就是稍微耐心等待一下
```
- Data URL: https://raw.githubusercontent.com/CocoaPods/Specs/77452efc17bf18757e9a6ab9b09d5a3d08b3f649/Specs/NHEnDecryptor/0.0.3/NHEnDecryptor.podspec.json
  - Log messages:
    - September 29th, 02:35: Push for `NHEnDecryptor 0.0.3' initiated.
    - September 29th, 02:35: Push for `NHEnDecryptor 0.0.3' has been pushed
    (1.760894249 s).

```
看到上述提示说明你已经提交成功了，等待CocoaPods团队的审核吧，很快就会通过，然后就可以通过终端搜索到你的成果了！

#### 好了！恭喜你！至此你已经学会了如何将自己的成果分享给大家了！赶快行动吧