---
title: '方法 : コントロールの描画クラスを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: e5b82c3317d2d162fbd5a182166a9e0061fd770e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534106"
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="87ed8-102">方法 : コントロールの描画クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="87ed8-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="87ed8-103">この例で使用する方法、<xref:System.Windows.Forms.ComboBoxRenderer>をコンボ ボックスの矢印ボックス コントロールをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="87ed8-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="87ed8-104">例から成る、<xref:System.Windows.Forms.Control.OnPaint%2A>単純なカスタム コントロールのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="87ed8-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="87ed8-105"><xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType>プロパティを使用して、アプリケーション ウィンドウのクライアント領域で visual スタイルが有効かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="87ed8-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="87ed8-106">Visual スタイルが、アクティブな場合、<xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType>メソッドは、visual スタイル; で、ドロップダウン矢印をレンダリングするそれ以外の場合、<xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType>メソッドは従来の Windows スタイルでのドロップダウン矢印を表示します。</span><span class="sxs-lookup"><span data-stu-id="87ed8-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ed8-107">例</span><span class="sxs-lookup"><span data-stu-id="87ed8-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87ed8-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="87ed8-108">Compiling the Code</span></span>  
 <span data-ttu-id="87ed8-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87ed8-109">This example requires:</span></span>  
  
-   <span data-ttu-id="87ed8-110">派生したカスタム コントロール、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="87ed8-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="87ed8-111">A<xref:System.Windows.Forms.Form>カスタム コントロールをホストします。</span><span class="sxs-lookup"><span data-stu-id="87ed8-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="87ed8-112">参照、 <xref:System?displayProperty=nameWithType>、 <xref:System.Drawing?displayProperty=nameWithType>、 <xref:System.Windows.Forms?displayProperty=nameWithType>、および<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="87ed8-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ed8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="87ed8-113">See Also</span></span>  
 [<span data-ttu-id="87ed8-114">visual スタイルが使用されているコントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="87ed8-114">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
