---
title: "方法 : 内在コントロールのプロパティを公開する"
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
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="45afb-102">方法 : 内在コントロールのプロパティを公開する</span><span class="sxs-lookup"><span data-stu-id="45afb-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="45afb-103">複合コントロールを構成するコントロールが呼び出されます*内在コントロール*です。</span><span class="sxs-lookup"><span data-stu-id="45afb-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="45afb-104">これらのコントロールは、通常、プライベートとして宣言し、ため、開発者がアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="45afb-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="45afb-105">以降のユーザーにこれらのコントロールのプロパティを使用できるようにする場合は、ユーザーに公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45afb-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="45afb-106">内在コントロールのプロパティは、ユーザー コントロールでプロパティを作成および使用によって公開される、`get`と`set`内在コントロールのプライベート プロパティの変更を有効にするためのプロパティのアクセサー。</span><span class="sxs-lookup"><span data-stu-id="45afb-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="45afb-107">という名前の構成要素であるボタンで、仮想的なユーザー コントロールを検討してください`MyButton`です。</span><span class="sxs-lookup"><span data-stu-id="45afb-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="45afb-108">ユーザーが要求したときに、この例では、`ConstituentButtonBackColor`プロパティに格納された値、<xref:System.Windows.Forms.Control.BackColor%2A>のプロパティ`MyButton`配信されます。</span><span class="sxs-lookup"><span data-stu-id="45afb-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="45afb-109">ユーザーには、このプロパティに値が割り当てられ、その値を自動的に渡されます、<xref:System.Windows.Forms.Control.BackColor%2A>プロパティ`MyButton`と`set`の色を変更する、コードが実行されます`MyButton`です。</span><span class="sxs-lookup"><span data-stu-id="45afb-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="45afb-110">次の例は、公開する方法を示します、<xref:System.Windows.Forms.Control.BackColor%2A>内在ボタンのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="45afb-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="45afb-111">内在コントロールのプロパティを公開するには</span><span class="sxs-lookup"><span data-stu-id="45afb-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="45afb-112">ユーザー コントロールのパブリック プロパティを作成します。</span><span class="sxs-lookup"><span data-stu-id="45afb-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="45afb-113">`get`を公開するプロパティの値を取得するコードを記述するプロパティのセクションでします。</span><span class="sxs-lookup"><span data-stu-id="45afb-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="45afb-114">`set`プロパティ、プロパティの値を公開されている、内在コントロールのプロパティに渡すコードの記述のセクションです。</span><span class="sxs-lookup"><span data-stu-id="45afb-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45afb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="45afb-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="45afb-116">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="45afb-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="45afb-117">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="45afb-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
