---
title: "Label コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f68642eb5f996722097976e042006afbf366ae39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="defa5-102">Label コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="defa5-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="defa5-103">Windows フォーム<xref:System.Windows.Forms.Label>テキストや、ユーザーが編集できないイメージを表示するコントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="defa5-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="defa5-104">フォーム上のオブジェクトの識別に使用されます: どのような特定のコントロールの説明をクリックした場合などを提供するか、実行時イベントまたはアプリケーションのプロセスへの応答に情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="defa5-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="defa5-105">たとえば、ラベルを使用して、テキスト ボックス、リスト ボックス、コンボ ボックス、およびようにわかりやすいキャプションを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="defa5-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="defa5-106">実行時にイベントに応答のラベルで表示されるテキストを変更するコードを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="defa5-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="defa5-107">たとえば、アプリケーションは、変更を処理するまで数分かかる、ラベルに処理ステータス メッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="defa5-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="defa5-108">ラベル コントロールの操作</span><span class="sxs-lookup"><span data-stu-id="defa5-108">Working with the Label Control</span></span>  
 <span data-ttu-id="defa5-109"><xref:System.Windows.Forms.Label>コントロールがフォーカスを受け取ることはできません、他のコントロールのアクセス キーの作成にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="defa5-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="defa5-110">アクセス キーは、ユーザーはアクセス キー、ALT キーを押すと、その他のコントロールを選択できます。</span><span class="sxs-lookup"><span data-stu-id="defa5-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="defa5-111">詳細については、次を参照してください。[アクセス キーの Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)と[する方法: Windows フォームの Label コントロールでのアクセス キーの作成](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="defa5-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="defa5-112">ラベルに表示されるキャプションに含まれている、<xref:System.Windows.Forms.Label.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="defa5-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="defa5-113"><xref:System.Windows.Forms.Label.TextAlign%2A>プロパティでは、ラベル内のテキストの配置を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="defa5-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="defa5-114">詳細については、次を参照してください。[する方法: Windows フォーム コントロールによって表示されるテキストを設定](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="defa5-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="defa5-115">参照</span><span class="sxs-lookup"><span data-stu-id="defa5-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="defa5-116">方法: Windows フォーム Label コントロールのサイズを内容に合わせて変更する</span><span class="sxs-lookup"><span data-stu-id="defa5-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="defa5-117">方法: Windows フォームの Label コントロールでアクセス キーを作成する</span><span class="sxs-lookup"><span data-stu-id="defa5-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
