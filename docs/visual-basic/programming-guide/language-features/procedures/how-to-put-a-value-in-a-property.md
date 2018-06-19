---
title: '方法: プロパティに値を格納する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650372"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="1654e-102">方法: プロパティに値を格納する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1654e-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="1654e-103">プロパティに値を格納するには、代入ステートメントの左側にあるプロパティの名前を置きます。</span><span class="sxs-lookup"><span data-stu-id="1654e-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="1654e-104">プロパティの`Set`プロシージャが、値を格納しますが、呼び出すことはありません明示的にその名前でします。</span><span class="sxs-lookup"><span data-stu-id="1654e-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="1654e-105">変数を使用すると同様に、プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="1654e-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="1654e-106">Visual Basic では、プロパティのプロシージャ呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="1654e-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="1654e-107">プロパティの値を格納するには</span><span class="sxs-lookup"><span data-stu-id="1654e-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="1654e-108">代入ステートメントの左側にあるプロパティの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="1654e-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="1654e-109">次の例は、Visual Basic の値を設定`TimeOfDay`プロパティ、正午を暗黙的に呼び出してその`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1654e-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="1654e-110">プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。</span><span class="sxs-lookup"><span data-stu-id="1654e-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="1654e-111">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="1654e-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="1654e-112">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="1654e-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="1654e-113">プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1654e-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="1654e-114">代入ステートメントの右側にある生成された値は、プロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1654e-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1654e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1654e-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="1654e-116">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1654e-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="1654e-117">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="1654e-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1654e-118">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="1654e-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="1654e-119">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="1654e-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="1654e-120">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="1654e-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="1654e-121">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="1654e-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="1654e-122">方法 : プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1654e-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="1654e-123">方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1654e-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="1654e-124">方法 : プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="1654e-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
