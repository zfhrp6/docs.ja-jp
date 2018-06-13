---
title: '方法 : 複数行の TextBox コントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553288"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="554fc-102">方法 : 複数行の TextBox コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="554fc-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="554fc-103">この例を使用する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張するコントロール。</span><span class="sxs-lookup"><span data-stu-id="554fc-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="554fc-104">例</span><span class="sxs-lookup"><span data-stu-id="554fc-104">Example</span></span>  
 <span data-ttu-id="554fc-105">設定、<xref:System.Windows.Controls.TextBox.TextWrapping%2A>属性を**ラップ**入力したテキストを新しいをラップすると、行の端、<xref:System.Windows.Controls.TextBox>コントロールに達すると、自動的に拡大、<xref:System.Windows.Controls.TextBox>の場合、新しい行の領域を確保するコントロールいる。</span><span class="sxs-lookup"><span data-stu-id="554fc-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="554fc-106">設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>属性を**true** RETURN キーを押すと、自動的にもう一度拡張に挿入される新しい行をにより、<xref:System.Windows.Controls.TextBox>に必要な場合、新しい行のスペースを含めます。</span><span class="sxs-lookup"><span data-stu-id="554fc-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="554fc-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>属性によって、スクロール バーを表示、追加、<xref:System.Windows.Controls.TextBox>いるための内容、<xref:System.Windows.Controls.TextBox>できますスクロールできる場合は、<xref:System.Windows.Controls.TextBox>フレームまたはそれを囲むウィンドウのサイズよりも大ききます。</span><span class="sxs-lookup"><span data-stu-id="554fc-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="554fc-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="554fc-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="554fc-109">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="554fc-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="554fc-110">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="554fc-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
