---
title: "方法 : アプリケーション ドメインを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f8d791a7aa673c25104e5dddf018d4b167563ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="46ca9-102">方法 : アプリケーション ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="46ca9-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="46ca9-103">共通言語ランタイム ホストにより、必要なときに、アプリケーション ドメインが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="46ca9-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="46ca9-104">ただし、独自のアプリケーション ドメインを作成し、個人的に管理するアセンブリにそれを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="46ca9-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="46ca9-105">アプリケーション ドメインを作成し、そこからコードを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="46ca9-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="46ca9-106"><xref:System.AppDomain?displayProperty=nameWithType> クラスのオーバーロードされた **CreateDomain** メソッドの 1 つを利用し、新しいアプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="46ca9-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="46ca9-107">アプリケーション ドメインに名前を付け、その名前で参照できます。</span><span class="sxs-lookup"><span data-stu-id="46ca9-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="46ca9-108">次の例では、新しいアプリケーション ドメインを作成し、それに `MyDomain` という名前を割り当て、ホスト ドメインの名前と新しく作成された子アプリケーション ドメインがコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="46ca9-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ca9-109">例</span><span class="sxs-lookup"><span data-stu-id="46ca9-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="46ca9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="46ca9-110">See Also</span></span>  
 [<span data-ttu-id="46ca9-111">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="46ca9-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="46ca9-112">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="46ca9-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
