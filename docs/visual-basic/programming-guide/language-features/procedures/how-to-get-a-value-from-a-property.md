---
title: '方法: プロパティから値を取得する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648409"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="3db49-102">方法: プロパティから値を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3db49-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="3db49-103">プロパティの値を取得するには、式の中で、プロパティ名を含めます。</span><span class="sxs-lookup"><span data-stu-id="3db49-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="3db49-104">プロパティの`Get`プロシージャが、値を取得しますが、呼び出すことはありません明示的にその名前でします。</span><span class="sxs-lookup"><span data-stu-id="3db49-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="3db49-105">変数を使用すると同様に、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3db49-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="3db49-106">Visual Basic では、プロパティのプロシージャ呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="3db49-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="3db49-107">プロパティから値を取得するには</span><span class="sxs-lookup"><span data-stu-id="3db49-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="3db49-108">式の中で変数名を使用するのと同様に対応するプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="3db49-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="3db49-109">プロパティを使用する変数または定数を使用する任意の場所。</span><span class="sxs-lookup"><span data-stu-id="3db49-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="3db49-110">- または -</span><span class="sxs-lookup"><span data-stu-id="3db49-110">-or-</span></span>  
  
     <span data-ttu-id="3db49-111">等号の後、プロパティ名を使用して (`=`) 代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="3db49-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="3db49-112">次の例は、Visual Basic の値を読み取ります`Now`プロパティ、暗黙的に呼び出してその`Get`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3db49-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="3db49-113">プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。</span><span class="sxs-lookup"><span data-stu-id="3db49-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="3db49-114">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="3db49-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="3db49-115">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="3db49-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="3db49-116">プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="3db49-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="3db49-117">プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3db49-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db49-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3db49-118">See Also</span></span>  
 [<span data-ttu-id="3db49-119">手順</span><span class="sxs-lookup"><span data-stu-id="3db49-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="3db49-120">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3db49-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="3db49-121">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="3db49-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3db49-122">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="3db49-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="3db49-123">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="3db49-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="3db49-124">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="3db49-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="3db49-125">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="3db49-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="3db49-126">方法 : プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3db49-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="3db49-127">方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3db49-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="3db49-128">方法 : プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="3db49-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
