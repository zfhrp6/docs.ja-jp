---
title: "方法 : バックグラウンドで操作を実行する"
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9a92427310dc36392b35f22e39c1d4ae101db74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="aa802-102">方法 : バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="aa802-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="aa802-103">完了に長い時間がかかる操作を実行しており、ユーザー インターフェイスで遅延が発生しないようにするには<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="aa802-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="aa802-104">次のコード例は、バック グラウンドで時間のかかる操作を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aa802-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="aa802-105">フォームには、**[開始]** ボタンと **[キャンセル]** ボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="aa802-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="aa802-106">非同期操作を実行するには、**[開始]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa802-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="aa802-107">実行中の非同期操作を停止するには、**[キャンセル]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa802-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="aa802-108">各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa802-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="aa802-109">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] では、このタスクに対する広範なサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa802-109">There is extensive support for this task in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="aa802-110">「[チュートリアル: 操作をバックグラウンドで実行する](http://msdn.microsoft.com/library/ms233672\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa802-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa802-111">例</span><span class="sxs-lookup"><span data-stu-id="aa802-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa802-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="aa802-112">Compiling the Code</span></span>  
 <span data-ttu-id="aa802-113">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa802-113">This example requires:</span></span>  
  
-   <span data-ttu-id="aa802-114">System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="aa802-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="aa802-115">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa802-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="aa802-116">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="aa802-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="aa802-117">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa802-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa802-118">参照</span><span class="sxs-lookup"><span data-stu-id="aa802-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="aa802-119">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="aa802-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="aa802-120">BackgroundWorker コンポーネント</span><span class="sxs-lookup"><span data-stu-id="aa802-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
