---
title: "方法: プロパティ (Visual Basic の場合) から値を取得 |Microsoft ドキュメント"
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
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
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
ms.openlocfilehash: 719a4fc9ff163fb4437ea40c8265a5e36232347e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="a49de-102">方法: プロパティから値を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a49de-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="a49de-103">プロパティの値を取得するには、式の中でプロパティ名を含めます。</span><span class="sxs-lookup"><span data-stu-id="a49de-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="a49de-104">プロパティの`Get`プロシージャが値を取得が明示的に呼び出さないことを名前です。</span><span class="sxs-lookup"><span data-stu-id="a49de-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="a49de-105">変数と同じように、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a49de-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a49de-106">プロパティのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a49de-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="a49de-107">プロパティから値を取得するには</span><span class="sxs-lookup"><span data-stu-id="a49de-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="a49de-108">式の中で変数名を使用すると同じように対応するプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="a49de-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="a49de-109">プロパティを使用する変数または定数を使用する任意の場所。</span><span class="sxs-lookup"><span data-stu-id="a49de-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="a49de-110">または</span><span class="sxs-lookup"><span data-stu-id="a49de-110">-or-</span></span>  
  
     <span data-ttu-id="a49de-111">後に続くプロパティ名を使用して (`=`)、代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="a49de-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="a49de-112">次の例は、値を読み取って、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now`プロパティには、暗黙的に呼び出すことの`Get`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="a49de-112">The following example reads the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="a49de-113">[!code-vb[VbVbalrDateProperties&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a49de-113">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="a49de-114">プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。</span><span class="sxs-lookup"><span data-stu-id="a49de-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a49de-115">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="a49de-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="a49de-116">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="a49de-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a49de-117">プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a49de-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="a49de-118">プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a49de-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49de-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a49de-119">See Also</span></span>  
 <span data-ttu-id="a49de-120">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-120">[Procedures](./index.md) </span></span>  
<span data-ttu-id="a49de-121"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="a49de-122"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-122"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a49de-123"> [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-123"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="a49de-124"> [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-124"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="a49de-125"> [方法: プロパティを作成します。](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-125"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="a49de-126"> [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-126"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="a49de-127"> [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-127"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="a49de-128"> [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="a49de-128"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="a49de-129"> [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="a49de-129"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md)</span></span>
