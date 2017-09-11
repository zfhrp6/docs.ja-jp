---
title: "方法: プロパティ (Visual Basic) に値を格納 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c838141a27c30b11765d30ae8b0c19bccc929f4b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="805d0-102">方法: プロパティに値を格納する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="805d0-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="805d0-103">プロパティに値を格納するには、代入ステートメントの左側にあるプロパティ名を置きます。</span><span class="sxs-lookup"><span data-stu-id="805d0-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="805d0-104">プロパティの`Set`プロシージャは値を格納するが、明示的に呼び出さないことを名前です。</span><span class="sxs-lookup"><span data-stu-id="805d0-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="805d0-105">変数と同じように、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="805d0-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="805d0-106">プロパティのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="805d0-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="805d0-107">プロパティの値を格納するには</span><span class="sxs-lookup"><span data-stu-id="805d0-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="805d0-108">代入ステートメントの左側にあるプロパティの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="805d0-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="805d0-109">次の例の値の設定、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay`プロパティ、正午を暗黙的に呼び出す、`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="805d0-109">The following example sets the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     <span data-ttu-id="805d0-110">[!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="805d0-110">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="805d0-111">プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。</span><span class="sxs-lookup"><span data-stu-id="805d0-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="805d0-112">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="805d0-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="805d0-113">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="805d0-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="805d0-114">プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="805d0-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="805d0-115">代入ステートメントの右側にある生成された値は、このプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="805d0-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805d0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="805d0-116">See Also</span></span>  
 <span data-ttu-id="805d0-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="805d0-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span></span>   
<span data-ttu-id="805d0-118"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-118"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="805d0-119"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-119"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="805d0-120"> [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-120"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="805d0-121"> [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-121"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="805d0-122"> [方法: プロパティを作成します。](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-122"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="805d0-123"> [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-123"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="805d0-124"> [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-124"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="805d0-125"> [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="805d0-125"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="805d0-126"> [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="805d0-126"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
