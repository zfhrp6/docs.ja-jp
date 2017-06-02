---
title: "ClearType レジストリの設定 | Microsoft Docs"
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
  - "ClearType, レジストリ設定"
  - "タイポグラフィ, ClearType レジストリの設定"
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ClearType レジストリの設定
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで使用される [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] レジストリ設定の概要について説明します。  
  
   
  
<a name="overview"></a>   
## テクノロジの概要  
 ディスプレイ デバイスにテキストをレンダリングする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 機能を使用して読みやすさを拡張します。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、ラップトップや Pocket PC の画面、フラット パネル モニターなど、既存の LCD \(液晶ディスプレイ\) でのテキストの読みやすさを向上させるために [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] が開発したソフトウェア テクノロジです。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] は、LCD 画面の各ピクセル内の個々の垂直カラー ストライプ要素にアクセスすることによって機能します。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] の詳細については、「[ClearType の概要](../../../../docs/framework/wpf/advanced/cleartype-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] でレンダリングされるテキストの表示は、表示先のディスプレイ デバイスによって大きく異なります。  たとえば、一般的な赤、緑、青 \([!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]\) の順ではなく青、緑、赤の順でカラー ストライプ要素を実装するモニターもわずかに存在します。  
  
 また、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] でレンダリングされるテキストの表示は、各個人の色の感度レベルによっても大きく異なります。  他の人よりも色のわずかな違いを見分ける能力に長けている人もいます。  
  
 それぞれの場合において、各個人が最も読みやすい表示を実現するために、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 機能を変更する必要があります。  
  
<a name="registry_settings"></a>   
## レジストリ設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] の機能を制御するための 4 つのレジストリ設定が用意されています。  
  
|設定|Description|  
|--------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベル|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] の色の鮮明度を示します。|  
|ガンマ レベル|ディスプレイ デバイスのピクセル カラー コンポーネントのレベルを示します。|  
|ピクセル構造|ディスプレイ デバイスのピクセルの配置を示します。|  
|テキストのコントラスト レベル|表示されるテキストのコントラストのレベルを示します。|  
  
 これらの設定には、所定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レジストリ設定の参照方法を認識している外部構成ユーティリティを使用してアクセスできます。  また、これらの設定は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] レジストリ エディターを使用して値に直接アクセスして作成または変更することもできます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レジストリ設定が設定されていない場合 \(既定の状態\)、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションは、フォント スムージング設定について [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] システム パラメーター情報に照会します。  
  
> [!NOTE]
>  ディスプレイ デバイス名の列挙については、`SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 関数を参照してください。  
  
<a name="ClearType_level"></a>   
## ClearType レベル  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルを設定すると、個人の色の感度および知覚に基づいてテキストのレンダリングを調整できます。人によっては、最高レベルの [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] を使用するテキストのレンダリングでは最も読みやすい表示が実現されない場合があります。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルは、0 ～ 100 の範囲の整数値です。  既定のレベルは 100 です。これは、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] でディスプレイ デバイスの最大限のカラー ストライプ要素が使用されることを意味します。  ただし、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルが 0 の場合、テキストはグレースケールでレンダリングされます。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルを 0 ～ 100 の間に設定することで、個人の色の感度に適した中間レベルを実現できます。  
  
### レジストリ設定  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応する個別のユーザー設定の場所にあります。  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザのディスプレイ デバイス名ごとに `ClearTypeLevel` の DWORD 値が定義されます。  次のスクリーンショットは、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディターの ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] を使用する場合と使用しない場合のいずれかのモードでテキストがレンダリングされます。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] を使用しないテキストのレンダリングは、グレースケール レンダリングと呼ばれます。  
  
<a name="gamma_level"></a>   
## ガンマ レベル  
 ガンマ レベルとは、ピクセル値とルミナンス間の非線形リレーションシップのことです。  ガンマ レベル設定は、ディスプレイ デバイスの物理特性に対応する必要があります。対応していない場合、レンダリング出力にゆがみが発生する場合があります。  たとえば、テキストの表示が広すぎたり細すぎたりする場合や、色縁がグリフの縦線の端に表示される場合などがあります。  
  
 ガンマ レベルは、1000 ～ 2200 の範囲の整数値です。  既定のレベルは 1900 です。  
  
### レジストリ設定  
 ガンマ レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザのディスプレイ デバイス名ごとに `GammaLevel` の DWORD 値が定義されます。  次のスクリーンショットは、ガンマ レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディターの ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## ピクセル構造  
 ピクセル構造は、ディスプレイ デバイスを構成するピクセルの種類を示します。  ピクセル構造は、次の 3 種類のいずれかとして定義されます。  
  
|種類|値|Description|  
|--------|-------|-----------------|  
|フラット|0|ディスプレイ デバイスにピクセル構造がありません。  つまり、各色の光源がピクセル領域に均等に拡散しています。これは、グレースケール レンダリングと呼ばれます。  標準のディスプレイ デバイスはこのようにして機能します。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] はレンダリングされたテキストに適用されません。|  
|RGB|1|ディスプレイ デバイスのピクセルは、赤、緑、青の順の 3 つのストライプで構成されます。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] がレンダリングされたテキストに適用されます。|  
|BGR|2|ディスプレイ デバイスのピクセルは、青、緑、赤の順の 3 つのストライプで構成されます。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] がレンダリングされたテキストに適用されます。  順序が RGB の場合の逆であることに注目してください。|  
  
 ピクセル構造は、0 ～ 2 の範囲の整数値に対応します。  既定のレベルは 0 です。これは、フラット ピクセル構造を表します。  
  
> [!NOTE]
>  ディスプレイ デバイス名の列挙については、`EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 関数を参照してください。  
  
### レジストリ設定  
 ピクセル構造のレジストリ設定は、特定のディスプレイ デバイス名に対応するローカル マシン設定の場所にあります。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザのディスプレイ デバイス名ごとに `PixelStructure` の DWORD 値が定義されます。  次のスクリーンショットは、ピクセル構造のレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディターの ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## テキストのコントラスト レベル  
 テキストのコントラスト レベルを設定すると、グリフの縦線の幅に基づいてテキストのレンダリングを調整できます。  テキストのコントラスト レベルは、0 ～ 6 の範囲の整数値です。整数値を大きくすると、縦線の幅が広くなります。  既定のレベルは 1 です。  
  
### レジストリ設定  
 テキストのコントラスト レベルのレジストリ設定は、特定のディスプレイ デバイス名に対応する個別のユーザー設定の場所にあります。  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 ユーザのディスプレイ デバイス名ごとに `TextContrastLevel` の DWORD 値が定義されます。  次のスクリーンショットは、テキストのコントラスト レベルのレジストリ エディターの設定を示しています。  
  
 ![レジストリ エディターの ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## 参照  
 [ClearType の概要](../../../../docs/framework/wpf/advanced/cleartype-overview.md)   
 [ClearType アンチエイリアシング](_win32_ClearType_Antialiasing)