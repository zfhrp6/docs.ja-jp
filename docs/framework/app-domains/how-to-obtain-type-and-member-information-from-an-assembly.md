---
title: "方法 : アセンブリから型およびメンバーの情報を取得する"
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
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e488e16541d15fe876254fe2d137c8e0c22c1742
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="e4d4b-102">方法 : アセンブリから型およびメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="e4d4b-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="e4d4b-103"><xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e4d4b-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="e4d4b-104">このセクションでは、これらのメソッドの 1 つを実行する例を示します。</span><span class="sxs-lookup"><span data-stu-id="e4d4b-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="e4d4b-105">詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4d4b-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="e4d4b-106">アセンブリから型およびメンバーの情報を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e4d4b-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d4b-107">例</span><span class="sxs-lookup"><span data-stu-id="e4d4b-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="e4d4b-108">参照</span><span class="sxs-lookup"><span data-stu-id="e4d4b-108">See Also</span></span>  
 [<span data-ttu-id="e4d4b-109">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="e4d4b-109">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="e4d4b-110">リフレクション</span><span class="sxs-lookup"><span data-stu-id="e4d4b-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="e4d4b-111">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="e4d4b-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
