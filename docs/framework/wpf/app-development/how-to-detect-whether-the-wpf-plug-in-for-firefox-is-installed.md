---
title: "方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する | Microsoft Docs"
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
  - "確認 (Firefox プラグインを) [WPF]"
  - "検出 (Firefox のインストールを) [WPF]"
  - "検出 (Firefox に対応した WPF プラグインがインストールされているかどうかを) [WPF]"
  - "Firefox [WPF], 検出 (インストールを)"
  - "Firefox に対応したプラグイン [WPF]"
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する
Firefox に対応した [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] プラグインを使用すると、[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] ファイルおよび Loose XAML ファイルを Mozilla Firefox ブラウザーで実行できます。  ここでは、Firefox に対応した WPF プラグインがインストールされているかどうかを確認するための、HTML および JavaScript で記述されたスクリプトを示します。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のインストール、配置、および検出の詳細については、「[.NET Framework のインストール](../../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] がインストールされると、クライアント コンピューターは、Firefox に対応した WPF プラグインで構成されます。  Firefox に対応した WPF プラグインの有無をチェックして、適切なステータス メッセージを表示するスクリプトの例を次に示します。  
  
```  
<HTML>  
  
  <HEAD>  
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT type="text/javascript">  
    <!--  
    function OnLoad()  
    {  
  
       // Check for the WPF plug-in for Firefox and report  
       var msg = "The WPF plug-in for Firefox is ";  
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];  
       if( wpfPlugin != null ) {  
          document.writeln(msg + " installed.");  
       }  
       else {  
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");  
       }  
    }  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY onload="OnLoad()" />  
  
</HTML>  
```  
  
 Firefox に対応した WPF プラグインの有無のチェックが成功すると、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is installed.`  
  
 それ以外の場合は、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is not installed.  Please install or reinstall the .NET Framework 3.5.`  
  
## 参照  
 [.NET Framework 3.0 がインストールされているかどうかの確認](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)   
 [.NET Framework 3.5 がインストールされているかどうかの確認](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)   
 [WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)