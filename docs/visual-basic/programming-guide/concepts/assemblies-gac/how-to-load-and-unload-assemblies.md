---
title: '方法: ロードおよびアンロード アセンブリ (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 1cec7a7e15843874b65cf5d2f3a23b8e644a26d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="4e561-102">方法: ロードおよびアンロード アセンブリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e561-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="4e561-103">プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="4e561-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="4e561-104">詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e561-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="4e561-105">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e561-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="4e561-106">アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。</span><span class="sxs-lookup"><span data-stu-id="4e561-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="4e561-107">一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="4e561-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="4e561-108">詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e561-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="4e561-109">アセンブリをアプリケーション ドメインに読み込むには</span><span class="sxs-lookup"><span data-stu-id="4e561-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="4e561-110"><xref:System.AppDomain> クラスと <xref:System.Reflection> クラスに含まれるいくつかの load メソッドの 1 つを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e561-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="4e561-111">詳細については、「[方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e561-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="4e561-112">アプリケーション ドメインをアンロードするには</span><span class="sxs-lookup"><span data-stu-id="4e561-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="4e561-113">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e561-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="4e561-114">`Unload` の <xref:System.AppDomain> メソッドを使用してアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="4e561-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="4e561-115">詳細については、「[方法: アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e561-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e561-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e561-116">See Also</span></span>  
 [<span data-ttu-id="4e561-117">プログラミングの概念</span><span class="sxs-lookup"><span data-stu-id="4e561-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="4e561-118">アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e561-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4e561-119">方法: アプリケーション ドメインにアセンブリを読み込む</span><span class="sxs-lookup"><span data-stu-id="4e561-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
