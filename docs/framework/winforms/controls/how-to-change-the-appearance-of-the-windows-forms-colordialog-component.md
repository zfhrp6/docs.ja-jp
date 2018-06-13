---
title: '方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 816850fa61de97b5f4c251571a74da7e0a70cba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530248"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>方法 : Windows フォーム ColorDialog コンポーネントの表示形式を変更する
Windows フォームの外観を構成する<xref:System.Windows.Forms.ColorDialog>コンポーネントはそのプロパティの数。 ダイアログ ボックスには、次の 2 つのセクションでは、基本色とユーザーがカスタム カラーを定義できるいずれかを示す 1 つです。  
  
 ほとんどのプロパティは、ユーザーがダイアログ ボックスから選択できる色を制限します。 場合、<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>プロパティに設定されている`true`ユーザーがカスタム カラーを定義できるようにします。 <xref:System.Windows.Forms.ColorDialog.FullOpen%2A>プロパティは`true`カスタム カラーを定義する ダイアログ ボックスが展開されている場合それ以外の場合、ユーザー必要があります、"を定義するカスタム カラー ボタンをクリックして"です。 ときに、<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>プロパティに設定されている`true`、ダイアログ ボックスは、基本色のセットで使用可能なすべての色を表示します。 場合、<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>プロパティに設定されている`true`ユーザーがディザリングされた色を選択できません; を選択する純色のみ利用できます。  
  
 場合、<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティに設定されている`true`、ダイアログ ボックスで、[ヘルプ] ボタンが表示されます。 ユーザーがヘルプ ボタンをクリックしたときに、<xref:System.Windows.Forms.ColorDialog>コンポーネントの<xref:System.Windows.Forms.CommonDialog.HelpRequest>イベントが発生します。  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>色のダイアログ ボックスの外観を構成するには  
  
1.  設定、 <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>、 <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>、 <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>、および<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>プロパティを目的の値にします。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog コンポーネント](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [ColorDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
