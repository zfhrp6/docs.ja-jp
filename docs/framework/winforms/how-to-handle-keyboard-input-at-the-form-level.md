---
title: "方法 : キーボード入力をフォーム レベルで処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2539ef6bb093ea026b3578250e4ec3a4cf1a19
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="e8c59-102">方法 : キーボード入力をフォーム レベルで処理する</span><span class="sxs-lookup"><span data-stu-id="e8c59-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="e8c59-103">Windows フォームでは、キーボード メッセージがコントロールに到達する前に、それらのメッセージをフォーム レベルで処理できます。</span><span class="sxs-lookup"><span data-stu-id="e8c59-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="e8c59-104">ここでは、このタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8c59-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="e8c59-105">キーボード入力をフォーム レベルで処理するには</span><span class="sxs-lookup"><span data-stu-id="e8c59-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="e8c59-106">スタートアップ フォームの <xref:System.Windows.Forms.Control.KeyPress> イベントまたは <xref:System.Windows.Forms.Control.KeyDown> イベントを処理し、このフォームの <xref:System.Windows.Forms.Form.KeyPreview%2A> プロパティを `true` に設定して、キーボード メッセージがフォーム上のコントロールに到達する前にフォームによって受け取られるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8c59-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="e8c59-107">次のコード例では、<xref:System.Windows.Forms.Control.KeyPress> イベントを処理して、すべての数値キーを検出し、"1"、"4"、および "7" の各キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8c59-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e8c59-108">例</span><span class="sxs-lookup"><span data-stu-id="e8c59-108">Example</span></span>  
 <span data-ttu-id="e8c59-109">次のコード例は、上の例の完全なアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e8c59-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="e8c59-110">このアプリケーションには、<xref:System.Windows.Forms.TextBox> の他に、<xref:System.Windows.Forms.TextBox> からフォーカスを移動できるようにするいくつかのコントロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e8c59-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="e8c59-111">メイン <xref:System.Windows.Forms.Form> の <xref:System.Windows.Forms.Control.KeyPress> イベントは "1"、"4"、および "7" の各キーを使用し、<xref:System.Windows.Forms.TextBox> の <xref:System.Windows.Forms.Control.KeyPress> イベントは "2"、"5"、および "8" の各キーを使用します。残りのキーは表示されるだけです。</span><span class="sxs-lookup"><span data-stu-id="e8c59-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="e8c59-112"><xref:System.Windows.Forms.TextBox> にフォーカスがあるときに数値キーを押すと生成される <xref:System.Windows.Forms.MessageBox> 出力と、他のコントロールのいずれかにフォーカスがあるときに数値キーを押すと生成される <xref:System.Windows.Forms.MessageBox> 出力を比較してください。</span><span class="sxs-lookup"><span data-stu-id="e8c59-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8c59-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e8c59-113">Compiling the Code</span></span>  
 <span data-ttu-id="e8c59-114">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e8c59-114">This example requires:</span></span>  
  
-   <span data-ttu-id="e8c59-115">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="e8c59-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e8c59-116">[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c59-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e8c59-117">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e8c59-117">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e8c59-118">「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8c59-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c59-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8c59-119">See Also</span></span>  
 [<span data-ttu-id="e8c59-120">Windows フォーム アプリケーションにおけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="e8c59-120">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
