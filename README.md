# Mi 11 Lite 5G 向けDevice Tree (Android 17対応)
日本版への最適化やKernelSUの導入など、個人的に使いたい機能を統合したDevice Treeです。

## このDevice Treeでの機能
- crDroid 13.x (Android 17) / crDroid 12.x (Android 16 QPR2)
  - LineageOS系統であれば、おそらく他のROMもビルド可能
  - (2026/10/6) ひとまずAndroid 17で起動確認できました
- ReSukiSU + SUSFS
  - A16 QPR2より非GKIデバイスと互換性の高いBakaSU/ReSukiSUに変更しました
  - パッチは[JackA1ltman/NonGKI_Kernel_Build_2nd](https://github.com/JackA1ltman/NonGKI_Kernel_Build_2nd)を使用
- 日本版への最適化
  - 端末情報を`M2101K9R`として設定
  - おサイフケータイ対応
  - 技適表示 (保証なし)

## 使用上の注意
**カスタムROMは自己責任で使用してください。**

このOrganizationに含まれるデータは、非営利の調査・研究目的で提供されています。

**カスタムROMやDevice Treeの使用に起因するデータ損失等の損害について、一切保証いたしません。また、各機能は「現状のまま」提供され、Cememerは一切の責任を負いません。**

おサイフケータイアプリは利用可能ですが、**実際に非接触決済ができるかは保証しません。**

GAPPSの導入などは各自で行ってください。

## ビルド上の注意点
このリポジトリにある`local_manifests`を使用し、patch/内のパッチを当てるとビルドできるかと思います。

### パッチについて

- build_make_core_tasks__avoidance_check.patch
  - `availability check`エラー抑制
- packages_apps_Settings__enable_regulatory_info.patch
  - 設定で技適(規制ラベル)を表示させるパッチ (device_xiaomi_renoirで規制ラベルを設定するだけではうまく統合されませんでした)
- kernel_xiaomi_sm8350__commentout_hooks_error.patch
  - KSUの手動フック未設定の警告によるカーネルビルドエラー抑制 (必要なパッチはkernel_xiaomi_sm8350に適用済)

## Credits
- @xiaomi-lisa-devs
  - SM8350共通コンポーネントのベース、Android 16/17対応
- @felica-droid
  - 日本版への最適化
- @LineageOS
  - LineageOS/android_device_xiaomi_renoir
  - LineageOS/android_device_xiaomi_sm8350-common
  - LineageOS/android_kernel_xiaomi_sm8350
    - LineageOS/android_kernel_qcom_sm8350
- [JackA1ltman/NonGKI_Kernel_Build_2nd](https://github.com/JackA1ltman/NonGKI_Kernel_Build_2nd)
  - ReSukiSU/SUSFSの統合パッチ