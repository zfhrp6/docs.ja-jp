---
title: "ListBox の代わりに Windows フォーム ComboBox を使用する場合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c4a2886dae3aee147d80957874d0d98714c0ca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox の代わりに Windows フォーム ComboBox を使用する場合
<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>コントロール似たような動作は、でき、場合によっては同義です。 ただしが 1 つまたはもう一方のタスクをより適切な時間があります。  
  
 一般に、コンボ ボックスが適して、推奨される選択肢の一覧があるし、リスト ボックスは、一覧にあるものへの入力を制限する場合に適しています。 コンボ ボックスには、一覧にない値を入力するためのテキスト ボックスのフィールドが含まれています。 例外は、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されている<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>です。 その場合は、コントロールが選択項目の最初の文字を入力するされます。  
  
 さらに、コンボ ボックスは、フォームの領域を節約します。 下向きの矢印をクリックするまでに、完全な一覧が表示されていないために、コンボ ボックスは、リスト ボックスが収まらない小さなスペースに簡単に適合できます。 ときに例外が、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されている<xref:System.Windows.Forms.ComboBoxStyle.Simple>: 完全な一覧が表示され、コンボ ボックスは、リスト ボックスの場合よりもさらにスペースを占有します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
