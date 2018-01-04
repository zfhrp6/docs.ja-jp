---
title: "方法 : TextBox から行のコレクションを取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12d32266bb901f6ce47d19d92d6f0785277aa7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="52f58-102">方法 : TextBox から行のコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="52f58-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="52f58-103">この例からのテキスト行のコレクションを取得する方法を示しています、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="52f58-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52f58-104">例</span><span class="sxs-lookup"><span data-stu-id="52f58-104">Example</span></span>  
 <span data-ttu-id="52f58-105">次の例を受け取る単純なメソッドを示しています、<xref:System.Windows.Controls.TextBox>引数、および返しますとして、<xref:System.Collections.Specialized.StringCollection>内のテキストの行を含む、 **TextBox**です。</span><span class="sxs-lookup"><span data-stu-id="52f58-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="52f58-106"><xref:System.Windows.Controls.TextBox.LineCount%2A>現在では行の数を決定するプロパティを使用、 **TextBox**、および<xref:System.Windows.Controls.TextBox.GetLineText%2A>各行を抽出し、行のコレクションに追加するメソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="52f58-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="52f58-107">参照</span><span class="sxs-lookup"><span data-stu-id="52f58-107">See Also</span></span>  
 [<span data-ttu-id="52f58-108">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="52f58-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="52f58-109">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="52f58-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
