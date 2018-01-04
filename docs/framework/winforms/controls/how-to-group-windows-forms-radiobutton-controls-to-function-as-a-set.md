---
title: "方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="e2eb2-102">方法 : セットとして機能する Windows フォーム RadioButton コントロールをグループ化する</span><span class="sxs-lookup"><span data-stu-id="e2eb2-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="e2eb2-103">Windows フォーム<xref:System.Windows.Forms.RadioButton>ユーザーがいるプロシージャまたはオブジェクトを 1 つのみを割り当てることが、2 つ以上の設定の間で選択できるようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="e2eb2-104">たとえば、一連の<xref:System.Windows.Forms.RadioButton>コントロールは、注文の配送業者をパッケージの選択を表示できますが、通信事業者の 1 つだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="e2eb2-105">1 つだけしたがって<xref:System.Windows.Forms.RadioButton>一度に選択できる場合でも、機能グループの一部であります。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="e2eb2-106">オプション ボタンをグループ化することによって、コンテナーの内部など、<xref:System.Windows.Forms.Panel>コントロール、<xref:System.Windows.Forms.GroupBox>コントロール、またはフォームです。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="e2eb2-107">フォームになる 1 つのグループに直接追加されるすべてのオプション ボタンです。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="e2eb2-108">別のグループを追加するには、パネルまたはグループ ボックス内に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="e2eb2-109">パネルまたはグループ ボックスの詳細については、次を参照してください。 [Panel コントロールの概要](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)または[GroupBox コントロールの概要](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="e2eb2-110">その他のセットとは無関係に関数をセットとして RadioButton コントロールをグループ化</span><span class="sxs-lookup"><span data-stu-id="e2eb2-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="e2eb2-111">ドラッグ、<xref:System.Windows.Forms.GroupBox>または<xref:System.Windows.Forms.Panel>から制御、 **Windows フォーム**タブで、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="e2eb2-112">描画<xref:System.Windows.Forms.RadioButton>コントロールに対して、<xref:System.Windows.Forms.GroupBox>または<xref:System.Windows.Forms.Panel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e2eb2-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2eb2-113">参照</span><span class="sxs-lookup"><span data-stu-id="e2eb2-113">See Also</span></span>  
 <xref:System.Windows.Forms.RadioButton>  
 [<span data-ttu-id="e2eb2-114">RadioButton コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="e2eb2-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [<span data-ttu-id="e2eb2-115">Panel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="e2eb2-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="e2eb2-116">GroupBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="e2eb2-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e2eb2-117">CheckBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="e2eb2-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="e2eb2-118">RadioButton コントロール</span><span class="sxs-lookup"><span data-stu-id="e2eb2-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
