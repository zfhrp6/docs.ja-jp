---
title: '方法 : Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
ms.openlocfilehash: e47c61667a12ea9215c13bee873a668d2ad2188b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="7a17e-102">方法 : Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする</span><span class="sxs-lookup"><span data-stu-id="7a17e-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="7a17e-103"><xref:System.Windows.Forms.ListView> コントロールの並べて表示ビュー機能を使用すると、グラフィカルな情報とテキスト情報をバランスよく表示できます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="7a17e-104">並べて表示ビューの項目で表示されるテキスト情報は、詳細ビュー用に定義されている列情報と同じ情報です。</span><span class="sxs-lookup"><span data-stu-id="7a17e-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="7a17e-105">並べて表示ビューは、<xref:System.Windows.Forms.ListView> コントロールのグループ化機能または挿入マーク機能のいずれかと組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="7a17e-106">並べて表示ビューでは、サイズが 32 × 32 ピクセルのアイコンと数行のテキストが次の画像のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="7a17e-107">![ListView コントロール内のタイル ビュー](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="7a17e-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
<span data-ttu-id="7a17e-108">並べて表示ビューのアイコンとテキスト</span><span class="sxs-lookup"><span data-stu-id="7a17e-108">Tile view icons and text</span></span>  
  
 <span data-ttu-id="7a17e-109">並べて表示ビューを有効にするには、<xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View.Tile> に設定します。</span><span class="sxs-lookup"><span data-stu-id="7a17e-109">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="7a17e-110"><xref:System.Windows.Forms.ListView.TileSize%2A> プロパティを設定するとタイトルのサイズを調整できます。また、<xref:System.Windows.Forms.ListView.Columns%2A> コレクションを調整すると、タイルに表示されるテキストの行数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-110">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a17e-111">並べて表示ビューを [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> メソッドを呼び出した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="7a17e-111">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a17e-112">旧バージョンのオペレーティング システムでは、並べて表示ビューに関するコードがすべて無効になり、<xref:System.Windows.Forms.ListView> コントロールは大きなアイコンのビューで表示されます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-112">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="7a17e-113">詳細については、「<xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a17e-113">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="7a17e-114">プログラムによって並べて表示ビューを設定するには</span><span class="sxs-lookup"><span data-stu-id="7a17e-114">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="7a17e-115"><xref:System.Windows.Forms.ListView> コントロールの <xref:System.Windows.Forms.View> 列挙体を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a17e-115">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="7a17e-116">例</span><span class="sxs-lookup"><span data-stu-id="7a17e-116">Example</span></span>  
 <span data-ttu-id="7a17e-117">次の完全なコード例は、タイルに表示するテキストを 3 行に変更した並べて表示ビューを示しています。</span><span class="sxs-lookup"><span data-stu-id="7a17e-117">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="7a17e-118">行の折り返しが発生しないようにタイルのサイズを調整しました。</span><span class="sxs-lookup"><span data-stu-id="7a17e-118">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a17e-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7a17e-119">Compiling the Code</span></span>  
 <span data-ttu-id="7a17e-120">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7a17e-120">This example requires:</span></span>  
  
-   <span data-ttu-id="7a17e-121">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="7a17e-121">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="7a17e-122">book.ico という名前のアイコン ファイルは、実行可能ファイルと同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="7a17e-122">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="7a17e-123">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a17e-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7a17e-124">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="7a17e-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="7a17e-125">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a17e-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a17e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a17e-126">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="7a17e-127">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="7a17e-127">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="7a17e-128">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7a17e-128">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="7a17e-129">Windows XP の機能と Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="7a17e-129">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
