---
title: "ShouldSerialize メソッドと Reset メソッドによる既定値の定義 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "カスタム コントロール [Windows フォーム], プロパティ メソッド"
  - "Reset メソッド"
  - "ShouldPersist メソッド"
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# ShouldSerialize メソッドと Reset メソッドによる既定値の定義
`ShouldSerialize` メソッドと `Reset` メソッドは、プロパティに単純な既定値がない場合に、このプロパティに指定できるオプションのメソッドです。  プロパティに単純な既定値がある場合には、<xref:System.ComponentModel.DefaultValueAttribute> を適用して、属性クラス コンストラクターに既定値を指定します。  ShouldSerialize メソッドまたは Reset メソッドを使用すると、次に示す機能がデザイナーで有効になります。  
  
-   プロパティの既定値が変更された場合、変更を示すマークがプロパティ ブラウザーに表示されます。  
  
-   プロパティの既定値に戻すには、ユーザーがプロパティを右クリックして、**\[リセット\]** をクリックします。  
  
-   デザイナーで、さらに効率的なコードが生成されます。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.DefaultValueAttribute> を適用するか、`Reset`*PropertyName* メソッドと `ShouldSerialize`*PropertyName* メソッドを提供します。  この 2 種類の操作を同時に実行しないでください。  
  
 次のコードに示すように、`Reset`*PropertyName* メソッドはプロパティに既定値を設定します。  
  
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
>  `Reset` メソッドがなく、<xref:System.ComponentModel.DefaultValueAttribute> が適用されておらず、宣言で既定値が指定されていないプロパティの場合、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] の Windows フォーム デザイナーの **\[プロパティ\]** ウィンドウのショートカット メニューでは、このプロパティの `Reset` オプションが無効になります。  
  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] などのデザイナーでは、`ShouldSerialize`*PropertyName* メソッドを使用して、プロパティの既定値が変更されているかどうかを確認し、プロパティが変更されている場合にだけフォームにコードを書き込みます。これにより、コード生成処理の効率性が向上します。  次に例を示します。  
  
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
  
 完全なコード例を次に示します。  
  
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
  
 この場合、`MyFont` プロパティがアクセスするプライベート変数の値が `null` であっても、プロパティ ブラウザーには `null` は表示されません。その代わりに、親の <xref:System.Windows.Forms.Control.Font%2A> プロパティ \(`null` 以外の場合\)、または <xref:System.Windows.Forms.Control> で定義されている <xref:System.Windows.Forms.Control.Font%2A> の既定値が表示されます。  つまり、`MyFont`  プロパティの既定値を簡単に設定できないため、このプロパティには <xref:System.ComponentModel.DefaultValueAttribute> を適用できません。  代わりに、`MyFont` プロパティに対しては、`ShouldSerialize` メソッドと `Reset` メソッドを実装する必要があります。  
  
## 参照  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [プロパティの定義](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)   
 [プロパティ変更イベント](../../../../docs/framework/winforms/controls/property-changed-events.md)