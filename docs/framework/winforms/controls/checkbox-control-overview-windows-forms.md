---
title: "CheckBox コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a154a3f639102e3f3e2acd62626379e12bbd1344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="8a391-102">CheckBox コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="8a391-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="8a391-103">Windows フォーム <xref:System.Windows.Forms.CheckBox> コントロールは、特定の条件がオンかオフかを示します。</span><span class="sxs-lookup"><span data-stu-id="8a391-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="8a391-104">一般的に、はい/いいえ、または True/False の選択肢をユーザーに提示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a391-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="8a391-105">ユーザーが 1 つ以上選択可能な複数の選択肢を表示するために、チェック ボックス コントロールをグループの中で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a391-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="8a391-106">各を選択したユーザーを示すために使用することで、チェック ボックス コントロールがラジオ ボタン コントロールに似ています。</span><span class="sxs-lookup"><span data-stu-id="8a391-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="8a391-107">そのグループ内の 1 つだけのラジオ ボタンを一度に選択できますが異なります。</span><span class="sxs-lookup"><span data-stu-id="8a391-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="8a391-108">チェック ボックス コントロールで、ただし、任意の数のチェック ボックスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="8a391-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="8a391-109">チェック ボックスは、単純データ バインディングを使用して、データベース内の要素に接続されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a391-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="8a391-110">使用して複数のチェック ボックスをグループ化することがあります、<xref:System.Windows.Forms.GroupBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8a391-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="8a391-111">コントロールをグループ化できます一緒に移動するフォーム デザイナーでこれは、外観もユーザー インターフェイスのデザインに便利です。</span><span class="sxs-lookup"><span data-stu-id="8a391-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="8a391-112">詳細については、次を参照してください。 [Windows フォーム データ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)と[GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a391-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="8a391-113"><xref:System.Windows.Forms.CheckBox>コントロールは、2 つの重要なプロパティを持つ<xref:System.Windows.Forms.CheckBox.Checked%2A>と<xref:System.Windows.Forms.CheckBox.CheckState%2A>です。</span><span class="sxs-lookup"><span data-stu-id="8a391-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="8a391-114"><xref:System.Windows.Forms.CheckBox.Checked%2A>プロパティには、どちらかを返します`true`または`false`です。</span><span class="sxs-lookup"><span data-stu-id="8a391-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="8a391-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A>プロパティには、どちらかを返します<xref:System.Windows.Forms.CheckState.Checked>または<xref:System.Windows.Forms.CheckState.Unchecked>; またはの場合、<xref:System.Windows.Forms.CheckBox.ThreeState%2A>プロパティに設定されている`true`、<xref:System.Windows.Forms.CheckBox.CheckState%2A>を返すことも<xref:System.Windows.Forms.CheckState.Indeterminate>します。</span><span class="sxs-lookup"><span data-stu-id="8a391-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="8a391-116">不確定な状態で淡色表示オプションは使用を示すために、ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a391-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a391-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a391-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="8a391-118">方法: Windows フォームの CheckBox コントロールでオプションを設定する</span><span class="sxs-lookup"><span data-stu-id="8a391-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="8a391-119">方法: Windows フォームの CheckBox のクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="8a391-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="8a391-120">CheckBox コントロール</span><span class="sxs-lookup"><span data-stu-id="8a391-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
