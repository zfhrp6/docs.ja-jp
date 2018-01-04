---
title: "方法 : TextBox コントロールのテキスト コンテンツを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef354a986ee71cfa7a8e00a62905ee909d9cf30d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="13f67-102">方法 : TextBox コントロールのテキスト コンテンツを設定する</span><span class="sxs-lookup"><span data-stu-id="13f67-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="13f67-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.TextBox.Text%2A>の最初のテキスト内容を設定するプロパティ、<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="13f67-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="13f67-104">**注**ですが、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]バージョンの例を使用、`<TextBox.Text>`の各ボタンのテキスト タグで囲みます<xref:System.Windows.Controls.TextBox>コンテンツの必要はありませんので、<xref:System.Windows.Controls.TextBox>適用、<xref:System.Windows.Markup.ContentPropertyAttribute>属性を<xref:System.Windows.Controls.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="13f67-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="13f67-105">詳細については、次を参照してください。 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="13f67-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f67-106">例</span><span class="sxs-lookup"><span data-stu-id="13f67-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="13f67-107">例</span><span class="sxs-lookup"><span data-stu-id="13f67-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="13f67-108">参照</span><span class="sxs-lookup"><span data-stu-id="13f67-108">See Also</span></span>  
 [<span data-ttu-id="13f67-109">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="13f67-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="13f67-110">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="13f67-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
