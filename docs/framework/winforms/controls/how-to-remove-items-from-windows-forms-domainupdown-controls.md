---
title: "方法 : Windows フォームの DomainUpDown コントロールから項目を削除する"
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
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cab9bf4445c7322c1b4824f26c0821de8c58657
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>方法 : Windows フォームの DomainUpDown コントロールから項目を削除する
項目を削除するには、Windows フォームから<xref:System.Windows.Forms.DomainUpDown>コントロールを呼び出して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>または<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>クラスです。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>メソッドは、特定のアイテムを削除中に、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>メソッドは、その位置で項目を削除します。  
  
### <a name="to-remove-an-item"></a>アイテムを削除するには  
  
-   使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>名前で項目を削除するクラス。  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     または  
  
-   使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>の位置で項目を削除するメソッド。  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [DomainUpDown コントロール](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [DomainUpDown コントロールの概要](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
