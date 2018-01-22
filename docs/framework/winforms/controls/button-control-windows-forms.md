---
title: "Button コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons
- Button control [Windows Forms]
ms.assetid: d38bc40c-8040-4f19-9e88-2c665b0ab80b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f9720f26458f3dd9cb2411d123fa830b20f3fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="button-control-windows-forms"></a><span data-ttu-id="0b8a4-102">Button コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="0b8a4-102">Button Control (Windows Forms)</span></span>
<span data-ttu-id="0b8a4-103">Windows フォームの `Button` コントロールを使用すると、ユーザーはそれをクリックしてアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-103">The Windows Forms `Button` control allows the user to click it to perform an action.</span></span> <span data-ttu-id="0b8a4-104">`Button` コントロールには、テキストとイメージの両方を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-104">The `Button` control can display both text and images.</span></span> <span data-ttu-id="0b8a4-105">ボタンをクリックすると、ボタンを実際に押して離したかのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-105">When the button is clicked, it looks as if it is being pushed in and released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b8a4-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0b8a4-106">In This Section</span></span>  
 [<span data-ttu-id="0b8a4-107">Button コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="0b8a4-107">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 <span data-ttu-id="0b8a4-108">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="0b8a4-109">方法: Windows フォームのボタンのクリックに応答する</span><span class="sxs-lookup"><span data-stu-id="0b8a4-109">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 <span data-ttu-id="0b8a4-110">Windows フォームでのボタンの基本的な使用法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-110">Explains the most basic use of a button on a Windows Form.</span></span>  
  
 [<span data-ttu-id="0b8a4-111">方法: Windows フォームの Button コントロールを承認ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="0b8a4-111">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 <span data-ttu-id="0b8a4-112">`Button` コントロールを承認ボタン (既定のボタン) として設定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-112">Explains how to designate a `Button` control to be the accept button, also known as the default button.</span></span>  
  
 [<span data-ttu-id="0b8a4-113">方法: Windows フォームの Button コントロールをキャンセル ボタンとして指定する</span><span class="sxs-lookup"><span data-stu-id="0b8a4-113">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 <span data-ttu-id="0b8a4-114">`Button` コントロールをキャンセル ボタンとして設定する方法を説明します。このボタンは、ユーザーが Esc キーを押すとクリックされます</span><span class="sxs-lookup"><span data-stu-id="0b8a4-114">Explains how to designate a `Button` control to be the cancel button, which is clicked whenever the user presses the ESC key.</span></span>  
  
 [<span data-ttu-id="0b8a4-115">Windows フォームの Button コントロールを選択する方法</span><span class="sxs-lookup"><span data-stu-id="0b8a4-115">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 <span data-ttu-id="0b8a4-116">ボタンを選択する方法の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-116">Lists methods of selecting a button.</span></span>  
  
 <span data-ttu-id="0b8a4-117">参照してください[する方法: デザイナーとして受け入れるボタンを使用して、Windows フォームの button コントロールを指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)と[する方法: デザイナーをキャンセル ボタンを使用して、として Windows フォームの button コントロールを指定する](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-117">Also see [How to: Designate a Windows Forms Button as the Accept Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md) and [How to: Designate a Windows Forms Button as the Cancel Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0b8a4-118">参照</span><span class="sxs-lookup"><span data-stu-id="0b8a4-118">Reference</span></span>  
 <span data-ttu-id="0b8a4-119"><xref:System.Windows.Forms.Button> クラス</span><span class="sxs-lookup"><span data-stu-id="0b8a4-119"><xref:System.Windows.Forms.Button> class</span></span>  
 <span data-ttu-id="0b8a4-120">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b8a4-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b8a4-121">Related Sections</span></span>  
 [<span data-ttu-id="0b8a4-122">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="0b8a4-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="0b8a4-123">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-123">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 <span data-ttu-id="0b8a4-124">参照してください[ダイアログ ボックスにユーザー入力](http://msdn.microsoft.com/library/63ad8645-6842-45e8-b215-73f778e29a55)と[する方法: ダイアログ ボックスを閉じて、ユーザー入力を保持する](http://msdn.microsoft.com/library/9e118fad-3bf4-4f70-a3de-a0cda2b0229d)です。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-124">Also see [User Input to Dialog Boxes](http://msdn.microsoft.com/library/63ad8645-6842-45e8-b215-73f778e29a55) and [How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/9e118fad-3bf4-4f70-a3de-a0cda2b0229d).</span></span>
