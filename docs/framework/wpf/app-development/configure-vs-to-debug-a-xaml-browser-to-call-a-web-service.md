---
title: "方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする | Microsoft Docs"
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
  - "構成 (XAML ブラウザー アプリケーションをデバッグするために Visual Studio を) [WPF]"
  - "構成 (XBAP をデバッグするために Visual Studio を) [WPF]"
  - "デバッグ (XBAP のセキュリティ例外を) [WPF]"
  - "デバッグ (Web サービスを呼び出す XBAP を) [WPF]"
  - "XBAP のセキュリティ例外 [WPF], デバッグ"
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] は、インターネット ゾーン アクセス許可セットに制限される部分信頼セキュリティ サンドボックス内で実行されます。  このアクセス許可セットは、Web サービス呼び出しを、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーションの起点サイトに位置する Web サービスにのみ制限するものです。  ただし、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] から [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] をデバッグする場合、参照する Web サービスと同じ起点サイトを持つとは見なされません。  このため、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] が Web サービスの呼び出しを試みると、セキュリティ例外が発生します。  ただし、[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] プロジェクトを構成することで、デバッグ時に、呼び出す Web サービスと同じ起点サイトを持つようにシミュレートできます。  これにより、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、セキュリティ例外を発生することなく、安全に Web サービスを呼び出すことができます。  
  
## Visual Studio の構成  
 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] を構成して、Web サービスを呼び出す [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] をデバッグするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[デバッグ\]** タブをクリックします。  
  
3.  **\[開始動作\]** セクションで、**\[外部プログラムの開始\]** をクリックし、次のように入力します。  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  **\[開始オプション\]** セクションで、**\[コマンド ライン引数\]** ボックスに次のように入力します。  
  
     `-debug`  *filename*  
  
     **\-debug** パラメーターの *filename* 値には、次に示すように、.xbap ファイル名を指定します。  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  これは、[!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] プロジェクト テンプレートで作成されるソリューションの既定の構成です。  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[デバッグ\]** タブをクリックします。  
  
3.  **\[開始オプション\]** セクションで、**\[コマンド ライン引数\]** ボックスに、次のコマンド ライン パラメーターを入力します。  
  
     `-debugSecurityZoneURL`  *URL*  
  
     **\-debugSecurityZoneURL** パラメーターの *URL* 値には、アプリケーションの起点サイトとしてシミュレートする場所の [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] を指定します。  
  
 たとえば、次の [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] の Web サービスを使用する [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] があるものとします。  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 この Web サービスの起点サイト [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] は、次のとおりです。  
  
 `http://services.msdn.microsoft.com`  
  
 したがって、完全な **\-debugSecurityZoneURL** コマンド ライン パラメーターおよび値は次のとおりです。  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## 参照  
 [WPF ホスト \(PresentationHost.exe\)](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)