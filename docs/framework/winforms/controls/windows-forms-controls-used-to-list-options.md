---
title: "オプションのリストを表示するための Windows フォーム コントロール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, listing options
- option lists in Windows Forms
ms.assetid: 5bc064c7-bc1f-4b62-8f4b-252f864b118e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e1b26ec97f4b379e6b2d75a407408b8382bca52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-controls-used-to-list-options"></a><span data-ttu-id="a87c6-102">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="a87c6-102">Windows Forms Controls Used to List Options</span></span>
<span data-ttu-id="a87c6-103">選択できるオプションの一覧をユーザーに提供する場合は、Windows フォームにさまざまなコントロールを追加できます。</span><span class="sxs-lookup"><span data-stu-id="a87c6-103">You can add a variety of controls to a Windows Form if you want to provide users with a list of options to choose from.</span></span> <span data-ttu-id="a87c6-104">量によって制限するユーザーの入力ですが、追加できます、<xref:System.Windows.Forms.ListBox>コントロール、<xref:System.Windows.Forms.ComboBox>コントロール、または<xref:System.Windows.Forms.CheckedListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a87c6-104">Depending on how much you want to restrict your users' input, you can add a <xref:System.Windows.Forms.ListBox> control, a <xref:System.Windows.Forms.ComboBox> control, or a <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="a87c6-105">次のリンクを使用して、最適なコントロールがニーズを判断します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-105">Use the following links to determine which control best suits your needs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a87c6-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a87c6-106">In This Section</span></span>  
 [<span data-ttu-id="a87c6-107">ListBox の代わりに Windows フォーム ComboBox を使用する場合</span><span class="sxs-lookup"><span data-stu-id="a87c6-107">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 <span data-ttu-id="a87c6-108">Windows フォームの制限とニーズに応じて適切なリストに基づくコントロールをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a87c6-108">Recommends an appropriate list-based control depending on the needs and restrictions of your Windows Form.</span></span>  
  
 [<span data-ttu-id="a87c6-109">方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールの特定の項目にアクセスする</span><span class="sxs-lookup"><span data-stu-id="a87c6-109">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 <span data-ttu-id="a87c6-110">指定した位置に項目を一覧が表示されますかプログラムで判断する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-110">Gives instructions for programmatically determining which item in a list appears in a given position.</span></span>  
  
 [<span data-ttu-id="a87c6-111">方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する</span><span class="sxs-lookup"><span data-stu-id="a87c6-111">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 <span data-ttu-id="a87c6-112">追加またはコントロールの項目のリストから項目を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-112">Gives instructions for adding or removing items from a control's list of items.</span></span>  
  
 [<span data-ttu-id="a87c6-113">方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する</span><span class="sxs-lookup"><span data-stu-id="a87c6-113">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)  
 <span data-ttu-id="a87c6-114">表示して、使いやすい形式のフォームのデータを格納する方法についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-114">Gives directions for displaying and storing form data in useful formats.</span></span>  
  
 [<span data-ttu-id="a87c6-115">方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドする</span><span class="sxs-lookup"><span data-stu-id="a87c6-115">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 <span data-ttu-id="a87c6-116">リストに基づくコントロールをデータ ソースにバインドするための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-116">Gives directions for binding a list-based control to a data source.</span></span>  
  
 [<span data-ttu-id="a87c6-117">方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える</span><span class="sxs-lookup"><span data-stu-id="a87c6-117">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 <span data-ttu-id="a87c6-118">データ ソースにあるリストのデータを並べ替える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-118">Explains how to sort list data at its data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a87c6-119">参照</span><span class="sxs-lookup"><span data-stu-id="a87c6-119">Reference</span></span>  
 <xref:System.Windows.Forms.CheckedListBox>  
 <span data-ttu-id="a87c6-120">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-120">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.ComboBox>  
 <span data-ttu-id="a87c6-121">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-121">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.ListBox>  
 <span data-ttu-id="a87c6-122">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-122">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a87c6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a87c6-123">Related Sections</span></span>  
 [<span data-ttu-id="a87c6-124">CheckedListBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="a87c6-124">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 <span data-ttu-id="a87c6-125">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-125">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a87c6-126">ComboBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="a87c6-126">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 <span data-ttu-id="a87c6-127">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-127">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a87c6-128">ListBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="a87c6-128">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 <span data-ttu-id="a87c6-129">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-129">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a87c6-130">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="a87c6-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="a87c6-131">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="a87c6-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
