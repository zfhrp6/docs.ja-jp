---
title: UI オートメーションを使用したテーブルの内容の公開
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 874eada0714ed0f96248ebac8edb0efe205d9f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407184"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a><span data-ttu-id="b4b43-102">UI オートメーションを使用したテーブルの内容の公開</span><span class="sxs-lookup"><span data-stu-id="b4b43-102">Expose the Content of a Table Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="b4b43-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b4b43-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b4b43-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b43-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b4b43-105">このトピックではどのように[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]使用して表形式のコントロール内の各セルのコンテンツと組み込みのプロパティを公開することができます。</span><span class="sxs-lookup"><span data-stu-id="b4b43-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose the content and intrinsic properties of each cell within a tabular control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4b43-106">例</span><span class="sxs-lookup"><span data-stu-id="b4b43-106">Example</span></span>  
 <span data-ttu-id="b4b43-107">次のコード例を取得する方法を示しています、<xref:System.Windows.Automation.AutomationElement>テーブル セルの内容を表す; 行および列のインデックス、行と列の範囲、および行および列のヘッダー情報などのセルのプロパティも取得します。</span><span class="sxs-lookup"><span data-stu-id="b4b43-107">The following code example demonstrates how to obtain a <xref:System.Windows.Automation.AutomationElement> that represents the content of a table cell; cell properties such as row and column indices, row and column spans, and row and column header information are also obtained.</span></span> <span data-ttu-id="b4b43-108">この例では、フォーカス変更イベント ハンドラーを使用して、キーボードの走査を実装する表形式のコントロールをシミュレートする[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b4b43-108">This example uses a focus change event handler to simulate keyboard traversal of a tabular control that implements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="b4b43-109">フォーカス変更イベントには、各テーブルの項目の情報が公開します。</span><span class="sxs-lookup"><span data-stu-id="b4b43-109">Information for each table item is exposed on a focus change event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4b43-110">フォーカスの変更がグローバル デスクトップ イベントであるため、テーブルの外部のフォーカス変更イベントをフィルター処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4b43-110">Since focus changes are global desktop events, focus change events outside the table should be filtered.</span></span> <span data-ttu-id="b4b43-111">参照してください、 [TrackFocus サンプル](http://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9)関連の実装です。</span><span class="sxs-lookup"><span data-stu-id="b4b43-111">See the [TrackFocus Sample](http://msdn.microsoft.com/library/4a91c0af-6bb5-4d38-a743-cf136f268fc9) for a related implementation.</span></span>  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="b4b43-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4b43-112">See Also</span></span>  
 [<span data-ttu-id="b4b43-113">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="b4b43-113">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="b4b43-114">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="b4b43-114">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="b4b43-115">UI オートメーション Table コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="b4b43-115">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="b4b43-116">UI オートメーション TableItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="b4b43-116">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="b4b43-117">UI オートメーション Grid コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="b4b43-117">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="b4b43-118">UI オートメーション GridItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="b4b43-118">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
