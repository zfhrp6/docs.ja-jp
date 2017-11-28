---
title: "方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする"
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
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac74e50eb6558c38d46714dd7bfe0cfd61133ac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a><span data-ttu-id="9af68-102">方法 : Windows フォームで ToolStrip コントロールの AutoComplete を有効にする</span><span class="sxs-lookup"><span data-stu-id="9af68-102">How to: Enable AutoComplete in ToolStrip Controls in Windows Forms</span></span>
<span data-ttu-id="9af68-103">次の手順を組み合わせて、<xref:System.Windows.Forms.ToolStripLabel>で、<xref:System.Windows.Forms.ToolStripComboBox>を削除できる最近など、アイテムの一覧を表示する Web サイトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9af68-103">The following procedure combines a <xref:System.Windows.Forms.ToolStripLabel> with a <xref:System.Windows.Forms.ToolStripComboBox> that can be dropped down to show a list of items, such as recently visited Web sites.</span></span> <span data-ttu-id="9af68-104">リスト内の項目のいずれかの最初の文字に一致する文字を入力すると、アイテムがすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9af68-104">If the user types a character that matches the first character of one of the items in the list, the item is immediately displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9af68-105">オート コンプリートと協力`ToolStrip`と連携して従来のコントロールなどのと同じ方法でコントロール<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="9af68-105">Automatic completion works with `ToolStrip` controls in the same way that it works with traditional controls such as <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a><span data-ttu-id="9af68-106">ToolStrip コントロールの AutoComplete を有効にするには</span><span class="sxs-lookup"><span data-stu-id="9af68-106">To enable AutoComplete in a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="9af68-107">作成、<xref:System.Windows.Forms.ToolStrip>を制御し、項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="9af68-107">Create a <xref:System.Windows.Forms.ToolStrip> control and add items to it.</span></span>  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
    ```  
  
2.  <span data-ttu-id="9af68-108">設定、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>ラベルにコンボ ボックスのプロパティに<xref:System.Windows.Forms.ToolStripItemOverflow.Never>リストが常に、フォームのサイズに関係なく使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9af68-108">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the label and the combo box to <xref:System.Windows.Forms.ToolStripItemOverflow.Never> so that the list is always available regardless of the form's size.</span></span>  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
3.  <span data-ttu-id="9af68-109">単語、項目のコレクションに追加、<xref:System.Windows.Forms.ToolStripComboBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9af68-109">Add words to the Items collection of the <xref:System.Windows.Forms.ToolStripComboBox> control.</span></span>  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  <span data-ttu-id="9af68-110">設定、<xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A>コンボ ボックスのプロパティ<xref:System.Windows.Forms.AutoCompleteMode.Append>です。</span><span class="sxs-lookup"><span data-stu-id="9af68-110">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteMode.Append>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  <span data-ttu-id="9af68-111">設定、<xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A>コンボ ボックスのプロパティ<xref:System.Windows.Forms.AutoCompleteSource.ListItems>です。</span><span class="sxs-lookup"><span data-stu-id="9af68-111">Set the <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> property of the combo box to <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.</span></span>  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9af68-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9af68-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripLabel>  
 <xref:System.Windows.Forms.ToolStripComboBox>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>  
 [<span data-ttu-id="9af68-113">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="9af68-113">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="9af68-114">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9af68-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="9af68-115">ToolStrip テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="9af68-115">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
