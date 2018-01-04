---
title: "方法 : GridLengthConverter オブジェクトを作成および使用する"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="7dd39-102">方法 : GridLengthConverter オブジェクトを作成および使用する</span><span class="sxs-lookup"><span data-stu-id="7dd39-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="7dd39-103">例</span><span class="sxs-lookup"><span data-stu-id="7dd39-103">Example</span></span>  
 <span data-ttu-id="7dd39-104">次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.GridLengthConverter>です。</span><span class="sxs-lookup"><span data-stu-id="7dd39-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="7dd39-105">例と呼ばれるカスタム メソッドを定義する`changeCol`、どのパス、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.GridLengthConverter>変換する、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.GridLength>です。</span><span class="sxs-lookup"><span data-stu-id="7dd39-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="7dd39-106">変換後の値がの値として渡されたし、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>のプロパティ、<xref:System.Windows.Controls.ColumnDefinition>要素。</span><span class="sxs-lookup"><span data-stu-id="7dd39-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="7dd39-107">例と呼ばれる 2 番目のカスタム メソッドを定義も`changeColVal`します。</span><span class="sxs-lookup"><span data-stu-id="7dd39-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="7dd39-108">このカスタム メソッドは、変換、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>の<xref:System.Windows.Controls.Slider>を<xref:System.String>と値にバックアップし、パス、<xref:System.Windows.Controls.ColumnDefinition>として、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>要素のです。</span><span class="sxs-lookup"><span data-stu-id="7dd39-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="7dd39-109">なお、個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルの内容を定義する、<xref:System.Windows.Controls.ListBoxItem>です。</span><span class="sxs-lookup"><span data-stu-id="7dd39-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd39-110">参照</span><span class="sxs-lookup"><span data-stu-id="7dd39-110">See Also</span></span>  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
