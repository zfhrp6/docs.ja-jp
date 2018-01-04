---
title: "方法 : バインディングをクリアする"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="09b1a-102">方法 : バインディングをクリアする</span><span class="sxs-lookup"><span data-stu-id="09b1a-102">How to: Clear Bindings</span></span>
<span data-ttu-id="09b1a-103">この例では、オブジェクトからバインディングをクリアする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09b1a-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b1a-104">例</span><span class="sxs-lookup"><span data-stu-id="09b1a-104">Example</span></span>  
 <span data-ttu-id="09b1a-105">オブジェクトの個々 のプロパティからバインドをクリアするには、呼び出す<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="09b1a-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="09b1a-106">次の例からバインドを削除する、<xref:System.Windows.Controls.TextBlock.TextProperty>の*mytext*、<xref:System.Windows.Controls.TextBlock>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="09b1a-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="09b1a-107">バインディングをクリアすると、バイディングが削除され、依存関係プロパティの値は、バインディングが存在していなかったときの値に変更されます。</span><span class="sxs-lookup"><span data-stu-id="09b1a-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="09b1a-108">この値は、既定値、継承された値、データ テンプレート バインディングの値などです。</span><span class="sxs-lookup"><span data-stu-id="09b1a-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="09b1a-109">オブジェクトのすべてのプロパティからバインドをクリアする<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>です。</span><span class="sxs-lookup"><span data-stu-id="09b1a-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b1a-110">参照</span><span class="sxs-lookup"><span data-stu-id="09b1a-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="09b1a-111">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="09b1a-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="09b1a-112">方法トピック</span><span class="sxs-lookup"><span data-stu-id="09b1a-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
