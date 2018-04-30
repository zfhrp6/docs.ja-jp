---
title: '方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b58abda33aa48372e4642dca48599867f389045
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する
Windows Presentation Foundation (WPF) Firefox のプラグインを有効に[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Mozilla Firefox ブラウザーで実行する XAML ファイルが失われるとします。 このトピックでは、HTML および WPF Firefox のプラグインがインストールされているかどうかを決定する管理者が使用できる JavaScript で記述されたスクリプトを提供します。  
  
> [!NOTE]
>  インストール、配置、および検出の詳細については、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]を参照してください[開発者向け .NET Framework をインストール](../../../../docs/framework/install/guide-for-developers.md)です。  
  
## <a name="example"></a>例  
 ときに、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]がインストールされている、クライアント コンピューターが構成されているプラグインの wpf Firefox のです。 次のスクリプトの例では、プラグインの WPF Firefox のチェックし、適切なステータス メッセージを表示します。  
  
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
  
 Firefox のプラグインの WPF のチェックが成功した場合は、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is installed.`  
  
 それ以外の場合、次のステータス メッセージが表示されます。  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 3.0 がインストールされているかどうかを確認する](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [.NET Framework 3.5 がインストールされているかどうかを確認する](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
