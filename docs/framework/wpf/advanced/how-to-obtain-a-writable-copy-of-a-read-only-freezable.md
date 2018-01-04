---
title: "方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する"
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
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe22e49ee28de60bc76d7a4f543462bbcfac48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="09908-102">方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する</span><span class="sxs-lookup"><span data-stu-id="09908-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="09908-103">この例を使用する方法を示しています、<xref:System.Windows.Freezable.Clone%2A>読み取り専用の書き込み可能なコピーを作成するメソッド<xref:System.Windows.Freezable>です。</span><span class="sxs-lookup"><span data-stu-id="09908-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="09908-104">後に、<xref:System.Windows.Freezable>オブジェクトがマークされている読み取り専用 ("凍結"した)、として、それを変更できません。</span><span class="sxs-lookup"><span data-stu-id="09908-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="09908-105">ただし、使用することができます、<xref:System.Windows.Freezable.Clone%2A>固定されたオブジェクトの変更可能な複製を作成します。</span><span class="sxs-lookup"><span data-stu-id="09908-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09908-106">例</span><span class="sxs-lookup"><span data-stu-id="09908-106">Example</span></span>  
 <span data-ttu-id="09908-107">次の例は、固定の変更可能な複製を作成<xref:System.Windows.Media.SolidColorBrush>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="09908-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="09908-108">詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="09908-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09908-109">参照</span><span class="sxs-lookup"><span data-stu-id="09908-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [<span data-ttu-id="09908-110">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="09908-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="09908-111">方法トピック</span><span class="sxs-lookup"><span data-stu-id="09908-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
