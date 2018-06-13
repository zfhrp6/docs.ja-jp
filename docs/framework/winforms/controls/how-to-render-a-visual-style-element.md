---
title: '方法 : visual スタイル要素を描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 284fca2d3f2b8f47b60e4d9c639df4a6bd43c701
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537623"
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="b28fd-102">方法 : visual スタイル要素を描画する</span><span class="sxs-lookup"><span data-stu-id="b28fd-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="b28fd-103"><xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間を公開<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>Windows ユーザーを表すオブジェクト インターフェイス (UI) 要素の視覚スタイルでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b28fd-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="b28fd-104">このトピックを使用する方法を示します、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>をレンダリングする、<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>を表す、**ログオフ**と**シャット ダウン**[スタート] メニューのボタンです。</span><span class="sxs-lookup"><span data-stu-id="b28fd-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="b28fd-105">Visual スタイル要素を表示するには</span><span class="sxs-lookup"><span data-stu-id="b28fd-105">To render a visual style element</span></span>  
  
1.  <span data-ttu-id="b28fd-106">作成、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>を描画する要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="b28fd-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="b28fd-107">使用に注意してください、<xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType>プロパティおよび<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType>メソッド以外の場合は、 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> visual スタイルが無効になっているか、要素が定義されていない場合にコンス トラクターが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b28fd-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  <span data-ttu-id="b28fd-108">呼び出す、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A>メソッドを要素のレンダリング、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>現在を表します。</span><span class="sxs-lookup"><span data-stu-id="b28fd-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b28fd-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b28fd-109">Compiling the Code</span></span>  
 <span data-ttu-id="b28fd-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b28fd-110">This example requires:</span></span>  
  
-   <span data-ttu-id="b28fd-111">派生したカスタム コントロール、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b28fd-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="b28fd-112">A<xref:System.Windows.Forms.Form>カスタム コントロールをホストします。</span><span class="sxs-lookup"><span data-stu-id="b28fd-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="b28fd-113">参照、 <xref:System?displayProperty=nameWithType>、 <xref:System.Drawing?displayProperty=nameWithType>、 <xref:System.Windows.Forms?displayProperty=nameWithType>、および<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="b28fd-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28fd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b28fd-114">See Also</span></span>  
 [<span data-ttu-id="b28fd-115">visual スタイルが使用されているコントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="b28fd-115">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
