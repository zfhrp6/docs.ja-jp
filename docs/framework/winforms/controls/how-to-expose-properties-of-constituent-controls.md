---
title: '方法 : 内在コントロールのプロパティを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: 8f7b5c44a5cb20b5da10df5fd630b371cc959fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532634"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>方法 : 内在コントロールのプロパティを公開する
複合コントロールを構成するコントロールが呼び出されます*内在コントロール*です。 これらのコントロールは、通常、プライベートとして宣言し、ため、開発者がアクセスできません。 以降のユーザーにこれらのコントロールのプロパティを使用できるようにする場合は、ユーザーに公開する必要があります。 内在コントロールのプロパティは、ユーザー コントロールでプロパティを作成および使用によって公開される、`get`と`set`内在コントロールのプライベート プロパティの変更を有効にするためのプロパティのアクセサー。  
  
 という名前の構成要素であるボタンで、仮想的なユーザー コントロールを検討してください`MyButton`です。 ユーザーが要求したときに、この例では、`ConstituentButtonBackColor`プロパティに格納された値、<xref:System.Windows.Forms.Control.BackColor%2A>のプロパティ`MyButton`配信されます。 ユーザーには、このプロパティに値が割り当てられ、その値を自動的に渡されます、<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ`MyButton`と`set`の色を変更する、コードが実行されます`MyButton`です。  
  
 次の例は、公開する方法を示します、<xref:System.Windows.Forms.Control.BackColor%2A>内在ボタンのプロパティ。  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>内在コントロールのプロパティを公開するには  
  
1.  ユーザー コントロールのパブリック プロパティを作成します。  
  
2.  `get`を公開するプロパティの値を取得するコードを記述するプロパティのセクションでします。  
  
3.  `set`プロパティ、プロパティの値を公開されている、内在コントロールのプロパティに渡すコードの記述のセクションです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.UserControl>  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
