---
title: "方法 : Windows フォームの NumericUpDown コントロールの書式を設定する"
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
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4ff6d8e584e65482285012af351ebd1a669b806
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>方法 : Windows フォームの NumericUpDown コントロールの書式を設定する
Windows フォームでの値を表示する方法を構成する<xref:System.Windows.Forms.NumericUpDown>コントロール。 <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>プロパティ、小数点の後に表示される番号の数が以外の場合は、既定値は 0 です。 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>プロパティは、3 桁ごと、区切り記号を挿入するかどうかを決定以外の場合は、既定値は`false`します。 コントロールは、場合に、10 進数の形式ではなく 16 進数の値を表示できます、<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティに設定されている`true`; 既定値は`false`します。  
  
### <a name="to-format-the-numeric-value"></a>数値の値の書式設定  
  
-   設定して、10 進値を表示、<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>プロパティ整数と設定を<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>プロパティを`true`または`false`です。  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     - または -  
  
-   16 進数の値を設定して表示、<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティを`true`です。  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  値は、16 進数としてフォームに表示されて、場合でも他のテストを実行するには<xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティは、10 進値をテストします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
