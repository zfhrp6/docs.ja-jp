---
title: ShouldSerialize メソッドと Reset メソッドによる既定値の定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 8d7645e8de5edee711c30bbe7edde8ba7b5b1dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize メソッドと Reset メソッドによる既定値の定義
`ShouldSerialize` `Reset`プロパティ用に指定できるオプションのメソッドは、プロパティがない場合、単純な既定値があります。 プロパティの単純な既定値が、適用してください、<xref:System.ComponentModel.DefaultValueAttribute>し、代わりに、属性クラスのコンス トラクターを既定値を指定します。 これらのメカニズムのいずれかにより、デザイナーで、次の機能。  
  
-   プロパティが既定値から変更された場合に、プロパティ ブラウザーで表示を提供します。  
  
-   ユーザーが、プロパティを右クリックし、選択**リセット**プロパティを既定値に復元します。  
  
-   デザイナーより効率的なコードを生成します。  
  
    > [!NOTE]
    >  適用するか、<xref:System.ComponentModel.DefaultValueAttribute>提供または`Reset` *PropertyName*と`ShouldSerialize` *PropertyName*メソッドです。 どちらも使用しないでください。  
  
 `Reset` *PropertyName*メソッドは、次のコード フラグメントで示すように、既定値にプロパティを設定します。  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  プロパティがない場合、`Reset`メソッド、されていない、 <xref:System.ComponentModel.DefaultValueAttribute>、および、その宣言で指定された既定値はありません、`Reset`オプションのショートカット メニューでそのプロパティは無効になって、 **のプロパティ** Visual Studio での Windows フォーム デザイナーのウィンドウ。  
  
 Visual Studio などのデザイナーを使用して、 `ShouldSerialize` *PropertyName*プロパティが既定値から変更されたかどうかを確認し、プロパティ場合にのみフォームにコードを記述する方法を変更すると、のでより効率的なコード生成します。 例えば:  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 完全なコード例に従います。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 ここでは、プライベート変数の値がからアクセスする場合でも、`MyFont`プロパティは`null`、プロパティ ブラウザーは表示されません`null`代わりに、表示、<xref:System.Windows.Forms.Control.Font%2A>されていない場合は、親のプロパティ`null`、。既定値または<xref:System.Windows.Forms.Control.Font%2A>で定義された値<xref:System.Windows.Forms.Control>です。 既定値ため`MyFont`、単に設定することはできませんと<xref:System.ComponentModel.DefaultValueAttribute>このプロパティには適用できません。 代わりに、`ShouldSerialize`と`Reset`のメソッドを実装する必要があります、`MyFont`プロパティです。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [プロパティの定義](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [プロパティ変更イベント](../../../../docs/framework/winforms/controls/property-changed-events.md)
