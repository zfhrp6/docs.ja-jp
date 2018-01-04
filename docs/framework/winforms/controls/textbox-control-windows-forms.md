---
title: "TextBox コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes
- TextBox control [Windows Forms]
ms.assetid: e5a06987-8aec-4271-b196-2245ba992d62
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d606140a5be2b1770bc5a16159e96e20b0fccdd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-windows-forms"></a><span data-ttu-id="7328a-102">TextBox コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="7328a-102">TextBox Control (Windows Forms)</span></span>
<span data-ttu-id="7328a-103">Windows フォームのテキスト ボックスは、ユーザーからの入力を取得またはテキストの表示に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7328a-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="7328a-104">`TextBox`コントロールもにできる読み取り専用ですが、一般に編集可能なテキストは、使用できます。</span><span class="sxs-lookup"><span data-stu-id="7328a-104">The `TextBox` control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="7328a-105">テキスト ボックスでは、複数の行を表示、コントロールのサイズにテキストを折り返す、および基本的な書式を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="7328a-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="7328a-106">`TextBox`コントロールはテキスト コントロールに表示または入力の 1 つの形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="7328a-106">The `TextBox` control allows a single format for text displayed or entered in the control.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7328a-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7328a-107">In This Section</span></span>  
 [<span data-ttu-id="7328a-108">TextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7328a-108">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 <span data-ttu-id="7328a-109">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-109">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="7328a-110">方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="7328a-110">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 <span data-ttu-id="7328a-111">エディット コントロールが最初にフォーカスを取得したときにカーソルが表示される場所を指定するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="7328a-111">Gives directions for specifying where the insertion point appears when an edit control first gets the focus.</span></span>  
  
 [<span data-ttu-id="7328a-112">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="7328a-112">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="7328a-113">テキスト ボックスに入力した内容を非表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-113">Explains how to conceal what is typed into a text box.</span></span>  
  
 [<span data-ttu-id="7328a-114">方法: 読み取り専用テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="7328a-114">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 <span data-ttu-id="7328a-115">テキスト ボックスの内容が変更されないようにする方法をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-115">Describes how to prevent the contents of a text box from being changed.</span></span>  
  
 [<span data-ttu-id="7328a-116">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="7328a-116">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 <span data-ttu-id="7328a-117">テキスト ボックスの文字列に引用符を追加するについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-117">Explains adding quotation marks to a string in a text box.</span></span>  
  
 [<span data-ttu-id="7328a-118">方法: Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="7328a-118">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="7328a-119">テキスト ボックス内のテキストを強調表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-119">Explains how to highlight text in a text box.</span></span>  
  
 [<span data-ttu-id="7328a-120">方法: Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="7328a-120">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 <span data-ttu-id="7328a-121">スクロール可能なテキスト ボックスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7328a-121">Describes how to make a text box scrollable.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7328a-122">参照</span><span class="sxs-lookup"><span data-stu-id="7328a-122">Reference</span></span>  
 <span data-ttu-id="7328a-123"><xref:System.Windows.Forms.TextBox> クラス</span><span class="sxs-lookup"><span data-stu-id="7328a-123"><xref:System.Windows.Forms.TextBox> class</span></span>  
 <span data-ttu-id="7328a-124">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7328a-124">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7328a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7328a-125">Related Sections</span></span>  
 [<span data-ttu-id="7328a-126">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="7328a-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="7328a-127">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="7328a-127">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
