---
title: "方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e821bd95679372fd169b7880e969fd10b5d03c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="6deff-102">方法 : Firefox に対応した WPF プラグインがインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="6deff-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>
<span data-ttu-id="6deff-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Firefox 有効用のプラグイン[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Mozilla Firefox ブラウザーで実行する XAML ファイルが失われるとします。</span><span class="sxs-lookup"><span data-stu-id="6deff-103">The [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] plug-in for Firefox enables [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="6deff-104">このトピックでは、HTML および WPF Firefox のプラグインがインストールされているかどうかを決定する管理者が使用できる JavaScript で記述されたスクリプトを提供します。</span><span class="sxs-lookup"><span data-stu-id="6deff-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6deff-105">インストール、配置、および検出の詳細については、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]を参照してください[開発者向け .NET Framework をインストール](../../../../docs/framework/install/guide-for-developers.md)です。</span><span class="sxs-lookup"><span data-stu-id="6deff-105">For more information about installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6deff-106">例</span><span class="sxs-lookup"><span data-stu-id="6deff-106">Example</span></span>  
 <span data-ttu-id="6deff-107">ときに、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]がインストールされている、クライアント コンピューターが構成されているプラグインの wpf Firefox のです。</span><span class="sxs-lookup"><span data-stu-id="6deff-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="6deff-108">次のスクリプトの例では、プラグインの WPF Firefox のチェックし、適切なステータス メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="6deff-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>  
  
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
  
 <span data-ttu-id="6deff-109">Firefox のプラグインの WPF のチェックが成功した場合は、次のステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6deff-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is installed.`  
  
 <span data-ttu-id="6deff-110">それ以外の場合、次のステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6deff-110">Otherwise, the following status message is displayed:</span></span>  
  
 `The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`  
  
## <a name="see-also"></a><span data-ttu-id="6deff-111">参照</span><span class="sxs-lookup"><span data-stu-id="6deff-111">See Also</span></span>  
 [<span data-ttu-id="6deff-112">.NET Framework 3.0 がインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="6deff-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)  
 [<span data-ttu-id="6deff-113">.NET Framework 3.5 がインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="6deff-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-5-is-installed.md)  
 [<span data-ttu-id="6deff-114">WPF XAML ブラウザー アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="6deff-114">WPF XAML Browser Applications Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)
