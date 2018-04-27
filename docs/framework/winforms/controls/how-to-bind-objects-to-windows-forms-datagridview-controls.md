---
title: '方法 : オブジェクトを Windows フォーム DataGridView コントロールにバインドする'
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
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8cb84608c0aeead00e56d2d91489954e4b7fca6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="55a18-102">方法 : オブジェクトを Windows フォーム DataGridView コントロールにバインドする</span><span class="sxs-lookup"><span data-stu-id="55a18-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="55a18-103">各オブジェクトが別々の行として表示されるように <xref:System.Windows.Forms.DataGridView> コントロールにオブジェクトのコレクションをバインドする方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="55a18-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="55a18-104">また、この例では、<xref:System.Windows.Forms.DataGridViewComboBoxColumn> にプロパティとして列挙型を表示し、コンボ ボックスのドロップダウン リストに列挙値が含まれるようにする方法も示されています。</span><span class="sxs-lookup"><span data-stu-id="55a18-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a18-105">例</span><span class="sxs-lookup"><span data-stu-id="55a18-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55a18-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="55a18-106">Compiling the Code</span></span>  
 <span data-ttu-id="55a18-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55a18-107">This example requires:</span></span>  
  
-   <span data-ttu-id="55a18-108">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="55a18-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="55a18-109">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="55a18-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="55a18-110">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="55a18-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="55a18-111">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="55a18-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a18-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="55a18-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="55a18-113">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="55a18-113">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="55a18-114">方法: Windows フォームの DataGridView 行にバインドされたオブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="55a18-114">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
