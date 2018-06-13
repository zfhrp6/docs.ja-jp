---
title: UI オートメーションを使用した、テキストの検索と強調表示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2fe7ecd84c6b88e6ccc81188235a6735b926a04b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401087"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="3c401-102">UI オートメーションを使用した、テキストの検索と強調表示</span><span class="sxs-lookup"><span data-stu-id="3c401-102">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="3c401-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="3c401-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3c401-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c401-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3c401-105">このトピックを順番に検索し、文字列を使用してテキスト コントロールのコンテンツ内の各出現する位置を強調表示方法を示します[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3c401-105">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c401-106">例</span><span class="sxs-lookup"><span data-stu-id="3c401-106">Example</span></span>  
 <span data-ttu-id="3c401-107">次の例では取得、<xref:System.Windows.Automation.TextPattern>テキスト コントロールからのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3c401-107">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="3c401-108">A<xref:System.Windows.Automation.Text.TextPatternRange>全体のドキュメントのテキスト コンテンツを表す、オブジェクトを使用して作成し、<xref:System.Windows.Automation.TextPattern.DocumentRange%2A>このプロパティ<xref:System.Windows.Automation.TextPattern>です。</span><span class="sxs-lookup"><span data-stu-id="3c401-108">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="3c401-109">2 つ追加<xref:System.Windows.Automation.Text.TextPatternRange>オブジェクトが順番に検索するには、作成、および機能を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3c401-109">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="3c401-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c401-110">See Also</span></span>  
 [<span data-ttu-id="3c401-111">UI オートメーションを使用した、テキストの検索と強調表示</span><span class="sxs-lookup"><span data-stu-id="3c401-111">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
