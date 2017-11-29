---
title: "方法 : 実行時にコントロールを非表示にする"
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
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 310750df0786eb07158909eb5e322369d157d1cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="402cd-102">方法 : 実行時にコントロールを非表示にする</span><span class="sxs-lookup"><span data-stu-id="402cd-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="402cd-103">実行時に表示されているユーザー コントロールを作成する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="402cd-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="402cd-104">たとえば、アラーム クロックであるコントロールはアラームが鳴っている場合を除く表示でない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="402cd-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="402cd-105">設定これを簡単に行う、<xref:System.Windows.Forms.Control.Visible%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="402cd-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="402cd-106">場合、<xref:System.Windows.Forms.Control.Visible%2A>プロパティは`true`コントロールを通常どおりに表示されます。</span><span class="sxs-lookup"><span data-stu-id="402cd-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="402cd-107">場合`false`コントロールは表示されません。</span><span class="sxs-lookup"><span data-stu-id="402cd-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="402cd-108">コントロール内のコードは、非表示のとき実行可能性がありますも、ユーザー インターフェイスを使用するコントロールと対話することはできません。</span><span class="sxs-lookup"><span data-stu-id="402cd-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="402cd-109">ユーザー (マウス クリックなど) の入力にも応答を非表示のコントロールを作成する場合は、透明なコントロールを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="402cd-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="402cd-110">詳細については、次を参照してください。[制御を透明な背景に与える](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)です。</span><span class="sxs-lookup"><span data-stu-id="402cd-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="402cd-111">実行時にコントロールを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="402cd-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="402cd-112"><xref:System.Windows.Forms.Control.Visible%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="402cd-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="402cd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="402cd-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="402cd-114">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="402cd-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="402cd-115">方法: コントロールに透明な背景を指定する</span><span class="sxs-lookup"><span data-stu-id="402cd-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
