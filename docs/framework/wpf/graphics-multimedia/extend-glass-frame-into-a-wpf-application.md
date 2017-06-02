---
title: "WPF アプリケーションへのグラス フレームの拡張 | Microsoft Docs"
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
  - "アプリケーション, 拡張 (グラス フレームを)"
  - "拡張 (アプリケーションにグラス フレームを)"
  - "グラス フレーム, 拡張 (アプリケーションに)"
  - "グラフィックス, 拡張 (アプリケーションにグラス フレームを)"
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# WPF アプリケーションへのグラス フレームの拡張
ここでは、[!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] のグラス フレームを [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションのクライアント領域に拡張する方法について説明します。  
  
> [!NOTE]
>  この例は、グラス対応の Desktop Window Manager \(DWM\) を実行している [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] コンピューターでのみ機能します。  [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic は、透明なグラス効果をサポートしていません。  その他の [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] で通常は透明なグラス効果でレンダリングされる領域は、不透明にレンダリングされます。  
  
## 使用例  
 Internet Explorer 7 のアドレス バーに拡張されたグラス フレームを次の図に示します。  
  
 **アドレス バーの背後にグラス フレームが拡張された Internet Explorer**  
  
 ![アドレス バーの背後にグラス フレームが拡張された IE7。](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 グラス フレームを [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで拡張するには、アンマネージ [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] へのアクセスが必要です。  フレームをクライアント領域に拡張するために必要な 2 つの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] に対してプラットフォーム呼び出し \(pinvoke\) を実行する方法を次のコード例に示します。  これらの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] は、それぞれ **NonClientRegionAPI** と呼ばれるクラスで宣言されます。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#DWMExtendFramePInvokeAPI](AvalonClientGlass#DWMExtendFramePInvokeAPI)]  -->  
  
 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea) [](_udwm_dwmextendframeintoclientarea) は、フレームをクライアント領域に拡張する DWM 関数です。  この関数では、ウィンドウ ハンドルと [MARGINS](inet_MARGINS) 構造体という、2 つのパラメーターを使用します。  [MARGINS](inet_MARGINS) は、フレームをクライアント領域に拡張する追加量を DWM に指示するために使用されます。  
  
## 使用例  
 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea) 関数を使用するには、ウィンドウ ハンドルを取得する必要があります。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、ウィンドウ ハンドルは <xref:System.Windows.Interop.HwndSource> の <xref:System.Windows.Interop.HwndSource.Handle%2A> プロパティから取得できます。  次の例では、ウィンドウの <xref:System.Windows.FrameworkElement.Loaded> イベントでフレームがクライアント領域に拡張されます。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#AvalonGlassOnLoadedCSharp](AvalonClientGlass#AvalonGlassOnLoadedCSharp)]  -->  
  
## 使用例  
 フレームがクライアント領域に拡張される簡単なウィンドウを次の例に示します。  フレームは、2 つの <xref:System.Windows.Controls.TextBox> オブジェクトを含む一番上の境界の背後に拡張されます。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#AvalonGlassFullWindowXAML](AvalonClientGlass#AvalonGlassFullWindowXAML)]  -->  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションに拡張されたグラス フレームを次の図に示します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **アプリケーション** に**拡張されたグラス フレーム**。  
  
 ![WPF アプリケーションに拡張されたグラス フレーム。](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.png "WPFextendedGlassIntoClient")  
  
## 参照  
 [Desktop Window Manager Overview](_udwm_overview)   
 [Desktop Window Manager Blur Overview](_udwm_blur_ovw)   
 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea)