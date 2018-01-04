---
title: "方法 : TextWrapping プロパティをプログラムにより変更する"
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
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca87d651f66edba00280a57ca1468af33657a329
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="d70f9-102">方法 : TextWrapping プロパティをプログラムにより変更する</span><span class="sxs-lookup"><span data-stu-id="d70f9-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="d70f9-103">例</span><span class="sxs-lookup"><span data-stu-id="d70f9-103">Example</span></span>  
 <span data-ttu-id="d70f9-104">次のコード例の値を変更する方法を示しています、<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>プロパティ プログラムでします。</span><span class="sxs-lookup"><span data-stu-id="d70f9-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="d70f9-105">次の 3 つ<xref:System.Windows.Controls.Button>内の要素を配置している、<xref:System.Windows.Controls.StackPanel>内の要素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d70f9-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="d70f9-106">各<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを<xref:System.Windows.Controls.Button>をイベント ハンドラーのコードに対応しています。</span><span class="sxs-lookup"><span data-stu-id="d70f9-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="d70f9-107">イベント ハンドラーと同じ名前を使用して、<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>値に適用されます`txt2`ボタンがクリックされたときにします。</span><span class="sxs-lookup"><span data-stu-id="d70f9-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="d70f9-108">内のテキストも、 `txt1` (、<xref:System.Windows.Controls.TextBlock>に表示されていない、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) プロパティに変更を反映するように更新されます。</span><span class="sxs-lookup"><span data-stu-id="d70f9-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d70f9-109">参照</span><span class="sxs-lookup"><span data-stu-id="d70f9-109">See Also</span></span>  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
