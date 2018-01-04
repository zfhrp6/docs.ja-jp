---
title: "方法 : Freezable が固定されているかどうかを判別する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eed85f982687bfc90f53e57ab1ec3949820097e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="c6267-102">方法 : Freezable が固定されているかどうかを判別する</span><span class="sxs-lookup"><span data-stu-id="c6267-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="c6267-103">この例を決める方法を説明するかどうか、<xref:System.Windows.Freezable>オブジェクトが固定されています。</span><span class="sxs-lookup"><span data-stu-id="c6267-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="c6267-104">固定された変更を行う場合<xref:System.Windows.Freezable>オブジェクトをスロー、<xref:System.InvalidOperationException>です。</span><span class="sxs-lookup"><span data-stu-id="c6267-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="c6267-105">この例外がスローされることを避けるためを使用して、<xref:System.Windows.Freezable.IsFrozen%2A>のプロパティ、<xref:System.Windows.Freezable>が固定されているかどうかを決定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c6267-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6267-106">例</span><span class="sxs-lookup"><span data-stu-id="c6267-106">Example</span></span>  
 <span data-ttu-id="c6267-107">次の例がフリーズする、<xref:System.Windows.Media.SolidColorBrush>を使用してテストし、その、<xref:System.Windows.Freezable.IsFrozen%2A>が固定されているかどうかを決定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c6267-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="c6267-108">詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6267-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6267-109">参照</span><span class="sxs-lookup"><span data-stu-id="c6267-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [<span data-ttu-id="c6267-110">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="c6267-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="c6267-111">方法トピック</span><span class="sxs-lookup"><span data-stu-id="c6267-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
