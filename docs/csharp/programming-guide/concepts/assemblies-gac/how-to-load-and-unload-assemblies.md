---
title: "方法: アセンブリを読み込み、アンロードする (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="d387d-102">方法: アセンブリを読み込み、アンロードする (C#)</span><span class="sxs-lookup"><span data-stu-id="d387d-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="d387d-103">プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="d387d-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="d387d-104">詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d387d-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="d387d-105">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d387d-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="d387d-106">アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。</span><span class="sxs-lookup"><span data-stu-id="d387d-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="d387d-107">一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d387d-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="d387d-108">詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d387d-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="d387d-109">アセンブリをアプリケーション ドメインに読み込むには</span><span class="sxs-lookup"><span data-stu-id="d387d-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="d387d-110"><xref:System.AppDomain> クラスと <xref:System.Reflection> クラスに含まれるいくつかの load メソッドの 1 つを使用します。</span><span class="sxs-lookup"><span data-stu-id="d387d-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="d387d-111">詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d387d-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="d387d-112">アプリケーション ドメインをアンロードするには</span><span class="sxs-lookup"><span data-stu-id="d387d-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="d387d-113">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d387d-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="d387d-114">`Unload` の <xref:System.AppDomain> メソッドを使用してアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="d387d-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="d387d-115">詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d387d-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d387d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d387d-116">See Also</span></span>  
 [<span data-ttu-id="d387d-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d387d-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d387d-118">アセンブリとグローバル アセンブリ キャッシュ (C#)</span><span class="sxs-lookup"><span data-stu-id="d387d-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="d387d-119">方法: アプリケーション ドメインにアセンブリを読み込む</span><span class="sxs-lookup"><span data-stu-id="d387d-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
