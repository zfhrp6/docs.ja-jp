---
title: "方法 : TextBox コントロールを読み取り専用にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36116346b389dac7e9783e69d9bcd79573b4bf75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="51c6e-102">方法 : TextBox コントロールを読み取り専用にする</span><span class="sxs-lookup"><span data-stu-id="51c6e-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="51c6e-103">この例は、構成する方法を示します、<xref:System.Windows.Controls.TextBox>ユーザー入力や変更を許可しないように制御します。</span><span class="sxs-lookup"><span data-stu-id="51c6e-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c6e-104">例</span><span class="sxs-lookup"><span data-stu-id="51c6e-104">Example</span></span>  
 <span data-ttu-id="51c6e-105">ユーザーがの内容を変更することを防止する、<xref:System.Windows.Controls.TextBox>コントロールを設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>属性を**true**です。</span><span class="sxs-lookup"><span data-stu-id="51c6e-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="51c6e-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>属性にはユーザーの入力のみが影響します。 内のテキスト セットには影響しません、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の説明、<xref:System.Windows.Controls.TextBox>コントロール、またはプログラムから設定されたテキスト、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="51c6e-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="51c6e-107">既定値の<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>は**false**です。</span><span class="sxs-lookup"><span data-stu-id="51c6e-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c6e-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="51c6e-108">See Also</span></span>  
 [<span data-ttu-id="51c6e-109">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="51c6e-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="51c6e-110">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="51c6e-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
