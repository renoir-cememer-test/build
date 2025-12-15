# Mi 11 Lite 5G 向けDevice Tree (Android 16対応)
日本版への最適化やKernelSUの導入など、個人的に使いたい機能を統合したDevice Treeです。

## このDevice Treeでの機能
- crDroid 12.x (Android 16)
  - LineageOS系統であれば、おそらく他のROMもビルド可能？
- KernelSU Next v1.1.1 + SUSFS v1.5.5
- 日本版への最適化
  - 端末情報を`M2101K9R`として設定
  - 技適表示 (保証なし)
  - おサイフケータイの構成 (未検証)

## 使用上の注意
**カスタムROMは自己責任で使用してください。**

このOrganizationに含まれるデータは、非営利の調査・研究目的で提供されています。

**カスタムROMやDevice Treeの使用に起因するデータ損失等の損害について、一切保証いたしません。また、各機能は「現状のまま」提供され、Cememerは一切の責任を負いません。**

おサイフケータイアプリは利用可能ですが、**実際に非接触決済ができるかは未検証です。**

GAPPSの導入などは各自で行ってください。

## ビルド上の注意点
`local_manifests`は、このリポジトリにある物を使用するとビルドできるかと思います。

ただし、そのままではavailability checkでエラーが発生するため、`build_make_core_tasks__avoidance_check.patch`を適用して、エラーを抑制させる必要があります。

`packages_apps_Settings__enable_regulatory_info.patch`は、設定で技適(規制ラベル)表示を表示させるパッチです。(DeviceTreeに規制ラベル表示を設定してもうまく統合されないようです...)

## Credits
- @xiaomi-lisa-devs
  - SM8350共通コンポーネントのベース、Android 16対応
- @felica-droid
  - 日本版への最適化
- @LineageOS
  - LineageOS/android_device_xiaomi_renoir
  - LineageOS/android_device_xiaomi_sm8350-common
  - LineageOS/android_kernel_xiaomi_sm8350
    - LineageOS/android_kernel_qcom_sm8350