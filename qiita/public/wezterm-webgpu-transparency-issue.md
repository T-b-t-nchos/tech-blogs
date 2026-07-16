---
title: NVIDIA GPU + WezTermでWebGPU透過が"出来なかった"話
private: false
tags:
  - wezterm
  - webgpu
  - nvidia
updated_at: '2026-07-16T08:20:44.034Z'
id: null
organization_url_name: null
slide: false
---

## ✨️ 結論

WezTermで、WebGPUの透過が出来ない時は、
NVIDIA コントロールパネルの、`3D設定の管理`から、
`Vulkan/OpenGLの既存の方法` を`ネイティブを優先する`にすべし。

## 🖥️ 環境
fastfetchより一部抜粋。
```
OS: Windows 11 Pro Insider Preview (25H2) x86_64
Host: B550M AORUS ELITE
Kernel: WIN32_NT 10.0.26220.8764
Display (LCD-AD243ED): 1920x1080 in 24", 60 Hz [External]
WM: Desktop Window Manager 10.0.26100.8764

Terminal: WezTerm 20260331-040028-577474d8

CPU: AMD Ryzen 5 5600G (12) @ 4.45 GHz
GPU 1: AMD Radeon(TM) Graphics (495.77 MiB) [Integrated]
GPU 2: NVIDIA GeForce GTX 1060 3GB @ 1.91 GHz (2.90 GiB) [Discrete]
Memory: 63.35 GiB
```

## 🤔 いきさつ

(参考までに...)

何故か突然、フロントエンドがWebGPUのWezTermのウィンドウ透過が出来なくなった。
OpenGLでは透過出来たけれど、フォントが細くなってしまい、よくない。

![OpenGLとWezTermの比較](https://raw.githubusercontent.com/T-b-t-nchos/tech-blogs/main/images/wezterm-webgpu-transparency-issue/image1.png)
*手前がWebGPU、奥がOpenGL (透過後)*

`webgpu_power_preference`を`LowPower`にしてみると、何故か色がおかしくなる...(!?)

![色が変...](https://raw.githubusercontent.com/T-b-t-nchos/tech-blogs/main/images/wezterm-webgpu-transparency-issue/image2.png)
*暗い...*

そこで、NVIDIA コントロールパネルの中身をいじくり回してみると、無事解決

## 📝 その他

ChatGPTに頼った際のリンク: https://chatgpt.com/share/6a589287-e6d8-83ee-b904-b4c7ca7479fb
(5月ぐらいから苦戦してました...)


## 🔍️ 最後に

有識者の方...何故これで解決できたのか、教えていただけると...!
