---
title: ".NET アプリケーションの配置をサポートするための Firefox のアドオン | Microsoft Docs"
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
  - ".NET アプリケーションの配置, 配置 (Firefox アドオンによる)"
  - ".NET Framework Assistant for Firefox"
  - "Firefox アドオン (.NET アプリケーションを配置するための)"
  - "Firefox に対応した WPF プラグイン"
ms.assetid: 2403403b-9b14-48e9-b70d-fa288a3c9081
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# .NET アプリケーションの配置をサポートするための Firefox のアドオン
Firefox に対応した [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] プラグインおよび .NET Framework Assistant for Firefox を使用すると、[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]、Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、および ClickOnce アプリケーションを Mozilla Firefox ブラウザーで実行できます。  
  
## Firefox に対応した WPF プラグイン  
 Firefox に対応した WPF プラグインを使用すると、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] ファイルおよび Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルを Firefox ブラウザーの最上位レベルまたは HTML IFRAME にナビゲートして、そこで実行できます。  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、Web サーバーに公開してサポートされているブラウザー内で起動できる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションです。  Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、サポートされているブラウザーにナビゲートしてそのブラウザーで表示できる XAML のみのファイルです。XML ファイルとよく似ています。  
  
 Firefox に対応した [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] と共にインストールされます。  Window 7 には [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] が含まれますが、Firefox に対応した [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは含まれません。Windows 7 には、Firefox に対応した [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインをインストールできません。  
  
 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] には、Firefox に対応した [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] プラグインは含まれません。ただし、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] と [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] の両方がインストールされる場合、Firefox に対応した WPF プラグインは [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] と共にインストールされます。  WPF ホストが適切なバージョンのフレームワークを読み込むので、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] アプリケーションは稼働します。  詳細については、「[WPF ホスト \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)」を参照してください。  
  
## .NET Framework Assistant for Firefox  
 .NET Framework Assistant for Firefox を使用すると、スタンドアロンの ClickOnce アプリケーションを Firefox ブラウザーから実行できます。  .NET Framework Assistant for Firefox は、Firefox ブラウザーの前後どちらでインストールしたときも同じように機能します。  Firefox ブラウザーを起動して [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] をインストールするときに、Firefox が .NET Framework Assistant for Firefox を見つけてインストールします。  ユーザーは、.NET Framework Assistant for Firefox が次の動作を行うように構成できます。  
  
-   ClickOnce アプリケーションの実行前にプロンプトを表示する。  
  
-   インストールされている .NET Framework のすべてのバージョン、または最新バージョンのみを報告する。  
  
 .NET Framework Assistant for Firefox は、[!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] に含まれています。  .NET Framework Assistant for Firefox を削除する方法の詳細については、「[.NET Framework Assistant for Firefox を削除する方法](http://go.microsoft.com/fwlink/?LinkId=177944)」を参照してください。  
  
## 参照  
 [WPF アプリケーションの配置](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)   
 [WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)   
 [Firefox に対応した WPF プラグインがインストールされているかどうかを確認する](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed.md)