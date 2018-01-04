---
title: "方法 : 要素を名前で検索する"
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a><span data-ttu-id="78cff-102">方法 : 要素を名前で検索する</span><span class="sxs-lookup"><span data-stu-id="78cff-102">How to: Find an Element by Its Name</span></span>
<span data-ttu-id="78cff-103">この例を使用する方法を説明する、<xref:System.Windows.FrameworkElement.FindName%2A>要素を検索する方法、<xref:System.Windows.FrameworkElement.Name%2A>値。</span><span class="sxs-lookup"><span data-stu-id="78cff-103">This example describes how to use the <xref:System.Windows.FrameworkElement.FindName%2A> method to find an element by its <xref:System.Windows.FrameworkElement.Name%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78cff-104">例</span><span class="sxs-lookup"><span data-stu-id="78cff-104">Example</span></span>  
 <span data-ttu-id="78cff-105">この例では、名前を使用して、特定の要素を検索するメソッドは、ボタンのイベント ハンドラーとして書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="78cff-105">In this example, the method to find a particular element by its name is written as the event handler of a button.</span></span> <span data-ttu-id="78cff-106">`stackPanel`<xref:System.Windows.FrameworkElement.Name%2A>ルートの<xref:System.Windows.FrameworkElement>検索対象を示し、メソッドの例、視覚的に、検出された要素をキャストしてとして<xref:System.Windows.Controls.TextBlock>のいずれかを変更して、<xref:System.Windows.Controls.TextBlock>表示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]プロパティです。</span><span class="sxs-lookup"><span data-stu-id="78cff-106">`stackPanel` is the <xref:System.Windows.FrameworkElement.Name%2A> of the root <xref:System.Windows.FrameworkElement> being searched, and the example method then visually indicates the found element by casting it as <xref:System.Windows.Controls.TextBlock> and changing one of the <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] properties.</span></span>  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
