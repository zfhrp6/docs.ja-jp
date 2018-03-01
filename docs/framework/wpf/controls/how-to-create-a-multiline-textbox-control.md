---
title: "方法 : 複数行の TextBox コントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a6885a594e5fcd747f85dedf1afbd39ec644717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="1b39c-102">方法 : 複数行の TextBox コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="1b39c-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="1b39c-103">この例を使用する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張するコントロール。</span><span class="sxs-lookup"><span data-stu-id="1b39c-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b39c-104">例</span><span class="sxs-lookup"><span data-stu-id="1b39c-104">Example</span></span>  
 <span data-ttu-id="1b39c-105">設定、<xref:System.Windows.Controls.TextBox.TextWrapping%2A>属性を**ラップ**入力したテキストを新しいをラップすると、行の端、<xref:System.Windows.Controls.TextBox>コントロールに達すると、自動的に拡大、<xref:System.Windows.Controls.TextBox>の場合、新しい行の領域を確保するコントロールいる。</span><span class="sxs-lookup"><span data-stu-id="1b39c-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="1b39c-106">設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>属性を**true** RETURN キーを押すと、自動的にもう一度拡張に挿入される新しい行をにより、<xref:System.Windows.Controls.TextBox>に必要な場合、新しい行のスペースを含めます。</span><span class="sxs-lookup"><span data-stu-id="1b39c-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="1b39c-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>属性によって、スクロール バーを表示、追加、<xref:System.Windows.Controls.TextBox>いるための内容、<xref:System.Windows.Controls.TextBox>できますスクロールできる場合は、<xref:System.Windows.Controls.TextBox>フレームまたはそれを囲むウィンドウのサイズよりも大ききます。</span><span class="sxs-lookup"><span data-stu-id="1b39c-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="1b39c-108">参照</span><span class="sxs-lookup"><span data-stu-id="1b39c-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="1b39c-109">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="1b39c-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="1b39c-110">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="1b39c-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
