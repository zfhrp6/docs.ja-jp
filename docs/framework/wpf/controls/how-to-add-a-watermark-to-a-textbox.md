---
title: "方法: TextBox にウォーターマークを追加する"
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
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92d619cb713e22d49e5c62bf7545d946b418dbda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="46cf8-102">方法: TextBox にウォーターマークを追加する</span><span class="sxs-lookup"><span data-stu-id="46cf8-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="46cf8-103">次の例の使いやすさを支援する方法を示しています、<xref:System.Windows.Controls.TextBox>内の説明の背景イメージを表示することによって、<xref:System.Windows.Controls.TextBox>この時点で、イメージを削除するまで、ユーザーがテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="46cf8-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="46cf8-104">さらに、背景画像は、ユーザー入力を削除する場合、再度復元します。</span><span class="sxs-lookup"><span data-stu-id="46cf8-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="46cf8-105">次の図を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46cf8-105">See illustration below.</span></span>  
  
 <span data-ttu-id="46cf8-106">![背景画像を含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="46cf8-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46cf8-107">背景画像は、この例ではなく、単に操作で使用する理由、<xref:System.Windows.Controls.TextBox.Text%2A>のプロパティ<xref:System.Windows.Controls.TextBox>がある、背景画像は、データ バインディングには影響しません。</span><span class="sxs-lookup"><span data-stu-id="46cf8-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46cf8-108">例</span><span class="sxs-lookup"><span data-stu-id="46cf8-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="46cf8-109">参照</span><span class="sxs-lookup"><span data-stu-id="46cf8-109">See Also</span></span>  
 [<span data-ttu-id="46cf8-110">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="46cf8-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="46cf8-111">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="46cf8-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
