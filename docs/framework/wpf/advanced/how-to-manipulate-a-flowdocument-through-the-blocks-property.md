---
title: "方法 : Blocks プロパティを介して FlowDocument を操作する"
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
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7285d524d102158524301c2e3a9236b187097477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a><span data-ttu-id="98a6e-102">方法 : Blocks プロパティを介して FlowDocument を操作する</span><span class="sxs-lookup"><span data-stu-id="98a6e-102">How to: Manipulate a FlowDocument through the Blocks Property</span></span>
<span data-ttu-id="98a6e-103">これらの例で実行できる一般的な操作の点を示しています、<xref:System.Windows.Documents.FlowDocument>を通じて、<xref:System.Windows.Documents.FlowDocument.Blocks%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="98a6e-103">These examples demonstrate some of the more common operations that can be performed on a <xref:System.Windows.Documents.FlowDocument> through the <xref:System.Windows.Documents.FlowDocument.Blocks%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98a6e-104">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-104">Example</span></span>  
 <span data-ttu-id="98a6e-105">次の例は、新しい作成<xref:System.Windows.Documents.FlowDocument>を追加し、新しい<xref:System.Windows.Documents.Paragraph>要素を<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="98a6e-105">The following example creates a new <xref:System.Windows.Documents.FlowDocument> and then appends a new <xref:System.Windows.Documents.Paragraph> element to the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="98a6e-106">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-106">Example</span></span>  
 <span data-ttu-id="98a6e-107">次の例は、新しい作成<xref:System.Windows.Documents.Paragraph>要素の先頭に挿入し、<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="98a6e-107">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="98a6e-108">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-108">Example</span></span>  
 <span data-ttu-id="98a6e-109">次の例は、最上位レベルの数を取得<xref:System.Windows.Documents.Block>に含まれる要素の<xref:System.Windows.Documents.FlowDocument>します。</span><span class="sxs-lookup"><span data-stu-id="98a6e-109">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a><span data-ttu-id="98a6e-110">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-110">Example</span></span>  
 <span data-ttu-id="98a6e-111">次の例の最後の削除<xref:System.Windows.Documents.Block>内の要素、<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="98a6e-111">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="98a6e-112">例</span><span class="sxs-lookup"><span data-stu-id="98a6e-112">Example</span></span>  
 <span data-ttu-id="98a6e-113">次の例では、すべての内容を消去 (<xref:System.Windows.Documents.Block>要素) から、<xref:System.Windows.Documents.FlowDocument>です。</span><span class="sxs-lookup"><span data-stu-id="98a6e-113">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="98a6e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="98a6e-114">See Also</span></span>  
 [<span data-ttu-id="98a6e-115">RowGroups プロパティを介してテーブルの行グループを操作する</span><span class="sxs-lookup"><span data-stu-id="98a6e-115">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="98a6e-116">Columns プロパティによってテーブルの列を操作する</span><span class="sxs-lookup"><span data-stu-id="98a6e-116">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [<span data-ttu-id="98a6e-117">RowGroups プロパティを介してテーブルの行グループを操作する</span><span class="sxs-lookup"><span data-stu-id="98a6e-117">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
