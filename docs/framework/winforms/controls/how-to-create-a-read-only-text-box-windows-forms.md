---
title: "方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="35867-102">方法 : 読み取り専用テキスト ボックスを作成する (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="35867-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="35867-103">編集可能な Windows フォームのテキスト ボックスは読み取り専用のコントロールに変換できます。</span><span class="sxs-lookup"><span data-stu-id="35867-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="35867-104">たとえば、テキスト ボックスでは、通常は編集されますが、できない場合があります現時点では、アプリケーションの状態のための値を表示可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35867-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="35867-105">読み取り専用テキスト ボックスを作成するには</span><span class="sxs-lookup"><span data-stu-id="35867-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="35867-106">設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="35867-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="35867-107">プロパティ設定された`true`ユーザーがまだスクロールして変更を許可せずにテキスト ボックス内のテキストを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="35867-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="35867-108">A**コピー**コマンドがテキスト ボックスでは、機能が、**切り取り**と**貼り付け**のコマンドはできません。</span><span class="sxs-lookup"><span data-stu-id="35867-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35867-109"><xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>プロパティでは、実行時にユーザーとの対話のみに影響します。</span><span class="sxs-lookup"><span data-stu-id="35867-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="35867-110">まだ変更テキスト ボックスの内容プログラムで実行時に変更することによって、<xref:System.Windows.Forms.TextBox.Text%2A>テキスト ボックスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="35867-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35867-111">参照</span><span class="sxs-lookup"><span data-stu-id="35867-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="35867-112">TextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="35867-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="35867-113">方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="35867-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="35867-114">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="35867-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="35867-115">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="35867-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="35867-116">方法: Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="35867-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="35867-117">方法: Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="35867-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="35867-118">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="35867-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
