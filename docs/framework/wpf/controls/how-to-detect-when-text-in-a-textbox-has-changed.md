---
title: '方法 : TextBox のテキストがいつ変更されたかを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552953"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="e28ec-102">方法 : TextBox のテキストがいつ変更されたかを検出する</span><span class="sxs-lookup"><span data-stu-id="e28ec-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="e28ec-103">この例を使用する方法を示しています、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベント メソッドを実行するたびに内のテキスト、<xref:System.Windows.Controls.TextBox>コントロールが変更されました。</span><span class="sxs-lookup"><span data-stu-id="e28ec-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="e28ec-104">分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールを挿入するたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="e28ec-105">このメソッドのシグネチャが一致で期待される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="e28ec-106">イベント ハンドラーが呼び出されるとされるたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムによってコントロールを変更します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="e28ec-107">**注:** このイベントが発生したときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e28ec-108">例</span><span class="sxs-lookup"><span data-stu-id="e28ec-108">Example</span></span>  
 <span data-ttu-id="e28ec-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>コントロールを指定、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>の属性をイベント ハンドラー メソッドの名前に一致する値。</span><span class="sxs-lookup"><span data-stu-id="e28ec-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="e28ec-110">例</span><span class="sxs-lookup"><span data-stu-id="e28ec-110">Example</span></span>  
 <span data-ttu-id="e28ec-111">分離コード クラスで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を格納している、<xref:System.Windows.Controls.TextBox>変更については、監視するコントロールを挿入するたびに呼び出すメソッドを<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="e28ec-112">このメソッドのシグネチャが一致で期待される必要があります、<xref:System.Windows.Controls.TextChangedEventHandler>を委任します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="e28ec-113">イベント ハンドラーが呼び出されるとされるたびの内容、<xref:System.Windows.Controls.TextBox>ユーザー、またはプログラムによってコントロールを変更します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="e28ec-114">**注:** このイベントが発生したときに、<xref:System.Windows.Controls.TextBox>コントロールが作成し、最初にテキストを格納します。</span><span class="sxs-lookup"><span data-stu-id="e28ec-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="e28ec-115">コメント</span><span class="sxs-lookup"><span data-stu-id="e28ec-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28ec-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e28ec-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="e28ec-117">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="e28ec-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="e28ec-118">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="e28ec-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
