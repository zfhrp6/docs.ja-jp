---
title: '方法 : Windows フォームの DataGridView コントロールの行の外観をカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 343e637eb5250ff4d6a1e70660dc76453e632776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526280"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e40df-102">方法 : Windows フォームの DataGridView コントロールの行の外観をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="e40df-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e40df-103"><xref:System.Windows.Forms.DataGridView> 行の外観を制御するには、<xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> イベントと <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> イベントの一方、または両方を処理します。</span><span class="sxs-lookup"><span data-stu-id="e40df-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="e40df-104">これらのイベントは、ユーザーが任意のものだけ描画し、残りは <xref:System.Windows.Forms.DataGridView> コントロールに描画させるようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="e40df-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="e40df-105">たとえば、カスタムの背景を描画する場合は、<xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> イベントを処理し、それぞれの前景の内容は個々のセルに描画させるようにします。</span><span class="sxs-lookup"><span data-stu-id="e40df-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="e40df-106">または、セルを自動的に描画させ、<xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> イベントのハンドラーでカスタムの前景の内容を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="e40df-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="e40df-107">さらに、<xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> イベント ハンドラーを使用すれば、セルの描画をすべて無効にし、ユーザー自身ですべてを描画することもできます。</span><span class="sxs-lookup"><span data-stu-id="e40df-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="e40df-108">次のコード例では、選択行にグラデーションの背景を表示し、複数の列にわたるカスタムの前景の内容を提供するために、両方のイベントのハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="e40df-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40df-109">例</span><span class="sxs-lookup"><span data-stu-id="e40df-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e40df-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e40df-110">Compiling the Code</span></span>  
 <span data-ttu-id="e40df-111">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e40df-111">This example requires:</span></span>  
  
-   <span data-ttu-id="e40df-112">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="e40df-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e40df-113">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="e40df-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e40df-114">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="e40df-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e40df-115">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="e40df-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40df-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e40df-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [<span data-ttu-id="e40df-117">Windows フォーム DataGridView コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e40df-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="e40df-118">DataGridView コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="e40df-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
