---
title: "方法 : データ入力用のサイズ変更可能な Windows フォームを作成する"
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
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d81f47d0a8ba48d18eaf2973d5810672a9aba1b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="9f061-102">方法 : データ入力用のサイズ変更可能な Windows フォームを作成する</span><span class="sxs-lookup"><span data-stu-id="9f061-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="9f061-103">レイアウトが優れていると、その親フォームの寸法の変更に柔軟に対応できます。</span><span class="sxs-lookup"><span data-stu-id="9f061-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="9f061-104"><xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、フォームの寸法の変更に応じて一貫した方法でコントロールの位置とサイズが変更されるように、フォームのレイアウトを調整できます。</span><span class="sxs-lookup"><span data-stu-id="9f061-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="9f061-105"><xref:System.Windows.Forms.TableLayoutPanel> コントロールは、コントロールの内容の変更によってレイアウトの変更が生じる場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="9f061-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="9f061-106">この手順で説明するプロセスは、Visual Studio 環境内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9f061-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="9f061-107">「[チュートリアル: データ入力用のサイズ変更可能な Windows フォームの作成](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f061-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f061-108">例</span><span class="sxs-lookup"><span data-stu-id="9f061-108">Example</span></span>  
 <span data-ttu-id="9f061-109">ユーザーによるフォームのサイズ変更に適切に対応するレイアウトを <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用して作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9f061-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="9f061-110">また、ローカリゼーションに適切に対応するレイアウトも示します。</span><span class="sxs-lookup"><span data-stu-id="9f061-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f061-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9f061-111">Compiling the Code</span></span>  
 <span data-ttu-id="9f061-112">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9f061-112">This example requires:</span></span>  
  
-   <span data-ttu-id="9f061-113">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="9f061-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9f061-114">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f061-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9f061-115">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9f061-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9f061-116">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f061-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f061-117">参照</span><span class="sxs-lookup"><span data-stu-id="9f061-117">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="9f061-118">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="9f061-118">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="9f061-119">方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする</span><span class="sxs-lookup"><span data-stu-id="9f061-119">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="9f061-120">Microsoft Windows ユーザー エクスペリエンス、ユーザー インターフェイスの開発者とデザイナーのための公式のガイドライン。Redmond、WA: Microsoft Press、1999 年。(USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="9f061-120">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
