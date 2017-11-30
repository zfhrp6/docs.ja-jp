---
title: ".NET アプリケーションの配置をサポートするための Firefox のアドオン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Firefox add-ons for .NET application deployment
- WPF plug-in for Firefox
- .NET application deployment [WPF], deploying with Firefox add-ons
- .NET Framework Assistant for Firefox
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f16fc118ccfef6cfcb9ab0dc1356cb0c732ae229
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="firefox-add-ons-to-support-net-application-deployment"></a>.NET アプリケーションの配置をサポートするための Firefox のアドオン
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Firefox および Firefox の有効化の .NET Framework アシスタントのプラグイン[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]loose、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、や Mozilla Firefox ブラウザーで動作する ClickOnce アプリケーションです。  
  
## <a name="wpf-plug-in-for-firefox"></a>WPF Firefox のプラグイン  
 WPF Firefox のプラグインを有効に[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]厳密でないと[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に移動し、最上位または Firefox ブラウザーで HTML IFRAME でを実行するファイル。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]は、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Web サーバーにパブリッシュして内で起動できるアプリケーションでサポートされているブラウザー。 厳密でない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]XAML のみのファイルに移動し、XML ファイルと同様に、サポートされているブラウザーに表示されることができます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox がと共にインストールされるプラグイン、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]です。 ウィンドウ 7 には、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]は含まれませんが、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox のプラグイン。 インストールすることはできません、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox Windows 7 用のプラグイン。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]を含まない、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Firefox のプラグイン。 ただし、両方、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]と[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]がインストールされている WPF Firefox のプラグインがインストールされていると、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]です。 したがって[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]WPF ホストは、フレームワークの正しいバージョンを読み込むためのアプリケーションは引き続き実行します。 詳細については、次を参照してください。 [WPF ホスト (PresentationHost.exe)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)です。  
  
## <a name="net-framework-assistant-for-firefox"></a>.NET Framework Assistant for Firefox  
 Firefox の .NET Framework アシスタント Firefox ブラウザーから実行するスタンドアロンの ClickOnce アプリケーションを使用できます。 .NET Framework アシスタントでは、Firefox 関数 Firefox ブラウザーの前後にインストールされている場合に同じです。 Firefox ブラウザーが起動した場合、[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]がインストールされている、Firefox で検索して、Firefox 用の .NET Framework アシスタントをインストールします。 ユーザーは、Firefox には、次の .NET Framework Assistant で構成できます。  
  
-   ClickOnce アプリケーションを実行する前に確認します。  
  
-   インストールされているすべてのバージョンの .NET Framework または最新のバージョンのみを報告します。  
  
 Firefox の .NET Framework アシスタントに含まれて、[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)]です。 Firefox の .NET Framework アシスタント削除については、次を参照してください。 [Firefox の .NET Framework アシスタントを削除する方法](http://go.microsoft.com/fwlink/?LinkId=177944)です。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションの配置](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)  
 [WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)  
 [Firefox に対応した WPF プラグインがインストールされているかどうかを確認する](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)
