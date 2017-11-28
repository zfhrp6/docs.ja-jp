---
title: "WPF ホスト (PresentationHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b7662213d7204675de7e8681b6fc8141f04dd21
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-host-presentationhostexe"></a>WPF ホスト (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホスト (PresentationHost.exe) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを互換ブラウザー ([!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] 以降を含む) でホスト可能にするアプリケーションです。 既定では、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、ブラウザーによってホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツのシェルと [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] ハンドラーとして登録されます。該当するコンテンツには、次のものが含まれます。  
  
-   Loose (コンパイルされていない) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル (.xaml)。  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap)。  
  
 これらの種類のファイルに対して、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、次の処理を実行します。  
  
-   [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] コンテンツをホストするために、登録されている [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ハンドラーを起動します。  
  
-   必要な [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] と [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アセンブリの正しいバージョンを読み込みます。  
  
-   展開のゾーンに適切なアクセス許可レベルが設定されるようにします。  
  
 このトピックでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。  
  
## <a name="usage"></a>使用方法  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|ファイル名|アクティブにするファイルのパス。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] も指定できます。|  
|-debug|アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。 これは、ローカル ファイルをアクティブにする場合に限って使用できます。|  
|-debugSecurityZoneURL \<url>|アプリケーションを、指定した [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] から展開されたものとしてデバッグする必要があることを PresentationHost.exe に指示するために、[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 値と共に使用します。 これは、展開ゾーンと起点サイトの両方を決定します。|  
|-embedding|OLE で必要になります。 `-event` パラメーターまたは `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。|  
|-event \<eventname>|PresentationHost.exe が初期化され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。 PresentationHost.exe は、イベントを開く際にエラーが発生すると (そのイベントがまだ作成されていない場合など) 終了します。|  
|-launchApplication \<url>|指定した URL から、スタンドアロンの [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションを起動します。 .NET アプリケーションに関する [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] と WinINet のセキュリティ ポリシーが適用されます。|  
  
## <a name="scenarios"></a>シナリオ  
  
### <a name="shell-handler"></a>シェル ハンドラー  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>MIME ハンドラー  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio によるデバッグ  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio によるゾーンでのデバッグ  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>関連項目  
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)
