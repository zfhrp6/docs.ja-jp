---
title: "UI オートメーションを使用したテキストのスキャン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5b3d08c0a6293b6621d9b6debfa4d63c8abaf3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="7a644-102">UI オートメーションを使用したテキストのスキャン</span><span class="sxs-lookup"><span data-stu-id="7a644-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="7a644-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="7a644-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7a644-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7a644-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7a644-105">このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、 <xref:System.Windows.Automation.Text.TextUnit> ずつインクリメントしながらドキュメントのテキスト コンテンツを走査する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7a644-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a644-106">例</span><span class="sxs-lookup"><span data-stu-id="7a644-106">Example</span></span>  
 <span data-ttu-id="7a644-107">次のコード例では、UI オートメーション テキスト プロバイダーのコンテンツを走査する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a644-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="7a644-108"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> メソッドは、 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> の <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> エンドポイントと <xref:System.Windows.Automation.Text.TextPatternRange>エンドポイントを移動させます。</span><span class="sxs-lookup"><span data-stu-id="7a644-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="7a644-109">このテキスト範囲は、通常、テキスト挿入ポイントを表す低次元テキスト範囲です。</span><span class="sxs-lookup"><span data-stu-id="7a644-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a644-110">テキスト ベースの埋め込みオブジェクトのみがテキスト ストリームの一部と見なされるため、イメージなどの埋め込みオブジェクトは、 `Move` またはその戻り値に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="7a644-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="7a644-111">指定した <xref:System.Windows.Automation.Text.TextUnit> をコントロールがサポートしない場合、 <xref:System.Windows.Automation.Text.TextUnit> を使用するすべてのメソッドは、サポートされる次に大きい <xref:System.Windows.Automation.Text.TextUnit> を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a644-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a644-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a644-112">See Also</span></span>  
 [<span data-ttu-id="7a644-113">UI オートメーション TextPattern の概要</span><span class="sxs-lookup"><span data-stu-id="7a644-113">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="7a644-114">UI オートメーションを使用してテキスト ボックスにコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a644-114">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="7a644-115">検索し、UI オートメーションを使用してテキストを強調表示</span><span class="sxs-lookup"><span data-stu-id="7a644-115">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="7a644-116">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="7a644-116">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="7a644-117">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="7a644-117">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
