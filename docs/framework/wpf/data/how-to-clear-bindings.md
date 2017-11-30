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
ms.openlocfilehash: 9f8e009d00960f40abcd3c3913a15fa51f1be4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="5f556-102">方法 : バインディングをクリアする</span><span class="sxs-lookup"><span data-stu-id="5f556-102">How to: Clear Bindings</span></span>
<span data-ttu-id="5f556-103">この例では、オブジェクトからバインディングをクリアする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5f556-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f556-104">例</span><span class="sxs-lookup"><span data-stu-id="5f556-104">Example</span></span>  
 <span data-ttu-id="5f556-105">オブジェクトの個々 のプロパティからバインドをクリアするには、呼び出す<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="5f556-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="5f556-106">次の例からバインドを削除する、<xref:System.Windows.Controls.TextBlock.TextProperty>の*mytext*、<xref:System.Windows.Controls.TextBlock>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5f556-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="5f556-107">バインディングをクリアすると、バイディングが削除され、依存関係プロパティの値は、バインディングが存在していなかったときの値に変更されます。</span><span class="sxs-lookup"><span data-stu-id="5f556-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="5f556-108">この値は、既定値、継承された値、データ テンプレート バインディングの値などです。</span><span class="sxs-lookup"><span data-stu-id="5f556-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="5f556-109">オブジェクトのすべてのプロパティからバインドをクリアする<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>です。</span><span class="sxs-lookup"><span data-stu-id="5f556-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f556-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f556-110">See Also</span></span>  
 <xref:System.Windows.Data.BindingOperations>  
 [<span data-ttu-id="5f556-111">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="5f556-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5f556-112">方法トピック</span><span class="sxs-lookup"><span data-stu-id="5f556-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
