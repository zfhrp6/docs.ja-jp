---
title: '方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: b3a17a60f897cc3b017eea485952841eaae5a686
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535601"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="7cc0e-102">方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する</span><span class="sxs-lookup"><span data-stu-id="7cc0e-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="7cc0e-103">Windows フォームに <xref:System.Windows.Forms.BindingNavigator> コントロールが登場したことで、開発者はエンドユーザーに、作成したフォームにおける単純なデータ移動および操作のためのユーザー インターフェイスを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="7cc0e-104"><xref:System.Windows.Forms.BindingNavigator> コントロールは、データセットの最初、最後、次、前のレコードへの移動が構成済みのボタンや、レコードを追加および削除するためのボタンを持つ <xref:System.Windows.Forms.ToolStrip> コントロールです。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="7cc0e-105"><xref:System.Windows.Forms.BindingNavigator> コントロールへのボタンの追加は、<xref:System.Windows.Forms.ToolStrip> コントロールなので簡単です。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="7cc0e-106">「[方法 : Windows フォーム BindingNavigator コントロールに [Load]、[Save]、[Cancel] の各ボタンを追加する](http://msdn.microsoft.com/library/safa4957\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="7cc0e-107"><xref:System.Windows.Forms.BindingNavigator> コントロールの各ボタンについて、同じ機能をプログラムで許可する <xref:System.Windows.Forms.BindingSource> コンポーネントの対応するメンバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="7cc0e-108">たとえば、<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> ボタンは <xref:System.Windows.Forms.BindingSource> コンポーネントの <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> メソッドに対応し、<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> ボタンは <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> メソッドに対応します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="7cc0e-109">その結果、データ レコード間を移動する <xref:System.Windows.Forms.BindingNavigator> コントロールを有効にするために必要なのは、<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> プロパティをフォームの適切な <xref:System.Windows.Forms.BindingSource> コンポーネントに設定するだけです。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="7cc0e-110">BindingNavigator コントロールを設定するには</span><span class="sxs-lookup"><span data-stu-id="7cc0e-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="7cc0e-111">`bindingSource1` という名前の <xref:System.Windows.Forms.BindingSource> コンポーネントを 1 つ、`textBox1` と `textBox2` という名前の <xref:System.Windows.Forms.TextBox> コントロールを 2 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="7cc0e-112">`bindingSource1` をデータにバインドし、テキスト ボックス コントロールを `bindingSource1` にバインドします。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="7cc0e-113">そのためには、以下のコードをフォームに貼り付け、フォームのコンストラクターまたは <xref:System.Windows.Forms.Form.Load> イベント処理メソッドから `LoadData` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="7cc0e-114">`bindingNavigator1` という名前の <xref:System.Windows.Forms.BindingNavigator> コントロールをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="7cc0e-115">`bindingNavigator1` の <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> プロパティを `bindingSource1` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="7cc0e-116">これは、デザイナーを使用して、またはコード内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="7cc0e-117">例</span><span class="sxs-lookup"><span data-stu-id="7cc0e-117">Example</span></span>  
 <span data-ttu-id="7cc0e-118">次のコード例は、これまで説明した手順の完全な例です。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7cc0e-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7cc0e-119">Compiling the Code</span></span>  
 <span data-ttu-id="7cc0e-120">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-120">This example requires:</span></span>  
  
-   <span data-ttu-id="7cc0e-121">System、System.Data、System.Drawing、System.Windows.Forms、および System.Xml アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="7cc0e-122">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7cc0e-123">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="7cc0e-124">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cc0e-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc0e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cc0e-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="7cc0e-126">BindingNavigator コントロール</span><span class="sxs-lookup"><span data-stu-id="7cc0e-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="7cc0e-127">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="7cc0e-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
