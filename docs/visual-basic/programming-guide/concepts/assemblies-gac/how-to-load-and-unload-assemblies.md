---
title: "方法: ロード テストとアンロード アセンブリ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2e38be72bb58573b532fa42a569563df0be8301d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="0050c-102">方法: ロード テストとアンロード アセンブリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0050c-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="0050c-103">プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="0050c-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="0050c-104">詳細については、次を参照してください。[方法: アプリケーション ドメインにアセンブリをロード](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)します。</span><span class="sxs-lookup"><span data-stu-id="0050c-104">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
 <span data-ttu-id="0050c-105">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0050c-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="0050c-106">アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。</span><span class="sxs-lookup"><span data-stu-id="0050c-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="0050c-107">一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="0050c-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="0050c-108">詳細については、次を参照してください。[方法: アプリケーション ドメインをアンロード](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)します。</span><span class="sxs-lookup"><span data-stu-id="0050c-108">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="0050c-109">アセンブリをアプリケーション ドメインに読み込むには</span><span class="sxs-lookup"><span data-stu-id="0050c-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="0050c-110">クラス<xref:System.AppDomain>と<xref:System.Reflection></xref:System.Reflection></xref:System.AppDomain>に含まれているいくつかの load メソッドのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="0050c-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="0050c-111">詳細については、次を参照してください。[方法: アプリケーション ドメインにアセンブリをロード](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)します。</span><span class="sxs-lookup"><span data-stu-id="0050c-111">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="0050c-112">アプリケーション ドメインをアンロードするには</span><span class="sxs-lookup"><span data-stu-id="0050c-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="0050c-113">個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0050c-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="0050c-114">使用して、`Unload`メソッドから<xref:System.AppDomain>アプリケーション ドメインをアンロードします</xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="0050c-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="0050c-115">詳細については、次を参照してください。[方法: アプリケーション ドメインをアンロード](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192)します。</span><span class="sxs-lookup"><span data-stu-id="0050c-115">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0050c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0050c-116">See Also</span></span>  
 <span data-ttu-id="0050c-117">[プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="0050c-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="0050c-118"> [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="0050c-118"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="0050c-119"> [方法: アプリケーション ドメインにアセンブリを読み込む](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span><span class="sxs-lookup"><span data-stu-id="0050c-119"> [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span></span>
