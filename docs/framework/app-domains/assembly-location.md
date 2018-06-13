---
title: アセンブリの場所
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91fc7cf6ea66952fa5770ce73ecb1a8c129a9a2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743915"
---
# <a name="assembly-location"></a><span data-ttu-id="20912-102">アセンブリの場所</span><span class="sxs-lookup"><span data-stu-id="20912-102">Assembly Location</span></span>
<span data-ttu-id="20912-103">アセンブリの場所は、参照時に共通言語ランタイムがそれを見つけることができるかどうかを決定します。また、アセンブリをその他のアセンブリと共有できるかどうかも決定できます。</span><span class="sxs-lookup"><span data-stu-id="20912-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="20912-104">次の場所にアセンブリを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="20912-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="20912-105">アプリケーションのディレクトリまたはサブディレクトリ</span><span class="sxs-lookup"><span data-stu-id="20912-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="20912-106">これは、アセンブリを展開する最も一般的な場所です。</span><span class="sxs-lookup"><span data-stu-id="20912-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="20912-107">アプリケーションのルート ディレクトリのサブディレクトリは、言語またはカルチャを基にすることができます。</span><span class="sxs-lookup"><span data-stu-id="20912-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="20912-108">アセンブリにカルチャ属性の情報がある場合は、アプリケーション ディレクトリの下のサブディレクトリに、そのカルチャの名前で存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20912-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="20912-109">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="20912-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="20912-110">これは、共通言語ランタイムをインストールしている場所にインストールされている、コンピューター全体で使用できるコード キャッシュです。</span><span class="sxs-lookup"><span data-stu-id="20912-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="20912-111">ほとんどの場合、あるアセンブリを複数のアプリケーションで共有する場合は、そのアセンブリをグローバル アセンブリ キャッシュ内に展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20912-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="20912-112">HTTP サーバー上</span><span class="sxs-lookup"><span data-stu-id="20912-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="20912-113">HTTP サーバーに展開されているアセンブリは、厳密な名前を持つ必要があります。アプリケーションの構成ファイルのコードベース セクションにあるアセンブリをポイントします。</span><span class="sxs-lookup"><span data-stu-id="20912-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20912-114">参照</span><span class="sxs-lookup"><span data-stu-id="20912-114">See Also</span></span>  
 [<span data-ttu-id="20912-115">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="20912-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="20912-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="20912-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="20912-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="20912-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="20912-118">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="20912-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
