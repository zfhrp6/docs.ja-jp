---
title: "方法 : アセンブリから型およびメンバーの情報を取得する"
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
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 702567b7b05f8469f796b03a59f2ead71c0a9c22
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="cf8ed-102">方法 : アセンブリから型およびメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="cf8ed-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="cf8ed-103"><xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="cf8ed-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="cf8ed-104">このセクションでは、これらのメソッドの 1 つを実行する例を示します。</span><span class="sxs-lookup"><span data-stu-id="cf8ed-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="cf8ed-105">詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf8ed-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="cf8ed-106">アセンブリから型およびメンバーの情報を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cf8ed-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8ed-107">例</span><span class="sxs-lookup"><span data-stu-id="cf8ed-107">Example</span></span>  
 <span data-ttu-id="cf8ed-108">[!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)] [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)] [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]</span><span class="sxs-lookup"><span data-stu-id="cf8ed-108">[!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)] [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)] [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8ed-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf8ed-109">See Also</span></span>  
 <span data-ttu-id="cf8ed-110">[アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="cf8ed-110">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="cf8ed-111">[リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="cf8ed-111">[Reflection](../../../docs/framework/reflection-and-codedom/reflection.md) </span></span>  
 [<span data-ttu-id="cf8ed-112">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="cf8ed-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

