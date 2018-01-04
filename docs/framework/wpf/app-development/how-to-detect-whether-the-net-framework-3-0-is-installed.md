---
title: "方法: .NET Framework 3.0 がインストールされているかどうかを確認する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6990ca4bff7c8756f8d7f25ff0153b3a5d41a4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="2ebef-102">方法: .NET Framework 3.0 がインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="2ebef-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="2ebef-103">管理者は展開する前に[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)]アプリケーション システムでは、する必要がありますまずことを確認したこと、[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]ランタイムが存在します。</span><span class="sxs-lookup"><span data-stu-id="2ebef-103">Before administrators can deploy [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] applications on a system, they must first confirm that the [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] runtime is present.</span></span> <span data-ttu-id="2ebef-104">このトピックで記述されたスクリプトは、HTML または JavaScript を決定する管理者が使用できるのかどうか[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]は、システムに存在します。</span><span class="sxs-lookup"><span data-stu-id="2ebef-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ebef-105">インストール、配置、および検出についての詳細、[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]の説明を参照[を展開する Microsoft .NET Framework バージョン 3.0](http://go.microsoft.com/fwlink/?LinkId=96739)です。</span><span class="sxs-lookup"><span data-stu-id="2ebef-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="2ebef-106">".NET CLR"ユーザー エージェント文字列を検出します。</span><span class="sxs-lookup"><span data-stu-id="2ebef-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="2ebef-107">ときに[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]がインストールされている、MSI バージョン番号と".NET CLR"文字列に追加 UserAgent です。</span><span class="sxs-lookup"><span data-stu-id="2ebef-107">When [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="2ebef-108">次の例では、単純な HTML ページに埋め込まれたスクリプトを示します。</span><span class="sxs-lookup"><span data-stu-id="2ebef-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="2ebef-109">スクリプトを決定する UserAgent 文字列を検索するかどうか[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]がインストールされているし、検索の結果のステータス メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="2ebef-109">The script searches the UserAgent string to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="2ebef-110">".NET CLR"バージョンの検索が成功した場合は、次のようなステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ebef-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="2ebef-111">それ以外の場合、次のようなステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ebef-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
