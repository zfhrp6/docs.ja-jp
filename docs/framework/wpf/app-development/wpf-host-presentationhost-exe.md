---
title: "WPF ホスト (PresentationHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c5a9df438353701932a3e732d6df28b08402ee8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="8c2e6-102">WPF ホスト (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="8c2e6-102">WPF Host (PresentationHost.exe)</span></span>
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]<span data-ttu-id="8c2e6-103"> ホスト (PresentationHost.exe) は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを互換ブラウザー ([!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] 以降を含む) でホスト可能にするアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-103"> Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="8c2e6-104">既定では、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、ブラウザーによってホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツのシェルと [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] ハンドラーとして登録されます。該当するコンテンツには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-104">By default, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="8c2e6-105">Loose (コンパイルされていない) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル (.xaml)。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]<span data-ttu-id="8c2e6-106"> (.xbap)。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-106"> (.xbap).</span></span>  
  
 <span data-ttu-id="8c2e6-107">これらの種類のファイルに対して、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ホストは、次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-107">For files of these types, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host:</span></span>  
  
-   <span data-ttu-id="8c2e6-108">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] コンテンツをホストするために、登録されている [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ハンドラーを起動します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] content.</span></span>  
  
-   <span data-ttu-id="8c2e6-109">必要な [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] と [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アセンブリの正しいバージョンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] assemblies.</span></span>  
  
-   <span data-ttu-id="8c2e6-110">展開のゾーンに適切なアクセス許可レベルが設定されるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="8c2e6-111">このトピックでは、PresentationHost.exe で使用できるコマンド ライン パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="8c2e6-112">使用方法</span><span class="sxs-lookup"><span data-stu-id="8c2e6-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="8c2e6-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c2e6-113">Parameters</span></span>  
  
|<span data-ttu-id="8c2e6-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c2e6-114">Parameter</span></span>|<span data-ttu-id="8c2e6-115">説明</span><span class="sxs-lookup"><span data-stu-id="8c2e6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c2e6-116">ファイル名</span><span class="sxs-lookup"><span data-stu-id="8c2e6-116">filename</span></span>|<span data-ttu-id="8c2e6-117">アクティブにするファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-117">The path of the file to be activated.</span></span> <span data-ttu-id="8c2e6-118">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] も指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="8c2e6-119">-debug</span><span class="sxs-lookup"><span data-stu-id="8c2e6-119">-debug</span></span>|<span data-ttu-id="8c2e6-120">アプリケーションをアクティブにする場合に、このアプリケーションをストアにコミットしたり、ストアから実行しません。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="8c2e6-121">これは、ローカル ファイルをアクティブにする場合に限って使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="8c2e6-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="8c2e6-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="8c2e6-123">アプリケーションを、指定した [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] から展開されたものとしてデバッグする必要があることを PresentationHost.exe に指示するために、[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] 値と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="8c2e6-124">これは、展開ゾーンと起点サイトの両方を決定します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="8c2e6-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="8c2e6-125">-embedding</span></span>|<span data-ttu-id="8c2e6-126">OLE で必要になります。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-126">Required by OLE.</span></span> <span data-ttu-id="8c2e6-127">`-event` パラメーターまたは `-debug` パラメーターを指定した場合、`-embedding` パラメーターは内部で設定されるため、指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="8c2e6-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="8c2e6-128">-event \<eventname></span></span>|<span data-ttu-id="8c2e6-129">PresentationHost.exe が初期化され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] コンテンツをホストする準備ができた時点で、この名前のイベントを開き、シグナルを送信します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="8c2e6-130">PresentationHost.exe は、イベントを開く際にエラーが発生すると (そのイベントがまだ作成されていない場合など) 終了します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="8c2e6-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="8c2e6-131">-launchApplication \<url></span></span>|<span data-ttu-id="8c2e6-132">指定した URL から、スタンドアロンの [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> <span data-ttu-id="8c2e6-133">.NET アプリケーションに関する [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] と WinINet のセキュリティ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="8c2e6-133">[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="8c2e6-134">シナリオ</span><span class="sxs-lookup"><span data-stu-id="8c2e6-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="8c2e6-135">シェル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="8c2e6-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="8c2e6-136">MIME ハンドラー</span><span class="sxs-lookup"><span data-stu-id="8c2e6-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="8c2e6-137">Visual Studio によるデバッグ</span><span class="sxs-lookup"><span data-stu-id="8c2e6-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="8c2e6-138">Visual Studio によるゾーンでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="8c2e6-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="8c2e6-139">参照</span><span class="sxs-lookup"><span data-stu-id="8c2e6-139">See Also</span></span>  
 [<span data-ttu-id="8c2e6-140">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="8c2e6-140">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
