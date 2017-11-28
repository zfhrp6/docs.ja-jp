---
title: "方法 : ListBox にデータをバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: deb5e05a7c48f26d0b829ba75b4ae120841e0a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="4bd29-102">方法 : ListBox にデータをバインドする</span><span class="sxs-lookup"><span data-stu-id="4bd29-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="4bd29-103">アプリケーション開発者が作成できる<xref:System.Windows.Controls.ListBox>コントロールの内容を指定しないで<xref:System.Windows.Controls.ListBoxItem>とは別にします。</span><span class="sxs-lookup"><span data-stu-id="4bd29-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="4bd29-104">データ バインディングを使用すると、個々 の項目にデータをバインドします。</span><span class="sxs-lookup"><span data-stu-id="4bd29-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="4bd29-105">次の例を作成する方法を示しています、<xref:System.Windows.Controls.ListBox>に適用する、<xref:System.Windows.Controls.ListBoxItem>要素と呼ばれるデータ ソースへのデータ バインディングによって*色*です。</span><span class="sxs-lookup"><span data-stu-id="4bd29-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="4bd29-106">ここで使用する必要はありません<xref:System.Windows.Controls.ListBoxItem>タグを各項目のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="4bd29-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd29-107">例</span><span class="sxs-lookup"><span data-stu-id="4bd29-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd29-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bd29-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="4bd29-109">コントロール</span><span class="sxs-lookup"><span data-stu-id="4bd29-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
