---
title: '方法 : アセンブリから型およびメンバーの情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fb06555f18c13f87347a5a76e6f4a3060777f02
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="741c3-102">方法 : アセンブリから型およびメンバーの情報を取得する</span><span class="sxs-lookup"><span data-stu-id="741c3-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="741c3-103"><xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="741c3-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="741c3-104">このセクションでは、これらのメソッドの 1 つを実行する例を示します。</span><span class="sxs-lookup"><span data-stu-id="741c3-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="741c3-105">詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="741c3-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="741c3-106">アセンブリから型およびメンバーの情報を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="741c3-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="741c3-107">例</span><span class="sxs-lookup"><span data-stu-id="741c3-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="741c3-108">参照</span><span class="sxs-lookup"><span data-stu-id="741c3-108">See Also</span></span>  
 <span data-ttu-id="741c3-109">[アプリケーション ドメインを使用したプログラミング](./application-domains.md#programming-with-application-domains) [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)</span><span class="sxs-lookup"><span data-stu-id="741c3-109">[Programming with Application Domains](./application-domains.md#programming-with-application-domains) [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md)</span></span>  
 [<span data-ttu-id="741c3-110">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="741c3-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
