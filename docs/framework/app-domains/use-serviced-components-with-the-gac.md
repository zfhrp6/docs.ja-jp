---
title: "サービス コンポーネントとグローバル アセンブリ キャッシュの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="7d11e-102">サービス コンポーネントとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="7d11e-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="7d11e-103">サービス コンポーネント (マネージ COM+ コンポーネント) はグローバル アセンブリ キャッシュに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d11e-103">Serviced components (managed code COM+ components) should be put in the global assembly cache.</span></span> <span data-ttu-id="7d11e-104">共通言語ランタイムと COM+ サービスは、シナリオによって、グローバル アセンブリ キャッシュに配置されていないサービス コンポーネントを処理できる場合と、処理できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d11e-104">In some scenarios, the common language runtime and COM+ Services can handle serviced components that are not in the global assembly cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="7d11e-105">これについて、次のシナリオで説明します。</span><span class="sxs-lookup"><span data-stu-id="7d11e-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="7d11e-106">COM+ サーバー アプリケーションに含まれるサービス コンポーネントの場合、コンポーネントが含まれるアセンブリがグローバル アセンブリ キャッシュに配置されている必要があります。これは、Dllhost.exe がサービス コンポーネントを格納するのと同じディレクトリで実行されないためです。</span><span class="sxs-lookup"><span data-stu-id="7d11e-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the global assembly cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="7d11e-107">COM+ ライブラリ アプリケーションに含まれるサービス コンポーネントの場合、ランタイムと COM+ サービスは、現在のディレクトリで検索することにより、コンポーネントを含むアセンブリへの参照を解決できます。</span><span class="sxs-lookup"><span data-stu-id="7d11e-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="7d11e-108">この場合、アセンブリがグローバル アセンブリ キャッシュ内に配置されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7d11e-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="7d11e-109">ASP.NET アプリケーションに含まれるサービス コンポーネントの場合、状況は異なります。</span><span class="sxs-lookup"><span data-stu-id="7d11e-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="7d11e-110">サービス コンポーネントを含むアセンブリをアプリケーション ベースの bin ディレクトリに配置し、オンデマンド登録を使用すると、アセンブリはダウンロード キャッシュにシャドウとしてコピーされます。これは、ASP.NET がランタイムのシャドウ機能を利用するためです。</span><span class="sxs-lookup"><span data-stu-id="7d11e-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d11e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d11e-111">See Also</span></span>  
 [<span data-ttu-id="7d11e-112">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="7d11e-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="7d11e-113">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="7d11e-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
