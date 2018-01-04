---
title: "方法 : Enter キーが押されたことを検出する"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21bb0dc8a38f8b49a4f5372c9dfc1e17e5114d6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="f708f-102">方法 : Enter キーが押されたことを検出する</span><span class="sxs-lookup"><span data-stu-id="f708f-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="f708f-103">この例では、ときに検出、<xref:System.Windows.Input.Key.Enter>キーボードのキーが押されます。</span><span class="sxs-lookup"><span data-stu-id="f708f-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="f708f-104">この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。</span><span class="sxs-lookup"><span data-stu-id="f708f-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f708f-105">例</span><span class="sxs-lookup"><span data-stu-id="f708f-105">Example</span></span>  
 <span data-ttu-id="f708f-106">押されたとき、<xref:System.Windows.Input.Key.Enter>でキー、 <xref:System.Windows.Controls.TextBox>、テキスト ボックスに入力がの別の領域が表示される、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f708f-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="f708f-107">次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]から構成されるユーザー インターフェイスを作成、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="f708f-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="f708f-108">次のコードを作成、<xref:System.Windows.UIElement.KeyDown>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="f708f-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="f708f-109">キーが押されたがある場合、<xref:System.Windows.Input.Key.Enter>でメッセージを表示、キー、<xref:System.Windows.Controls.TextBlock>です。</span><span class="sxs-lookup"><span data-stu-id="f708f-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="f708f-110">参照</span><span class="sxs-lookup"><span data-stu-id="f708f-110">See Also</span></span>  
 [<span data-ttu-id="f708f-111">入力の概要</span><span class="sxs-lookup"><span data-stu-id="f708f-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="f708f-112">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="f708f-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
