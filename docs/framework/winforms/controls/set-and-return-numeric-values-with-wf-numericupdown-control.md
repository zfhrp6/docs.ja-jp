---
title: '方法 : Windows フォームの NumericUpDown コントロールを使用して数値を設定および取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: e214f556224577c3029b2b742784e58932d792f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535562"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>方法 : Windows フォームの NumericUpDown コントロールを使用して数値を設定および取得する
Windows フォームの数値<xref:System.Windows.Forms.NumericUpDown>コントロールはによって決定されます。 その<xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティです。 他のプロパティと同様に、コントロールの値に対する条件テストを記述できます。 1 回、<xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティが設定されてで、操作を実行するコードの記述で直接調整することができます、または呼び出すことができます、<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>と<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>メソッドです。  
  
### <a name="to-set-the-numeric-value"></a>数値の値を設定するには  
  
1.  値を割り当てる、<xref:System.Windows.Forms.NumericUpDown.Value%2A>コードまたはで、[プロパティ] ウィンドウのプロパティです。  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     - または -  
  
2.  呼び出す、<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>または<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>メソッドで指定した量によって、値を増減させて、<xref:System.Windows.Forms.NumericUpDown.Increment%2A>プロパティです。  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>数値の値を返す  
  
-   アクセス、<xref:System.Windows.Forms.NumericUpDown.Value%2A>コード内のプロパティです。  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.NumericUpDown>  
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>  
 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
