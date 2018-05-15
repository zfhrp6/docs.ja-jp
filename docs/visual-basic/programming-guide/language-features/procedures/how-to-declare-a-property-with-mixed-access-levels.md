---
title: '方法: 複数のアクセス レベルを持つプロパティを宣言する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 8d25086fe6f8b5f5300006466ef49782cb065edf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="e8baa-102">方法: 複数のアクセス レベルを持つプロパティを宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8baa-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="e8baa-103">場合は、`Get`と`Set`手順異なるアクセス レベルを設定するプロパティについてでさらに小さくレベルを使用することができます、`Property`ステートメントといずれかより制限の厳しいレベル、`Get`または`Set`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="e8baa-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="e8baa-104">プロパティの値を取得することができるコードの特定の部分と値を変更することができるコードの他の特定部分したい場合は、プロパティに混合アクセス レベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="e8baa-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="e8baa-105">アクセス レベルの詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="e8baa-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="e8baa-106">混合アクセス レベルを持つプロパティを宣言するには</span><span class="sxs-lookup"><span data-stu-id="e8baa-106">To declare a property with mixed access levels</span></span>  
  
1.  <span data-ttu-id="e8baa-107">通常の方法でプロパティを宣言し、制限の緩いアクセス レベルを指定します (など`Public`) で、`Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e8baa-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2.  <span data-ttu-id="e8baa-108">宣言するか、`Get`または`Set`より制限の厳しいアクセス レベルを指定する手順 (など`Friend`)。</span><span class="sxs-lookup"><span data-stu-id="e8baa-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3.  <span data-ttu-id="e8baa-109">その他のプロパティ プロシージャでは、アクセス レベルを指定しません。</span><span class="sxs-lookup"><span data-stu-id="e8baa-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="e8baa-110">宣言されているアクセス レベルを想定しています、`Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e8baa-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="e8baa-111">プロパティ プロシージャの 1 つのみにアクセスを制限することができます。</span><span class="sxs-lookup"><span data-stu-id="e8baa-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     <span data-ttu-id="e8baa-112">前の例で、`Get`手順では、同じ`Protected`自体のプロパティとしてアクセス中に、`Set`手順では`Private`アクセスします。</span><span class="sxs-lookup"><span data-stu-id="e8baa-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="e8baa-113">派生したクラス`employee`読み取ることができます、`salary`値しか、`employee`クラスで設定できます。</span><span class="sxs-lookup"><span data-stu-id="e8baa-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8baa-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8baa-114">See Also</span></span>  
 [<span data-ttu-id="e8baa-115">手順</span><span class="sxs-lookup"><span data-stu-id="e8baa-115">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="e8baa-116">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e8baa-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="e8baa-117">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="e8baa-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e8baa-118">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e8baa-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="e8baa-119">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="e8baa-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="e8baa-120">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="e8baa-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="e8baa-121">方法 : プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e8baa-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="e8baa-122">方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e8baa-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="e8baa-123">方法 : プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="e8baa-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="e8baa-124">方法 : プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="e8baa-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
