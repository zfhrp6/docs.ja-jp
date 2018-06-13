---
title: '方法 : Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 7359310b092e84b250c09153ef86d44c70d413fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526179"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>方法 : Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する
Windows フォームに項目を追加することができます<xref:System.Windows.Forms.DomainUpDown>コード内でコントロール。 呼び出す、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>または<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>をコントロールの項目を追加するクラス<xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティです。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>メソッドは、コレクションの末尾に項目を追加中に、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>メソッドが、指定した位置に項目を追加します。  
  
### <a name="to-add-a-new-item"></a>新しい項目を追加するには  
  
1.  使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>項目のリストの末尾に項目を追加します。  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     - または -  
  
2.  使用して、<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>メソッドを指定した位置にある一覧に項目を挿入します。  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [DomainUpDown コントロール](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [DomainUpDown コントロールの概要](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
