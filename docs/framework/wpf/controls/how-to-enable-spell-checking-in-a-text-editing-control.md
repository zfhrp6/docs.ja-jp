---
title: "方法 : テキスト編集コントロールでスペル チェックを有効にする"
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
- spellchecking [WPF]
- real-time spellchecking
- TextBox control [WPF], real-time spellchecking
- spelling checker [WPF]
- checking spelling [WPF]
ms.assetid: 6f953d2b-67e8-4012-84ce-53c0e958da47
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e70bbe3b4d3656001af23108b2f76b40d2887318
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-spell-checking-in-a-text-editing-control"></a><span data-ttu-id="92a99-102">方法 : テキスト編集コントロールでスペル チェックを有効にする</span><span class="sxs-lookup"><span data-stu-id="92a99-102">How to: Enable Spell Checking in a Text Editing Control</span></span>
<span data-ttu-id="92a99-103">次の例は、リアルタイムでスペル チェックを有効にする方法を示しています、<xref:System.Windows.Controls.TextBox>を使用して、<xref:System.Windows.Controls.SpellCheck.IsEnabled%2A>のプロパティ、<xref:System.Windows.Controls.SpellCheck>クラスです。</span><span class="sxs-lookup"><span data-stu-id="92a99-103">The following example shows how to enable real-time spell checking in a <xref:System.Windows.Controls.TextBox> by using the <xref:System.Windows.Controls.SpellCheck.IsEnabled%2A> property of the <xref:System.Windows.Controls.SpellCheck> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92a99-104">例</span><span class="sxs-lookup"><span data-stu-id="92a99-104">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellCheckExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/spellcheckexample.xaml#spellcheckexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/CSharp/SpellCheckExample.cs#spellcheckcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_procedural_snip#SpellCheckCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_procedural_snip/visualbasic/spellcheckexample.vb#spellcheckcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="92a99-105">関連項目</span><span class="sxs-lookup"><span data-stu-id="92a99-105">See Also</span></span>  
 [<span data-ttu-id="92a99-106">コンテキスト メニューでスペル チェックを使用する</span><span class="sxs-lookup"><span data-stu-id="92a99-106">Use Spell Checking with a Context Menu</span></span>](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [<span data-ttu-id="92a99-107">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="92a99-107">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="92a99-108">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="92a99-108">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
