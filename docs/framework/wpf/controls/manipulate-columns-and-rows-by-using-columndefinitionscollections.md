---
title: "方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する"
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
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e87c5001a676bcda331d289c286cf6b3e87c136f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a><span data-ttu-id="02043-102">方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する</span><span class="sxs-lookup"><span data-stu-id="02043-102">How to: Manipulate Columns and Rows by Using ColumnDefinitionsCollections and RowDefinitionsCollections</span></span>
<span data-ttu-id="02043-103">この例のメソッドを使用する方法を示しています、<xref:System.Windows.Controls.ColumnDefinitionCollection>と<xref:System.Windows.Controls.RowDefinitionCollection>クラスを追加する、オフにすると、行または列の内容のカウントなどのアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="02043-103">This example shows how to use the methods in the <xref:System.Windows.Controls.ColumnDefinitionCollection> and <xref:System.Windows.Controls.RowDefinitionCollection> classes to perform actions like adding, clearing, or counting the contents of rows or columns.</span></span> <span data-ttu-id="02043-104">たとえば、できます<xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>、 <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>、または<xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A>に含まれているアイテム、<xref:System.Windows.Controls.ColumnDefinition>または<xref:System.Windows.Controls.RowDefinition>です。</span><span class="sxs-lookup"><span data-stu-id="02043-104">For example, you can <xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>, <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>, or <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> the items that are included in a <xref:System.Windows.Controls.ColumnDefinition> or <xref:System.Windows.Controls.RowDefinition>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02043-105">例</span><span class="sxs-lookup"><span data-stu-id="02043-105">Example</span></span>  
 <span data-ttu-id="02043-106">次の例を作成、<xref:System.Windows.Controls.Grid>を持つ要素を<xref:System.Windows.FrameworkElement.Name%2A>の`grid1`します。</span><span class="sxs-lookup"><span data-stu-id="02043-106">The following example creates a <xref:System.Windows.Controls.Grid> element with a <xref:System.Windows.FrameworkElement.Name%2A> of `grid1`.</span></span> <span data-ttu-id="02043-107"><xref:System.Windows.Controls.Grid>が含まれています、<xref:System.Windows.Controls.StackPanel>を保持する<xref:System.Windows.Controls.Button>要素、それぞれ別のコレクションの方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="02043-107">The <xref:System.Windows.Controls.Grid> contains a <xref:System.Windows.Controls.StackPanel> that holds <xref:System.Windows.Controls.Button> elements, each controlled by a different collection method.</span></span> <span data-ttu-id="02043-108">クリックすると、 <xref:System.Windows.Controls.Button>、分離コード ファイル内のメソッド呼び出しがアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="02043-108">When you click a <xref:System.Windows.Controls.Button>, it activates a method call in the code-behind file.</span></span>  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="02043-109">この例は、一連のそれぞれに対応する、カスタム メソッドを定義、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>内のイベント、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。</span><span class="sxs-lookup"><span data-stu-id="02043-109">This example defines a series of custom methods, each corresponding to a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="02043-110">列と行の数を変更することができます、<xref:System.Windows.Controls.Grid>でいくつかの方法では、これには追加または行と列を削除し、行と列の合計数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="02043-110">You can change the number of columns and rows in the <xref:System.Windows.Controls.Grid> in several ways, which includes adding or removing rows and columns; and counting the total number of rows and columns.</span></span> <span data-ttu-id="02043-111">防ぐために<xref:System.ArgumentOutOfRangeException>と<xref:System.ArgumentException>例外、エラー チェック機能を使用することができますを<xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A>メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="02043-111">To prevent <xref:System.ArgumentOutOfRangeException> and <xref:System.ArgumentException> exceptions, you can use the error-checking functionality that the <xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> method provides.</span></span>  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="02043-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="02043-112">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
