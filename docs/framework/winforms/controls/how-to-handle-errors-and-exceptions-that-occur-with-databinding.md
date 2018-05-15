---
title: '方法 : データ バインドで発生するエラーと例外を処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: c7c05eb8d858c1f911e148def1c714e3caf74c95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="32600-102">方法 : データ バインドで発生するエラーと例外を処理する</span><span class="sxs-lookup"><span data-stu-id="32600-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="32600-103">基になるビジネス オブジェクトをコントロールにバインドするときに、それらのビジネス オブジェクトで例外やエラーが発生することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="32600-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="32600-104">特定の <xref:System.Windows.Forms.Binding> コンポーネント、<xref:System.Windows.Forms.BindingSource> コンポーネント、または <xref:System.Windows.Forms.CurrencyManager> コンポーネントの <xref:System.Windows.Forms.Binding.BindingComplete> イベントを処理することにより、これらのエラーや例外をインターセプトし、回復したり、エラー情報をユーザーに渡したりできます。</span><span class="sxs-lookup"><span data-stu-id="32600-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32600-105">例</span><span class="sxs-lookup"><span data-stu-id="32600-105">Example</span></span>  
 <span data-ttu-id="32600-106">データ バインディング操作時に発生するエラーと例外を処理する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="32600-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="32600-107">ここでは、<xref:System.Windows.Forms.Binding> オブジェクトの <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> イベントを処理してエラーをインターセプトする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="32600-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="32600-108">このイベントを処理してエラーと例外をインターセプトするには、バインディングの書式設定を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32600-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="32600-109">バインディングの書式設定は、バインディングの作成時やバインディング コレクションへの追加時に有効にできます。また、<xref:System.Windows.Forms.Binding.FormattingEnabled%2A> プロパティを `true` に設定すると有効にできます。</span><span class="sxs-lookup"><span data-stu-id="32600-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="32600-110">コードの実行時に、部品名に空の文字列が入力されるか、部品番号に 100 未満の値が入力されると、メッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="32600-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="32600-111">これは、これらのテキスト ボックス バインディングの <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> イベントを処理した結果です。</span><span class="sxs-lookup"><span data-stu-id="32600-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="32600-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="32600-112">Compiling the Code</span></span>  
 <span data-ttu-id="32600-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="32600-113">This example requires:</span></span>  
  
-   <span data-ttu-id="32600-114">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="32600-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="32600-115">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="32600-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="32600-116">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="32600-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="32600-117">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="32600-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32600-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="32600-118">See Also</span></span>  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [<span data-ttu-id="32600-119">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="32600-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
