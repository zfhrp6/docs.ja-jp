---
title: "方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する"
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
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28a83a623329a7bf0162bb9feb0dc21bb73611cf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="bc010-102">方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する</span><span class="sxs-lookup"><span data-stu-id="bc010-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="bc010-103">設定することができます、<xref:System.Windows.Forms.ToolTip>コード内、または Windows フォーム デザイナーでの文字列。</span><span class="sxs-lookup"><span data-stu-id="bc010-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="bc010-104">詳細については、<xref:System.Windows.Forms.ToolTip>コンポーネントを参照してください[ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc010-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc010-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc010-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bc010-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bc010-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bc010-107">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc010-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="bc010-108">ツールヒントをコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="bc010-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="bc010-109">ツールヒントを表示するコントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc010-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="bc010-110">使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="bc010-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="bc010-111">デザイナーでツールヒントを設定するには</span><span class="sxs-lookup"><span data-stu-id="bc010-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="bc010-112">フォームに <xref:System.Windows.Forms.ToolTip> コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc010-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="bc010-113">ツールヒントを表示またはフォームに追加されるコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="bc010-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="bc010-114">**プロパティ**ウィンドウで、設定、 **ToolTip1 のツールヒント**をテキストの適切な文字列値です。</span><span class="sxs-lookup"><span data-stu-id="bc010-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc010-115">参照</span><span class="sxs-lookup"><span data-stu-id="bc010-115">See Also</span></span>  
 [<span data-ttu-id="bc010-116">ToolTip コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="bc010-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="bc010-117">方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する</span><span class="sxs-lookup"><span data-stu-id="bc010-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="bc010-118">ToolTip コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bc010-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
