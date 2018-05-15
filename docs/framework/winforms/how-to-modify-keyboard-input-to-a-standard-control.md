---
title: '方法 : キーボード入力を標準コントロールに変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 726444e1decb3e03989317431e1f8c4a5fc4a697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="b04dd-102">方法 : キーボード入力を標準コントロールに変更する</span><span class="sxs-lookup"><span data-stu-id="b04dd-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="b04dd-103">Windows フォームは、キーボードの入力を使用して変更する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="b04dd-104">キーの使用とは、メッセージ キューのさらに下のその他のメソッドとイベントが、キーの値を受信しないようにメソッドまたはイベント ハンドラー内のキーを処理することを表します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="b04dd-105">キーの変更とは、メッセージ キューのさらに下のメソッドとイベント ハンドラーが、異なるキーの値を受け取るようにキーの値を変更することを表します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="b04dd-106">このトピックでは、これらのタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="b04dd-107">キーを使用するには</span><span class="sxs-lookup"><span data-stu-id="b04dd-107">To consume a key</span></span>  
  
-   <span data-ttu-id="b04dd-108"><xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="b04dd-109">または</span><span class="sxs-lookup"><span data-stu-id="b04dd-109">-or-</span></span>  
  
     <span data-ttu-id="b04dd-110"><xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで、<xref:System.Windows.Forms.KeyEventArgs> クラスの <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b04dd-111"><xref:System.Windows.Forms.Control.KeyDown> イベント ハンドラーで <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> プロパティを設定すると、<xref:System.Windows.Forms.Control.KeyPress> イベントと <xref:System.Windows.Forms.Control.KeyUp> イベントが現在のキー入力から発生しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="b04dd-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="b04dd-112">この目的には、<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="b04dd-113">次の例は、<xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーによって受信された <xref:System.Windows.Forms.KeyPressEventArgs> の <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを検査する `switch` ステートメントの抜粋です。</span><span class="sxs-lookup"><span data-stu-id="b04dd-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="b04dd-114">このコードは、'A' と 'a' 文字のキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="b04dd-115">標準の文字のキーを変更するには</span><span class="sxs-lookup"><span data-stu-id="b04dd-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="b04dd-116"><xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラーで、<xref:System.Windows.Forms.KeyPressEventArgs> クラスの <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> プロパティを新しい文字のキーの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="b04dd-117">次の例は、'B' を 'A' に変更して、'b' を 'a' に変更する `switch` ステートメントの抜粋です。</span><span class="sxs-lookup"><span data-stu-id="b04dd-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="b04dd-118"><xref:System.Windows.Forms.KeyPressEventArgs> パラメーターの <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> のプロパティが `false` に設定され、新しいキーの値が、メッセージ キューの他のメソッドとイベントに反映されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b04dd-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="b04dd-119">非文字キーを変更するには</span><span class="sxs-lookup"><span data-stu-id="b04dd-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="b04dd-120">Windows メッセージを処理する <xref:System.Windows.Forms.Control> メソッドをオーバーライドして、WM_KEYDOWN または WM_SYSKEYDOWN のメッセージを検出し、<xref:System.Windows.Forms.Message> パラメーターの <xref:System.Windows.Forms.Message.WParam%2A> プロパティを、新しい非文字キーを表す <xref:System.Windows.Forms.Keys> 値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="b04dd-121">次のコード例は、F1 から F9 のキーを検出して、F3 キーを押したときに F1 に変更するよう、コントロールの <xref:System.Windows.Forms.Control.PreProcessMessage%2A> メソッドをオーバーライドする方法を示しています、</span><span class="sxs-lookup"><span data-stu-id="b04dd-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="b04dd-122">詳細については<xref:System.Windows.Forms.Control>キーボード メッセージを中断するようにオーバーライドできるメソッドを参照してください[Windows フォーム アプリケーションにおけるユーザー入力](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)と[キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)です。</span><span class="sxs-lookup"><span data-stu-id="b04dd-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](../../../docs/framework/winforms/how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="b04dd-123">例</span><span class="sxs-lookup"><span data-stu-id="b04dd-123">Example</span></span>  
 <span data-ttu-id="b04dd-124">次のコード例は、前のセクションのコード例の完全なアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="b04dd-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="b04dd-125">アプリケーションは、<xref:System.Windows.Forms.TextBox> クラスから派生したカスタム コントロールを使用して、キーボードの入力を使用して変更します。</span><span class="sxs-lookup"><span data-stu-id="b04dd-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b04dd-126">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b04dd-126">Compiling the Code</span></span>  
 <span data-ttu-id="b04dd-127">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b04dd-127">This example requires:</span></span>  
  
-   <span data-ttu-id="b04dd-128">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="b04dd-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b04dd-129">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="b04dd-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b04dd-130">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="b04dd-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b04dd-131">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="b04dd-131">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04dd-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b04dd-132">See Also</span></span>  
 [<span data-ttu-id="b04dd-133">Windows フォーム アプリケーションにおけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="b04dd-133">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="b04dd-134">Windows フォーム アプリケーションにおけるユーザー入力</span><span class="sxs-lookup"><span data-stu-id="b04dd-134">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="b04dd-135">キーボード入力のしくみ</span><span class="sxs-lookup"><span data-stu-id="b04dd-135">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)
