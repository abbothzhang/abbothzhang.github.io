---
layout: indexGitHub

title: Xcode6升Xcode7遇到的问题及解决办法
---





####问题1：使用 universal-framework工程创建的工程，升到xcode7后universal无法重装导致framework打不出来
\--------解决办法：使用叁省创建的脚本，具体方法见http://www.atatech.org/articles/41378

-----

####问题2：build时报***does not contain bitcode. You must rebuild it with bitcode enabled (Xcodesetting ENABLE_BITCODE), obtain an updated library from the vendor, or disablebitcode for this target. for architecture arm64

\--------解决办法：在”Build Settings”->”Enable Bitcode”里设置为no。这是苹果为app瘦身做的优化，必须当所有的依赖的第三方bundle都支持时才可设置为yes

---

####问题3：控制台打印：Application Transport Security has blocked a cleartext HTTP (http://) resource load since it is insecure. Temporary exceptions can be configured via your app's Info.plist file.

\--------解决办法：在info.plist文件和`<key>CFBundleName</key>`平级的地方加入

`<key>NSAppTransportSecurity</key>
    <dict>
        <key>NSAllowsArbitraryLoads</key>
        <true/>
    </dict>`
    

---

####问题4：新建工程点击run时报process launch failed: Security。

\--------需要在手机上设置->通用->描述文件里点击信任


---

####ps：发现iOS9一个坑， AVCaptureSession isRunning方法在iOS9之前锁屏时返回YES，iOS9上为NO，使用到这个方法时候要注意




{{ page.date | date_to_string }}