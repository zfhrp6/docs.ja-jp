---
title: '方法 : 実行時にコントロールを非表示にする'
ms.date: 03/30/2017
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
ms.openlocfilehash: 51e804c7f01b55ed7504837042b6c32bf47d9405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532413"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="4d2af-102">方法 : 実行時にコントロールを非表示にする</span><span class="sxs-lookup"><span data-stu-id="4d2af-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="4d2af-103">実行時に表示されているユーザー コントロールを作成する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4d2af-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="4d2af-104">たとえば、アラーム クロックであるコントロールはアラームが鳴っている場合を除く表示でない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d2af-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="4d2af-105">設定これを簡単に行う、<xref:System.Windows.Forms.Control.Visible%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="4d2af-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="4d2af-106">場合、<xref:System.Windows.Forms.Control.Visible%2A>プロパティは`true`コントロールを通常どおりに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4d2af-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="4d2af-107">場合`false`コントロールは表示されません。</span><span class="sxs-lookup"><span data-stu-id="4d2af-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="4d2af-108">コントロール内のコードは、非表示のとき実行可能性がありますも、ユーザー インターフェイスを使用するコントロールと対話することはできません。</span><span class="sxs-lookup"><span data-stu-id="4d2af-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="4d2af-109">ユーザー (マウス クリックなど) の入力にも応答を非表示のコントロールを作成する場合は、透明なコントロールを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d2af-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="4d2af-110">詳細については、次を参照してください。[制御を透明な背景に与える](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d2af-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="4d2af-111">実行時にコントロールを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="4d2af-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="4d2af-112"><xref:System.Windows.Forms.Control.Visible%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4d2af-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d2af-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d2af-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="4d2af-114">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="4d2af-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="4d2af-115">方法: コントロールに透明な背景を指定する</span><span class="sxs-lookup"><span data-stu-id="4d2af-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
