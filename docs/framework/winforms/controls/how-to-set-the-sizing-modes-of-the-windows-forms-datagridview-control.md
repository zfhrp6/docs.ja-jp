---
title: '方法 : Windows フォーム DataGridView コントロールのサイズ変更モードを設定する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62eb5c9dde5686bf2734e445b9c2a25477a5876f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="6b9c3-102">方法 : Windows フォーム DataGridView コントロールのサイズ変更モードを設定する</span><span class="sxs-lookup"><span data-stu-id="6b9c3-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6b9c3-103">次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールおよびコントロール内の特定の列に対して使用できるサイズ変更オプションをカスタマイズまたは組み合わせる一般的なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="6b9c3-104">固定幅の列を作成するには</span><span class="sxs-lookup"><span data-stu-id="6b9c3-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="6b9c3-105"><xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> に、<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> プロパティを <xref:System.Windows.Forms.DataGridViewTriState.False> に、<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> プロパティを `true` に、<xref:System.Windows.Forms.DataGridViewColumn.Width%2A> プロパティに適切な値をそれぞれ設定します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="6b9c3-106">コンテンツに合わせてサイズが調整される列を作成するには</span><span class="sxs-lookup"><span data-stu-id="6b9c3-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="6b9c3-107"><xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> プロパティを、コンテンツに基づくサイズ変更モードに設定します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="6b9c3-108">サイズと重要度が異なる値に対してフィル モードの列を作成するには</span><span class="sxs-lookup"><span data-stu-id="6b9c3-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="6b9c3-109"><xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> に設定し、この値をオーバーライドしないすべての列のサイズ変更モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="6b9c3-110">列の <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> プロパティを、平均のコンテンツ幅に比例した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="6b9c3-111">重要な列の <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> プロパティを設定して、コンテンツを部分的に表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="6b9c3-112">例</span><span class="sxs-lookup"><span data-stu-id="6b9c3-112">Example</span></span>  
 <span data-ttu-id="6b9c3-113">ここで説明したサイズ変更オプションを理解するために役立つデモ アプリケーションを次の完全なコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="6b9c3-114">このデモ アプリケーションは、次のようにして使用します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="6b9c3-115">フォームのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-115">Change the size of the form.</span></span> <span data-ttu-id="6b9c3-116"><xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> プロパティ値で指定した比率を維持しながら、フィル モードの列の幅が変化する様子を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="6b9c3-117">フォームが小さすぎる場合に、列の <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> より狭くは変更されない様子を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="6b9c3-118">マウスで列の区分線をドラッグして、列のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="6b9c3-119">一部の列ではサイズ変更ができない様子、およびサイズ変更可能な列でも幅を最小幅よりも狭くできない様子を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b9c3-120">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6b9c3-120">Compiling the Code</span></span>  
 <span data-ttu-id="6b9c3-121">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-121">This example requires:</span></span>  
  
-   <span data-ttu-id="6b9c3-122">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6b9c3-123">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6b9c3-124">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6b9c3-125">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b9c3-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9c3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b9c3-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
