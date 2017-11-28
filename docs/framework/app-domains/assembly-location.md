---
title: "アセンブリの場所"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e069c1636004896bfb193fd70a352195ba045865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-location"></a><span data-ttu-id="947e2-102">アセンブリの場所</span><span class="sxs-lookup"><span data-stu-id="947e2-102">Assembly Location</span></span>
<span data-ttu-id="947e2-103">アセンブリの場所は、参照時に共通言語ランタイムがそれを見つけることができるかどうかを決定します。また、アセンブリをその他のアセンブリと共有できるかどうかも決定できます。</span><span class="sxs-lookup"><span data-stu-id="947e2-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="947e2-104">次の場所にアセンブリを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="947e2-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="947e2-105">アプリケーションのディレクトリまたはサブディレクトリ</span><span class="sxs-lookup"><span data-stu-id="947e2-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="947e2-106">これは、アセンブリを展開する最も一般的な場所です。</span><span class="sxs-lookup"><span data-stu-id="947e2-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="947e2-107">アプリケーションのルート ディレクトリのサブディレクトリは、言語またはカルチャを基にすることができます。</span><span class="sxs-lookup"><span data-stu-id="947e2-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="947e2-108">アセンブリにカルチャ属性の情報がある場合は、アプリケーション ディレクトリの下のサブディレクトリに、そのカルチャの名前で存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="947e2-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="947e2-109">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="947e2-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="947e2-110">これは、共通言語ランタイムをインストールしている場所にインストールされている、コンピューター全体で使用できるコード キャッシュです。</span><span class="sxs-lookup"><span data-stu-id="947e2-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="947e2-111">ほとんどの場合、あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内に展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="947e2-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="947e2-112">HTTP サーバー上</span><span class="sxs-lookup"><span data-stu-id="947e2-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="947e2-113">HTTP サーバーに展開されているアセンブリは、厳密な名前を持つ必要があります。アプリケーションの構成ファイルのコードベース セクションにあるアセンブリをポイントします。</span><span class="sxs-lookup"><span data-stu-id="947e2-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947e2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="947e2-114">See Also</span></span>  
 [<span data-ttu-id="947e2-115">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="947e2-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="947e2-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="947e2-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="947e2-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="947e2-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="947e2-118">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="947e2-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
