---
title: "ToolTip コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="3620b-102">ToolTip コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="3620b-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="3620b-103">Windows フォーム <xref:System.Windows.Forms.ToolTip> コンポーネントは、ユーザーがコントロールをポイントしたときにテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="3620b-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="3620b-104">ツールヒントは任意のコントロールに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="3620b-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="3620b-105">このコンポーネントの使用例: フォームの容量を節約するボタンに小さなアイコンを表示し、ボタンの機能を説明するツールヒントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3620b-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="3620b-106">ToolTip コンポーネントの操作</span><span class="sxs-lookup"><span data-stu-id="3620b-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="3620b-107">A<xref:System.Windows.Forms.ToolTip>コンポーネントは、提供、`ToolTip`プロパティを複数のコントロール Windows フォームまたはその他のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="3620b-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="3620b-108">たとえば、1 つ配置した場合<xref:System.Windows.Forms.ToolTip>フォームのコンポーネントは、「の名前を入力」表示できる、<xref:System.Windows.Forms.TextBox>を制御し、「ここをクリックして変更を保存する」、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3620b-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="3620b-109">主要なメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネントは<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>と<xref:System.Windows.Forms.ToolTip.GetToolTip%2A>です。</span><span class="sxs-lookup"><span data-stu-id="3620b-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="3620b-110">使用することができます、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>コントロールに対して表示されるツールヒントを設定します。</span><span class="sxs-lookup"><span data-stu-id="3620b-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="3620b-111">詳細については、次を参照してください。[する方法: デザイン時に Windows フォームのコントロールにツールヒントを設定](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="3620b-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="3620b-112">プロパティは<xref:System.Windows.Forms.ToolTip.Active%2A>設定する必要があります`true`が表示されるツールヒントのおよび<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>、ツール ヒントの文字列が表示されている時間の長さを設定する、ユーザーが表示されるツールヒントのコントロールでポイントする必要があります期間と長時間かかる場合は、方法表示されるツールヒント ウィンドウを取得します。</span><span class="sxs-lookup"><span data-stu-id="3620b-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="3620b-113">詳細については、次を参照してください。[する方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="3620b-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3620b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3620b-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="3620b-115">方法: デザイン時に Windows フォームのコントロールにツールヒントを設定する</span><span class="sxs-lookup"><span data-stu-id="3620b-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="3620b-116">方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する</span><span class="sxs-lookup"><span data-stu-id="3620b-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
