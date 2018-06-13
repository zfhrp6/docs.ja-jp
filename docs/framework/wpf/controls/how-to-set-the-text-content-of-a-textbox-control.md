---
title: '方法 : TextBox コントロールのテキスト コンテンツを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 37d636a5e35e9c52ca35ae558b60b5f32d63cabe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551727"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="f7228-102">方法 : TextBox コントロールのテキスト コンテンツを設定する</span><span class="sxs-lookup"><span data-stu-id="f7228-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="f7228-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.TextBox.Text%2A>の最初のテキスト内容を設定するプロパティ、<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f7228-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="f7228-104">**注**ですが、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]バージョンの例を使用、`<TextBox.Text>`の各ボタンのテキスト タグで囲みます<xref:System.Windows.Controls.TextBox>コンテンツの必要はありませんので、<xref:System.Windows.Controls.TextBox>適用、<xref:System.Windows.Markup.ContentPropertyAttribute>属性を<xref:System.Windows.Controls.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f7228-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="f7228-105">詳細については、次を参照してください。 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7228-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7228-106">例</span><span class="sxs-lookup"><span data-stu-id="f7228-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="f7228-107">例</span><span class="sxs-lookup"><span data-stu-id="f7228-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="f7228-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7228-108">See Also</span></span>  
 [<span data-ttu-id="f7228-109">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="f7228-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="f7228-110">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="f7228-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
