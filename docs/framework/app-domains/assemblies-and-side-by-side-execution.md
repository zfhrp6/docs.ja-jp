---
title: アセンブリと side-by-side 実行
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 605cb6dfd3232d90d6c278f9563ac8d9f101b053
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="e37a4-102">アセンブリと side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="e37a4-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="e37a4-103">side-by-side 実行は、アプリケーションやコンポーネントの複数のバージョンを同じコンピューターに格納して実行する機能です。</span><span class="sxs-lookup"><span data-stu-id="e37a4-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="e37a4-104">つまり、ランタイムの複数のバージョンと、特定のバージョンのランタイムを使用するアプリケーションおよびコンポーネントの複数のバージョンを、同一コンピューター上に共存させることができます。</span><span class="sxs-lookup"><span data-stu-id="e37a4-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="e37a4-105">side-by-side 実行によって、アプリケーションをバインドするコンポーネントのバージョンや、アプリケーションが使用するランタイムのバージョンを細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="e37a4-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="e37a4-106">同じアセンブリの異なるバージョンの side-by-side ストレージにおける side-by-side 実行のサポートは、厳密な名前には不可欠の要素であり、ランタイムのインフラストラクチャに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="e37a4-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="e37a4-107">厳密な名前を持つアセンブリのバージョン番号がその識別子の一部に含まれているため、ランタイムは同じアセンブリの複数のバージョンをグローバル アセンブリ キャッシュに格納し、実行時にこれらのアセンブリを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e37a4-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="e37a4-108">ランタイムは、side-by-side 実行できるアプリケーションの作成機能を提供しますが、side-by-side 実行は自動的にサポートされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e37a4-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="e37a4-109">side-by-side 実行できるアプリケーションの作成に関する詳細については、「[Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)」 (side-by-side 実行用のコンポーネントを作成するためのガイドライン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e37a4-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37a4-110">参照</span><span class="sxs-lookup"><span data-stu-id="e37a4-110">See Also</span></span>  
 [<span data-ttu-id="e37a4-111">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="e37a4-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="e37a4-112">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="e37a4-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
