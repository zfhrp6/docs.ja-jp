---
title: "方法: .NET Framework 3.5 がインストールされているかどうかを確認する | Microsoft Docs"
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
  - "検出 (.NET Framework 3.5 のインストールを) [WPF]"
  - "検出 (.NET Framework 3.5 がインストールされているかどうかを) [WPF]"
  - "確認 (.NET Framework 3.5 がインストールされているかどうかを) [WPF]"
  - "検証 (.NET Framework 3.5 がインストールされているかどうかを) [WPF]"
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法: .NET Framework 3.5 がインストールされているかどうかを確認する
管理者が [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションを [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] に対応するシステムに配置するには、最初に、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] ランタイムが存在することを確認する必要があります。  ここでは、システムに [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] が存在するかどうかを確認するための、HTML\/JavaScript で記述されたスクリプトを示します。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のインストール、配置、および検出の詳細については、「[.NET Framework のインストール](../../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] がインストールされるときに、MSI によって ".NET CLR" およびバージョン番号が UserAgent 文字列に追加されます。  次の例では、単純な HTML ページに埋め込まれたスクリプトを示します。  このスクリプトは、UserAgent 文字列を検索して、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] がインストールされているかどうかを判断し、検索の結果についてのステータス メッセージを表示します。  
  
> [!NOTE]
>  このスクリプトは Internet Explorer 向けです。  他のブラウザーでは、UserAgent 文字列に .NET CLR の情報は含まれません。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 ".NET CLR " バージョンが検出された場合は、次のようなステータス メッセージが表示されます。  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 それ以外の場合は、次のようなステータス メッセージが表示されます。  
  
 `This machine does not have the correct version of the .NET Framework 3.5.  The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## 参照  
 [.NET Framework 3.0 がインストールされているかどうかの確認](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)