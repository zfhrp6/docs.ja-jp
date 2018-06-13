---
title: '方法 : ToolStripControlHost を使用して Windows フォーム コントロールをラップする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: 09509705fc8e23b1b5e4fd8c67c12d0be84fc17a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538305"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="a0e1a-102">方法 : ToolStripControlHost を使用して Windows フォーム コントロールをラップする</span><span class="sxs-lookup"><span data-stu-id="a0e1a-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="a0e1a-103"><xref:System.Windows.Forms.ToolStripControlHost> は、<xref:System.Windows.Forms.ToolStripControlHost> コンストラクターを使用するか、<xref:System.Windows.Forms.ToolStripControlHost> 自身を拡張することによって、任意の Windows フォーム コントロールをホストできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="a0e1a-104">より簡単にコントロールをラップするには、<xref:System.Windows.Forms.ToolStripControlHost> を拡張し、頻繁に使用するコントロールのプロパティとメソッドを公開するプロパティとメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="a0e1a-105">コントロールのイベントを <xref:System.Windows.Forms.ToolStripControlHost> レベルで公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="a0e1a-106">派生により ToolStripControlHost でコントロールをホストするには</span><span class="sxs-lookup"><span data-stu-id="a0e1a-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1.  <span data-ttu-id="a0e1a-107"><xref:System.Windows.Forms.ToolStripControlHost> を拡張します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="a0e1a-108">必要なコントロールを渡して基底クラスのコンストラクターを呼び出す既定のコンストラクターを実装します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2.  <span data-ttu-id="a0e1a-109">ラップされたコントロールと同じ型のプロパティを宣言し、プロパティのアクセサーに入れて正しい型のコントロールとして `Control` を返します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3.  <span data-ttu-id="a0e1a-110">ラップされたコントロールで頻繁に使用される他のプロパティとメソッドを、拡張されたクラスのプロパティとメソッドを使用して公開します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4.  <span data-ttu-id="a0e1a-111">必要に応じて、<xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A> メソッドと <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> メソッドをオーバーライドし、公開するコントロール イベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5.  <span data-ttu-id="a0e1a-112">公開するイベントに必要なラップを提供します。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="a0e1a-113">例</span><span class="sxs-lookup"><span data-stu-id="a0e1a-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0e1a-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a0e1a-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="a0e1a-115">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-115">This example requires:</span></span>  
  
-   <span data-ttu-id="a0e1a-116">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a0e1a-117">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a0e1a-118">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="a0e1a-119">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0e1a-119">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e1a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0e1a-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripControlHost>  
 [<span data-ttu-id="a0e1a-121">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="a0e1a-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="a0e1a-122">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="a0e1a-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="a0e1a-123">ToolStrip テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="a0e1a-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
