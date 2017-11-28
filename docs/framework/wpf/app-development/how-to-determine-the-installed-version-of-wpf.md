---
title: "方法: インストールされている WPF のバージョンを確認する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60f2dd65702a5dfcff4cbafa97e5a48080b8e5be
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="0ab12-102">方法: インストールされている WPF のバージョンを確認する</span><span class="sxs-lookup"><span data-stu-id="0ab12-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="0ab12-103">現在インストールされているバージョンのバージョン番号[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]内にある、**レジストリ**です。</span><span class="sxs-lookup"><span data-stu-id="0ab12-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="0ab12-104">バージョン番号を検索するには。</span><span class="sxs-lookup"><span data-stu-id="0ab12-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="0ab12-105">**[スタート]** メニューで、 **[ファイル名を指定して実行]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0ab12-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="0ab12-106">**開く**、型**regedit.exe**です。</span><span class="sxs-lookup"><span data-stu-id="0ab12-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="0ab12-107">次のキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0ab12-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="0ab12-108">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にバージョン番号が格納されている、**バージョン**値。</span><span class="sxs-lookup"><span data-stu-id="0ab12-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
