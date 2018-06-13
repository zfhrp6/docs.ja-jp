---
title: '方法: .NET Framework 3.0 がインストールされているかどうかを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 09de427980ecfb515b8d341d0d7833b878140286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546492"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="c8855-102">方法: .NET Framework 3.0 がインストールされているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="c8855-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="c8855-103">管理者は、システム上の Microsoft .NET Framework アプリケーションを展開したりする前にする必要がありますまずことを確認した .NET Framework ランタイムが存在します。</span><span class="sxs-lookup"><span data-stu-id="c8855-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="c8855-104">このトピックで HTML または JavaScript で記述されたスクリプトは、.NET Framework は、システムに存在するかどうかを決定する管理者を使用できることです。</span><span class="sxs-lookup"><span data-stu-id="c8855-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8855-105">配置、および Microsoft .NET Framework の検出がの説明を参照してインストールする方法についての詳細、[を展開する Microsoft .NET Framework バージョン 3.0](http://go.microsoft.com/fwlink/?LinkId=96739)です。</span><span class="sxs-lookup"><span data-stu-id="c8855-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="c8855-106">".NET CLR"ユーザー エージェント文字列を検出します。</span><span class="sxs-lookup"><span data-stu-id="c8855-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="c8855-107">.NET Framework がインストールされている場合、MSI は、".NET CLR"とバージョン番号を UserAgent 文字列に追加します。</span><span class="sxs-lookup"><span data-stu-id="c8855-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="c8855-108">次の例では、単純な HTML ページに埋め込まれたスクリプトを示します。</span><span class="sxs-lookup"><span data-stu-id="c8855-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="c8855-109">スクリプトは、.NET Framework がインストールされているし、検索の結果のステータス メッセージを表示するかどうかを判断する UserAgent 文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="c8855-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
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
  
 <span data-ttu-id="c8855-110">".NET CLR"バージョンの検索が成功した場合は、次のようなステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8855-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="c8855-111">それ以外の場合、次のようなステータス メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8855-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
