---
title: "方法 : 列挙値にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31fb9adbda47514e5405d465c0b5e2493b966d8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="c1834-102">方法 : 列挙値にバインドする</span><span class="sxs-lookup"><span data-stu-id="c1834-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="c1834-103">この例では、列挙体の GetValues メソッドにバインドして列挙型にバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1834-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1834-104">例</span><span class="sxs-lookup"><span data-stu-id="c1834-104">Example</span></span>  
 <span data-ttu-id="c1834-105">次の例で、<xref:System.Windows.Controls.ListBox>の一覧を表示<xref:System.Windows.HorizontalAlignment>データ バインディングを使用して列挙型値。</span><span class="sxs-lookup"><span data-stu-id="c1834-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="c1834-106"><xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>を変更するようにバインドされて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>のプロパティの値、<xref:System.Windows.Controls.Button>で値を選択して、<xref:System.Windows.Controls.ListBox>です。</span><span class="sxs-lookup"><span data-stu-id="c1834-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="c1834-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1834-107">See Also</span></span>  
 [<span data-ttu-id="c1834-108">メソッドにバインドする</span><span class="sxs-lookup"><span data-stu-id="c1834-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [<span data-ttu-id="c1834-109">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="c1834-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c1834-110">方法トピック</span><span class="sxs-lookup"><span data-stu-id="c1834-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
