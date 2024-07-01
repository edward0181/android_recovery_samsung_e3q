### TWRP device tree for Xiaomi 14

由于 Xiaomi 14 使用 Keyminit 3.0 Strongbox 加密, 我们大致需要以下步骤来解密 userdata:

metadata 解密后挂载 userdata → 输入密码 → weaver → keymint-strongbox → 对加密目录安装 key → userdata 解密完成.

经过测试发现 keymint-strongbox 需要调用一个 android.se.omapi.ISecureElementService 服务.

而 android.se.omapi.ISecureElementService/default 服务系统中由 SecureElementApplication_14.apk 提供, 我们无法在 TWRP 中直接运行.

因此我们需要一个能在 TWRP 中运行它的 c++ 替代品, 以达到解密 userdata 的目的. 

很明显我并没有这个能力将它转写成 TWRP 能跑的代码, 所以...