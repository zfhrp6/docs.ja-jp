---
title: "UI オートメーションを使用した、埋め込みオブジェクトへのアクセス"
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
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0f417acd3440c224db06ca4034c23a1cd6eb395e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="40f8e-102">UI オートメーションを使用した、埋め込みオブジェクトへのアクセス</span><span class="sxs-lookup"><span data-stu-id="40f8e-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="40f8e-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="40f8e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="40f8e-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40f8e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="40f8e-105">このトピックでは、どのように [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、テキスト コントロールのコンテンツ内に埋め込みオブジェクトを公開できるのかを示しています。</span><span class="sxs-lookup"><span data-stu-id="40f8e-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f8e-106">埋め込みオブジェクトには、イメージ、ハイパーリンク、ボタン、テーブル、ActiveX コントロールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="40f8e-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="40f8e-107">埋め込みオブジェクトは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダーの子と見なされます。</span><span class="sxs-lookup"><span data-stu-id="40f8e-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="40f8e-108">これにより、他のすべての [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 要素と同じ UI オートメーション ツリーの構造を介して公開することができます。</span><span class="sxs-lookup"><span data-stu-id="40f8e-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="40f8e-109">次に、機能は、埋め込みオブジェクトのコントロール型で通常必要とされるコントロール パターンを通じて公開されます (たとえば、ハイパーリンクはテキスト ベースであるため、 <xref:System.Windows.Automation.TextPattern>をサポートします)。</span><span class="sxs-lookup"><span data-stu-id="40f8e-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="40f8e-110">![テキスト コンテナー内の埋め込みオブジェクト。] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="40f8e-110">![Embedded objects in a text container.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="40f8e-111">サンプル ドキュメントのテキスト コンテンツ、(「ご存知でしたか。」[...])2 つの埋め込みオブジェクト (クジラとテキストのハイパーリンクの画像)、コード例については、ターゲットとして使用します。</span><span class="sxs-lookup"><span data-stu-id="40f8e-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40f8e-112">例</span><span class="sxs-lookup"><span data-stu-id="40f8e-112">Example</span></span>  
 <span data-ttu-id="40f8e-113">次のコード例は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダー内から埋め込みオブジェクトのコレクションを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="40f8e-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="40f8e-114">概要で提供されたサンプルのドキュメントについては、2 つのオブジェクトが返されます (イメージ要素と、テキスト要素)。</span><span class="sxs-lookup"><span data-stu-id="40f8e-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f8e-115">イメージ要素には、画像に関連付けられて説明する組み込みテキストが必要であり、通常は <xref:System.Windows.Automation.AutomationElement.NameProperty> 内にあります (「青いクジラ」など)。</span><span class="sxs-lookup"><span data-stu-id="40f8e-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="40f8e-116">ただし、イメージ オブジェクトにまたがるテキスト範囲を取得すると、イメージもこの説明のテキストもテキストのストリームで返されません。</span><span class="sxs-lookup"><span data-stu-id="40f8e-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="40f8e-117">例</span><span class="sxs-lookup"><span data-stu-id="40f8e-117">Example</span></span>  
 <span data-ttu-id="40f8e-118">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダー内の埋め込みオブジェクトからテキストの範囲を取得する方法を、次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="40f8e-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="40f8e-119">取得されるテキストの範囲は空の範囲です。ここで、開始エンドポイントは "…</span><span class="sxs-lookup"><span data-stu-id="40f8e-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="40f8e-120">ocean.(space)" の後に続き、終了エンドポイントは、(概要で提供した画像に示されているように) 埋め込みハイパーリンクを表す終了の "." に先行します。</span><span class="sxs-lookup"><span data-stu-id="40f8e-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="40f8e-121">これは空の範囲ですが、スパンが 0 ではないため、低次元テキスト範囲とはみなされません。</span><span class="sxs-lookup"><span data-stu-id="40f8e-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40f8e-122"><xref:System.Windows.Automation.TextPattern> はハイパーリンクなどのテキスト ベースの埋め込みオブジェクトを取得することができます。ただし、セカンダリ <xref:System.Windows.Automation.TextPattern> は完全な機能を公開するために、埋め込みオブジェクトから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40f8e-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="40f8e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="40f8e-123">See Also</span></span>  
 [<span data-ttu-id="40f8e-124">UI オートメーション TextPattern の概要</span><span class="sxs-lookup"><span data-stu-id="40f8e-124">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="40f8e-125">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="40f8e-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="40f8e-126">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="40f8e-126">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="40f8e-127">UI オートメーションを使用してテキスト ボックスにコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="40f8e-127">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="40f8e-128">検索し、UI オートメーションを使用してテキストを強調表示</span><span class="sxs-lookup"><span data-stu-id="40f8e-128">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
