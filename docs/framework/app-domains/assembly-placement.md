---
title: "アセンブリの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f5f80649e214583dae52ed8ec7933b77bf72fca5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="assembly-placement"></a><span data-ttu-id="84e0d-102">アセンブリの配置</span><span class="sxs-lookup"><span data-stu-id="84e0d-102">Assembly Placement</span></span>
<span data-ttu-id="84e0d-103">多くの .NET Framework アプリケーションの場合、アプリケーションを構成するアセンブリは、そのアプリケーションのディレクトリ、アプリケーション ディレクトリのサブディレクトリ、またはグローバル アセンブリ キャッシュ (アセンブリが共有されている場合) に配置します。</span><span class="sxs-lookup"><span data-stu-id="84e0d-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="84e0d-104">構成ファイルの [\<codeBase> エレメント](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)を使用すると、共通言語ランタイムがアセンブリを検索する場所をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="84e0d-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="84e0d-105">アセンブリが厳密な名前を持たない場合、[\<codeBase> エレメント](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)を使用して指定できる場所は、そのアプリケーションのディレクトリまたはサブディレクトリに制限されます。</span><span class="sxs-lookup"><span data-stu-id="84e0d-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="84e0d-106">アセンブリが厳密な名前を持つ場合は、[\<codeBase> エレメント](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)を使用してコンピューターまたはネットワーク上の任意の場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="84e0d-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="84e0d-107">また、アンマネージ コード アプリケーションや COM 相互運用アプリケーションで使用するアセンブリを検索する場所についても似たような規則が適用されます。アセンブリを複数のアプリケーションで共有する場合、そのアセンブリの検索場所はグローバル アセンブリ キャッシュになります。</span><span class="sxs-lookup"><span data-stu-id="84e0d-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="84e0d-108">アンマネージ コードで使用するアセンブリは、型ライブラリとしてエクスポートし、登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84e0d-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="84e0d-109">COM 相互運用で使用するアセンブリは、カタログに登録する必要がありますが、場合によっては、この登録が自動的に行われることもあります。</span><span class="sxs-lookup"><span data-stu-id="84e0d-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e0d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="84e0d-110">See Also</span></span>  
 <span data-ttu-id="84e0d-111">[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="84e0d-111">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 <span data-ttu-id="84e0d-112">[アプリの構成](../../../docs/framework/configure-apps/index.md) </span><span class="sxs-lookup"><span data-stu-id="84e0d-112">[Configuring Apps](../../../docs/framework/configure-apps/index.md) </span></span>  
 <span data-ttu-id="84e0d-113">[高度な COM 相互運用性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb) </span><span class="sxs-lookup"><span data-stu-id="84e0d-113">[Advanced COM Interoperability](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb) </span></span>  
 [<span data-ttu-id="84e0d-114">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="84e0d-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)

