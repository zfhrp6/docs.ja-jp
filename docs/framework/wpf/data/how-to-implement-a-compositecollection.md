---
title: "方法 : CompositeCollection を実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b33e3a61b91c2f9e2362a270216038d61770b815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="c51a9-102">方法 : CompositeCollection を実装する</span><span class="sxs-lookup"><span data-stu-id="c51a9-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="c51a9-103">例</span><span class="sxs-lookup"><span data-stu-id="c51a9-103">Example</span></span>  
 <span data-ttu-id="c51a9-104">次の例として、1 つのリストを使用して複数のコレクションと、項目を表示する方法を示しています、<xref:System.Windows.Data.CompositeCollection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="c51a9-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="c51a9-105">この例では`GreekGods`は、<xref:System.Collections.ObjectModel.ObservableCollection%601>の`GreekGod`カスタム オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c51a9-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="c51a9-106">データ テンプレートが定義されているように`GreekGod`オブジェクトおよび`GreekHero`オブジェクトはそれぞれ、gold およびシアン前景の色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c51a9-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c51a9-107">参照</span><span class="sxs-lookup"><span data-stu-id="c51a9-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="c51a9-108">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="c51a9-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c51a9-109">方法トピック</span><span class="sxs-lookup"><span data-stu-id="c51a9-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
