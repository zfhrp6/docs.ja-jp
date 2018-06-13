---
title: UI オートメーションを使用してテキスト属性を取得する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 991c67c9407c7f020e547f97c8573762d0590502
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400017"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="aefce-102">UI オートメーションを使用してテキスト属性を取得する</span><span class="sxs-lookup"><span data-stu-id="aefce-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="aefce-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="aefce-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="aefce-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aefce-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="aefce-105">このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、テキスト範囲からテキスト属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aefce-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="aefce-106">テキスト範囲は、ドキュメント内のキャレットの現在の位置 (または低次元選択)、テキストの連続した選択、非連続のテキスト選択のコレクション、またはドキュメントのテキスト コンテンツ全体に対応します。</span><span class="sxs-lookup"><span data-stu-id="aefce-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefce-107">例</span><span class="sxs-lookup"><span data-stu-id="aefce-107">Example</span></span>  
 <span data-ttu-id="aefce-108">次のコード例は、テキスト範囲から <xref:System.Windows.Automation.TextPattern.FontNameAttribute> を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aefce-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="aefce-109"><xref:System.Windows.Automation.TextPattern> コントロール パターンは <xref:System.Windows.Automation.Text.TextPatternRange> クラスと連携して、基本のテキスト属性、プロパティ、メソッドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="aefce-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="aefce-110"><xref:System.Windows.Automation.TextPattern> または <xref:System.Windows.Automation.Text.TextPatternRange> によってサポートされないコントロール固有の機能の場合、 <xref:System.Windows.Automation.AutomationElement>クラスは対応するネイティブ オブジェクト モデルにアクセスするための UI オートメーション クライアントのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="aefce-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefce-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="aefce-111">See Also</span></span>  
 [<span data-ttu-id="aefce-112">UI オートメーション TextPattern の概要</span><span class="sxs-lookup"><span data-stu-id="aefce-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="aefce-113">UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加</span><span class="sxs-lookup"><span data-stu-id="aefce-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="aefce-114">UI オートメーションを使用した、テキストの検索と強調表示</span><span class="sxs-lookup"><span data-stu-id="aefce-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="aefce-115">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="aefce-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="aefce-116">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="aefce-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="aefce-117">UI オートメーションを使用して混合テキスト属性の詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="aefce-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
