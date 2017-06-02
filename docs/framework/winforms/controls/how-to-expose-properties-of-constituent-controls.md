---
title: "方法 : 内在コントロールのプロパティを公開する | Microsoft Docs"
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
  - "内在コントロール"
  - "コントロール [Windows フォーム], 内在"
  - "カスタム コントロール [Windows フォーム], 公開 (プロパティを)"
  - "ユーザー コントロール [Windows フォーム], 公開 (内在コントロールを)"
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 内在コントロールのプロパティを公開する
複合コントロールを構成するコントロールを "*内在コントロール*" と呼びます。  これらのコントロールは、通常はプライベートとして宣言されるため、開発者がアクセスすることはできません。  このようなコントロールのプロパティを後で利用できるようにする場合は、プロパティを公開する必要があります。  内在コントロールのプロパティを公開するには、ユーザー コントロールにプロパティを作成し、そのプロパティの `get` アクセサーと `set` アクセサーを使用して、内在コントロールのプライベート プロパティに変更を反映します。  
  
 `MyButton` という名前の内在ボタンを持つ、仮想のユーザー コントロールを例に考えます。  この場合、ユーザーが `ConstituentButtonBackColor` プロパティを要求すると、`MyButton` の <xref:System.Windows.Forms.Control.BackColor%2A> プロパティに格納されている値が返されます。  ユーザーがこのプロパティに値を割り当てると、値は自動的に `MyButton` の <xref:System.Windows.Forms.Control.BackColor%2A> プロパティに渡され、`set` コードが実行されて `MyButton` の色を変更します。  
  
 内在ボタンの <xref:System.Windows.Forms.Control.BackColor%2A> プロパティを公開する方法を次の例に示します。  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### 内在コントロールのプロパティを公開するには  
  
1.  ユーザー コントロールのパブリック プロパティを作成します。  
  
2.  プロパティの `get` セクションに、公開するプロパティの値を取得するコードを記述します。  
  
3.  プロパティの `set` セクションに、内在コントロールの公開されたプロパティにプロパティの値を渡すコードを記述します。  
  
## 参照  
 <xref:System.Windows.Forms.UserControl>   
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)