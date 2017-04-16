---
title: "WPF ホスト (PresentationHost.exe) | Microsoft Docs"
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
  - "PresentationHost.exe"
  - "WPF ホスト アプリケーション"
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# WPF ホスト (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホスト \(PresentationHost.exe\) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを互換ブラウザー \([!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] およびそれ以降を含む\) でホストできるようにするアプリケーションです。  既定では、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、ブラウザーによってホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツのシェルおよび [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] ハンドラーとして登録されます。該当するコンテンツには、次のものが含まれます。  
  
-   Loose である \(コンパイルされていない\) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル \(.xaml\)。  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] \(.xbap\)。  
  
 これらの種類のファイルに対して、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、次の処理を実行します。  
  
-   [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] コンテンツをホストするために、登録されている [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ハンドラーを起動します。  
  
-   必要な[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] および [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アセンブリの正しいバージョンを読み込みます。  
  
-   展開のゾーンに適切なアクセス許可レベルが設定されるようにします。  
  
 ここでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。  
  
## 使用方法  
 `PresentationHost.exe [parameters] uri|filename`  
  
## パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|filename|アクティブにするファイルのパス。  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] も指定できます。|  
|\-debug|アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。  これは、ローカル ファイルをアクティブにする場合に限って使用できます。|  
|\-debugSecurityZoneURL \<url\>|アプリケーションを、指定した [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] から展開されたものとしてデバッグする必要があることを PresentationHost.exe に指示するために、[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 値と共に使用します。  これは、展開ゾーンと起点サイトの両方を決定します。|  
|\-embedding|OLE で必要になります。  `-event` または `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。|  
|\-event \<eventname\>|PresentationHost.exe が初期化され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。  PresentationHost.exe は、イベントを開く際にエラーが発生すると \(そのイベントがまだ作成されていない場合など\) 終了します。|  
|\-launchApplication \<url\>|指定した URL から、スタンドアロンの [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションを起動します。  .NET アプリケーションに関する [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] および WinINet のセキュリティ ポリシーが適用されます。|  
  
## シナリオ  
  
### シェル ハンドラー  
 `PresentationHost.exe example.xbap`  
  
### MIME ハンドラー  
 `PresentationHost.exe -embedding example.xbap`  
  
### Visual Studio によるデバッグ  
 `PresentationHost.exe -debug example.xbap`  
  
### Visual Studio によるゾーンでのデバッグ  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## 参照  
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)