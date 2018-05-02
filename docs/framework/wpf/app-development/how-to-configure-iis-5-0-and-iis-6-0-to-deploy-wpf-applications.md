---
title: '方法 : WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する'
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
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1b03cf39608566ed80e2288204480e77994ad7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="35e53-102">方法 : WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する</span><span class="sxs-lookup"><span data-stu-id="35e53-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>
<span data-ttu-id="35e53-103">適切な [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] タイプを使用して構成されている限り、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションは、ほとんどの Web サーバーから配置することができます。</span><span class="sxs-lookup"><span data-stu-id="35e53-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="35e53-104">既定では、[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] は、これらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを使用して構成されますが、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] および [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] は違います。</span><span class="sxs-lookup"><span data-stu-id="35e53-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>  
  
 <span data-ttu-id="35e53-105">このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを配置するように、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] および [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="35e53-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  
  
  
> [!NOTE]
>  <span data-ttu-id="35e53-106">レジストリ内の *UserAgent* 文字列を確認して、システムに [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="35e53-106">You can check the *UserAgent* string in the registry to determine whether a system has [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] installed.</span></span> <span data-ttu-id="35e53-107">*UserAgent* 文字列を調べて、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がシステムにインストールされているかどうかを確認するスクリプトについては、「[.NET Framework 3.0 がインストールされているかどうかを確認する](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35e53-107">For details and a script that examines the *UserAgent* string to determine whether [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="35e53-108">コンテンツの有効期限の設定を調整する</span><span class="sxs-lookup"><span data-stu-id="35e53-108">Adjust the Content Expiration Setting</span></span>  
 <span data-ttu-id="35e53-109">コンテンツの有効期限の設定を 1 分に調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35e53-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="35e53-110">次の手順は、[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] でこれを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="35e53-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>  
  
1.  <span data-ttu-id="35e53-111">**[スタート]** メニューをクリックして、**[管理ツール]** をポイントして、**[インターネット インフォメーション サービス (IIS) マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35e53-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="35e53-112">コマンド ラインで「SystemRoot%\system32\inetsrv\iis.msc %」と入力して、このアプリケーションを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="35e53-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>  
  
2.  <span data-ttu-id="35e53-113">**[Default Web Site]** ノードが見つかるまで、[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="35e53-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>  
  
3.  <span data-ttu-id="35e53-114">**[Default Web Site]** を右クリックし、コンテキスト メニューの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="35e53-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>  
  
4.  <span data-ttu-id="35e53-115">**[HTTP ヘッダー]** タブを選択し、[コンテンツの有効期限を有効にする をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35e53-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>  
  
5.  <span data-ttu-id="35e53-116">1 分後に期限切れになるようにコンテンツを設定します。</span><span class="sxs-lookup"><span data-stu-id="35e53-116">Set the content to expire after 1 minute.</span></span>  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="35e53-117">MIME タイプとファイル拡張子を登録する</span><span class="sxs-lookup"><span data-stu-id="35e53-117">Register MIME Types and File Extensions</span></span>  
 <span data-ttu-id="35e53-118">クライアント システムのブラウザーで適切なハンドラーを読み込めるように、いくつかの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35e53-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="35e53-119">次のタイプを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35e53-119">You need to add the following types:</span></span>  
  
|<span data-ttu-id="35e53-120">拡張子</span><span class="sxs-lookup"><span data-stu-id="35e53-120">Extension</span></span>|<span data-ttu-id="35e53-121">[MIME の種類]</span><span class="sxs-lookup"><span data-stu-id="35e53-121">MIME Type</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="35e53-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="35e53-122">.manifest</span></span>|<span data-ttu-id="35e53-123">application/manifest</span><span class="sxs-lookup"><span data-stu-id="35e53-123">application/manifest</span></span>|  
|<span data-ttu-id="35e53-124">.xaml</span><span class="sxs-lookup"><span data-stu-id="35e53-124">.xaml</span></span>|<span data-ttu-id="35e53-125">application/xaml+xml</span><span class="sxs-lookup"><span data-stu-id="35e53-125">application/xaml+xml</span></span>|  
|<span data-ttu-id="35e53-126">.application</span><span class="sxs-lookup"><span data-stu-id="35e53-126">.application</span></span>|<span data-ttu-id="35e53-127">application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="35e53-127">application/x-ms-application</span></span>|  
|<span data-ttu-id="35e53-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="35e53-128">.xbap</span></span>|<span data-ttu-id="35e53-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="35e53-129">application/x-ms-xbap</span></span>|  
|<span data-ttu-id="35e53-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="35e53-130">.deploy</span></span>|<span data-ttu-id="35e53-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="35e53-131">application/octet-stream</span></span>|  
|<span data-ttu-id="35e53-132">.xps</span><span class="sxs-lookup"><span data-stu-id="35e53-132">.xps</span></span>|<span data-ttu-id="35e53-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="35e53-133">application/vnd.ms-xpsdocument</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="35e53-134">クライアント システムに [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプとファイル拡張子を登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35e53-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="35e53-135">Microsoft .NET Framework をインストールするときに、自動的に登録します。</span><span class="sxs-lookup"><span data-stu-id="35e53-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>  
  
 <span data-ttu-id="35e53-136">次の Microsoft Visual Basic Scripting Edition (VBScript) サンプルは、必要なを自動的に追加[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]型を[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="35e53-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="35e53-137">スクリプトを使用するには、サーバー上の .vbs ファイルにこのコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="35e53-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="35e53-138">その後、コマンド ラインからファイルを実行するか、[!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] でファイルをダブルクリックして、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="35e53-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="35e53-139">このスクリプトを複数回実行すると、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに複数の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] マップ エントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="35e53-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
 <span data-ttu-id="35e53-140">このスクリプトを実行しても、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] から追加の [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを参照できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="35e53-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="35e53-141">しかし、これらの [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベースに追加されています。</span><span class="sxs-lookup"><span data-stu-id="35e53-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="35e53-142">次のスクリプトは、[!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] または [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] メタベース内のすべての [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] タイプを表示します。</span><span class="sxs-lookup"><span data-stu-id="35e53-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 <span data-ttu-id="35e53-143">スクリプトを `.vbs` ファイルとして保存し (たとえば、`DiscoverIISMimeTypes.vbs`)、次のコマンドを使用して、コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="35e53-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>  
  
 `cscript DiscoverIISMimeTypes.vbs`
