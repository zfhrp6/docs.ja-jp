---
title: "IWpfHostSupport | Microsoft Docs"
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
  - "IWpfHostSupport インターフェイス"
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# IWpfHostSupport
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コンテンツを PresentationHost.exe を介してホストするアプリケーションは、ホストと PresentationHost.exe を統合するポイントを提供するために、このインターフェイスを実装します。  
  
## 解説  
 Web ブラウザーなどの [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] アプリケーションは、[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] や Loose XAML などの [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] コンテンツをホストできます。  [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] アプリケーションは、[!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] コンテンツをホストするために、[WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)のインスタンスを作成します。  [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] をホストするには、PresentationHost.exe のインスタンスを作成します。これにより、ホストされる [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] コンテンツを [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=97911)で表示するために、ホストに提供します。  
  
 `IWpfHostSupport` で有効化される統合により、PresentationHost.exe では次のことが可能になります。  
  
-   ホスト アプリケーションに必要な未加工の入力デバイス \(ヒューマン インターフェイス デバイス\) を検出して登録する。  
  
-   登録された未加工の入力デバイスからの入力メッセージを受け取り、適切なメッセージをホスト アプリケーションに転送する。  
  
-   ホスト アプリケーションに対して、進行状況とエラーに関するカスタム ユーザー インターフェイスの有無を照会する。  
  
> [!NOTE]
>  この API は、ローカルのクライアント コンピューターでのみ使用できます。  
  
## メンバー  
  
|メンバー|Description|  
|----------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|ホスト アプリケーションに必要な入力ロー デバイス \(ヒューマン インターフェイス デバイス\) を PresentationHost.exe が検出できるようにします。|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|E\_NOTIMPL が返されない限り、メッセージを受け取るたびに PresentationHost.exe によって呼び出されます。|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|既定では、PresentationHost.exe には、WPF コンテンツの配置時に表示される、独自の配置状況と配置エラーのユーザー インターフェイスが備わっています。|