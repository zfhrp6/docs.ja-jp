---
title: "グラフィックス レンダリングのレジストリ設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グラフィックス [WPF], 描画"
  - "描画 (グラフィックスを)"
  - "描画 (グラフィックスを), レジストリ設定"
  - "描画 (グラフィックスを), トラブルシューティング"
  - "トラブルシューティング (グラフィックス レンダリング)"
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# グラフィックス レンダリングのレジストリ設定
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに影響を与える [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス レンダリングのレジストリ設定の概要について説明します。  
  
   
  
<a name="overview"></a>   
## グラフィックス レンダリングのレジストリ設定を使用する場合  
 これらのレジストリ設定は、トラブルシューティング、デバッグ、および製品サポートのために提供されています。  レジストリを変更するとすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションが影響を受けるので、アプリケーションでは、これらのレジストリ キーを自動的に変更したり、インストール時に変更したりしないでください。  
  
<a name="xpdmandwddm"></a>   
## XPDM と WDDM について  
 グラフィックス レンダリングのレジストリの一部の設定は、ビデオ カードが XPDM ドライバーまたは WDDM ドライバーのどちらを使用するかによって、既定値が異なります。  XPDM は [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Display Driver Model、WDDM は Windows Display Driver Model の略です。  WDDM は、[!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] および [!INCLUDE[win7](../../../../includes/win7-md.md)] を実行中のコンピューターで使用できます。  XPDM は、[!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]、および [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)] を実行中のコンピューターで使用できます。  WDDM の詳細については、「[Windows Vista Display Driver Model Design Guide \(Windows Vista ディスプレイ ドライバー モデル デザイン ガイド\)](http://go.microsoft.com/fwlink/?LinkId=178394)」を参照してください。  
  
<a name="registry_settings"></a>   
## レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のレンダリングを制御するために 4 つのレジストリ設定が用意されています。  
  
|設定|Description|  
|--------|-----------------|  
|**Disable Hardware Acceleration Option**|ハードウェア アクセラレータを有効にするかどうかを指定します。|  
|**Maximum Multisample Value**|[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] コンテンツのアンチエイリアシングのマルチサンプリングの度合いを指定します。|  
|**Required Video Driver Date Setting**|2004 年 11 月より前にリリースされたドライバーに対してハードウェア アクセラレータをシステムで無効にするかどうかを指定します。|  
|**Use Reference Rasterizer Option**|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でリファレンス ラスタライザーを使用するかどうかを指定します。|  
  
 これらの設定には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レジストリ設定の参照方法を認識している外部構成ユーティリティを使用してアクセスできます。  また、これらの設定は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] レジストリ エディターを使用して値に直接アクセスして作成または変更することもできます。  
  
<a name="disablehardwareacceleration"></a>   
## Disable Hardware Acceleration Option  
  
|レジストリ キー|値の種類|  
|--------------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **Disable Hardware Acceleration Option** を使用すると、デバッグとテストのためにハードウェアの加速を無効にできます。  アプリケーションでレンダリング アイテムを表示するとき、ハードウェア加速を無効にしてみてください。  アイテムが消える場合は、ビデオ ドライバーの問題である可能性があります。  
  
 **Disable Hardware Acceleration Option** は、0 か 1 の DWORD 値です。  値を 1 に設定すると、ハードウェア アクセラレータが無効になります。  値が 0 の場合、システムがハードウェア加速の要件を満たしていれば、ハードウェア加速が有効になります。詳細については、「[グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)」を参照してください。  
  
<a name="maxmultisample"></a>   
## Maximum Multisample Value  
  
|レジストリ キー|値の種類|  
|--------------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 **Maximum Multisample Value** を使用すると、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] コンテンツのアンチエイリアシングの最大量を調整できます。  [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] のアンチエイリアシングを [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] で無効にするには、または [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] で有効にするには、このレベルを使用します。  
  
 **Maximum Multisample Value** は、0 ～ 16 の範囲の DWORD 値です。  値 0 を指定すると、3\-D コンテンツのマルチサンプル アンチエイリアシングは無効になり、値 16 を指定すると、ビデオ カードがサポートする場合は、最大で 16 倍のマルチサンプル アンチエイリアシングの使用が試行されます。  XPDM ドライバーを使用するコンピューターでこのレジストリ キー値を設定すると、アプリケーションは大量のビデオ メモリを追加使用するため、[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] レンダリングのパフォーマンスが低下し、レンダリング エラーや安定性の問題が発生する可能性があることに注意してください。  
  
 このレジストリ キーを設定しないと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定値は、XPDM ドライバーでは 0、WDDM ドライバーでは 4 になります。  
  
<a name="requiredvideodriverdatesetting"></a>   
## Required Video Driver Date Setting  
  
|レジストリ キー|値の種類|  
|--------------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|\[文字列\]|  
  
 2004 年 11 月に、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] はドライバー テストに関するガイドラインの新バージョンをリリースしました。これ以降に作成されたドライバーは、安定性が向上しています。  既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、これらのドライバーに対してはハードウェア加速パイプラインを使用し、この日より前に公開された XPDM ドライバーについてはソフトウェア レンダリングを使用します。  
  
 **Required Video Driver Date Setting** を使用すると、XPDM ドライバーに対して最低限の代わりの日付を指定できます。  使用するビデオ ドライバーが十分に安定して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をサポートすることが確実な場合にのみ、2004 年 11 月より前の日付を指定するようにしてください。  
  
 ビデオ ドライバーの設定では、次の形式の文字列を使用する必要があります。  
  
||  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 *YYYY* は 4 桁の年、*MM* は 2 桁の月、*DD* は 2 桁の日です。  この値を設定しないと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は必要なビデオ ドライバーの日付として 2004 年 11 月を使用します。  
  
<a name="usereferencerasterizeroption"></a>   
## Use Reference Rasterizer Option  
  
|レジストリ キー|値の種類|  
|--------------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **Use Reference Rasterizer Option** を使用すると、強制的に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] をデバッグ用のシミュレートされたハードウェア レンダリング モードにすることができます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] はハードウェア モードになりますが、実際のハードウェア デバイスの代わりに、[!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] リファレンス ソフトウェア ラスタライザー d3dref9.dll を使用します。  
  
 リファレンス ラスタライザーは非常に低速ですが、ビデオ ドライバーをバイパスし、ドライバーの問題によって発生するレンダリングの問題を回避します。  このため、リファレンス ラスタライザーを使用すると、レンダリングの問題の原因がビデオ ドライバーかどうかを判断できます。  d3dref9.dll ファイルは、システム パス内の場所やアプリケーションのローカル ディレクトリなど、アプリケーションがアクセスできる場所に存在する必要があります。  
  
 **Use Reference Rasterizer Option** は DWORD 値を受け取ります。  値 0 は、リファレンス ラスタライザーを使用しないことを示します。  他の 0 以外の値は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にリファレンス ラスタライザーの使用を強制します。  
  
## 参照  
 [グラフィックスの描画層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)