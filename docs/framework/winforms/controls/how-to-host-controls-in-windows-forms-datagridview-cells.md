---
title: '方法 : Windows フォーム DataGridView Cells でコントロールをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 730a0677dbc405617c7075402ba0c20dfbd8724d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534048"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="c8d63-102">方法 : Windows フォーム DataGridView Cells でコントロールをホストする</span><span class="sxs-lookup"><span data-stu-id="c8d63-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="c8d63-103"><xref:System.Windows.Forms.DataGridView> コントロールには数種類の列があり、ユーザーはさまざまな方法で値を入力し、編集できます。</span><span class="sxs-lookup"><span data-stu-id="c8d63-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="c8d63-104">ただし、これらの種類の列がデータ入力の要件を満たさない場合は、独自の種類の列を作成して、任意のコントロールをホストするセルを用意できます。</span><span class="sxs-lookup"><span data-stu-id="c8d63-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="c8d63-105">これを作成するには、<xref:System.Windows.Forms.DataGridViewColumn> および <xref:System.Windows.Forms.DataGridViewCell> から派生する各クラスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8d63-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="c8d63-106">また、<xref:System.Windows.Forms.Control> から派生し、<xref:System.Windows.Forms.IDataGridViewEditingControl> インターフェイスを実装するクラスを定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c8d63-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="c8d63-107">予定表の列を作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="c8d63-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="c8d63-108">この列のセルは、通常のテキスト ボックスのセルに日付を表示しますが、ユーザーがセルを編集するときには <xref:System.Windows.Forms.DateTimePicker> コントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8d63-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="c8d63-109">テキスト ボックスの表示機能を再度実装しなくてもすむように、`CalendarCell` クラスは、<xref:System.Windows.Forms.DataGridViewCell> クラスを直接継承するのではなく <xref:System.Windows.Forms.DataGridViewTextBoxCell> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="c8d63-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8d63-110"><xref:System.Windows.Forms.DataGridViewCell> や <xref:System.Windows.Forms.DataGridViewColumn> から派生したクラスに新しいプロパティを追加するときは、`Clone` メソッドをオーバーライドし、複製操作時に新しいプロパティをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8d63-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="c8d63-111">また、基底クラスの `Clone` メソッドを呼び出して、基底クラスのプロパティを新しいセルまたは列にコピーする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c8d63-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8d63-112">例</span><span class="sxs-lookup"><span data-stu-id="c8d63-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8d63-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c8d63-113">Compiling the Code</span></span>  
 <span data-ttu-id="c8d63-114">この例には、次の項目が必要です。</span><span class="sxs-lookup"><span data-stu-id="c8d63-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="c8d63-115">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="c8d63-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c8d63-116">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8d63-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c8d63-117">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="c8d63-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c8d63-118">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8d63-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d63-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8d63-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [<span data-ttu-id="c8d63-120">Windows フォーム DataGridView コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="c8d63-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c8d63-121">DataGridView コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="c8d63-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="c8d63-122">Windows フォーム DataGridView コントロールの列型</span><span class="sxs-lookup"><span data-stu-id="c8d63-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
