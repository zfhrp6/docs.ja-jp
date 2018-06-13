---
title: '方法: 新しい変数を作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: f2e6a97e78bc42ebea9519eb0aa4411e9aec24cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651545"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="e9e86-102">方法: 新しい変数を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9e86-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="e9e86-103">変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="e9e86-104">新しい変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="e9e86-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="e9e86-105">変数を宣言、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e9e86-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="e9e86-106">など、変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="e9e86-107">詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="e9e86-108">必要としない、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。</span><span class="sxs-lookup"><span data-stu-id="e9e86-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="e9e86-109">変数の名前は、Visual Basic の規則と規則に従う必要がありますの仕様に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e9e86-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="e9e86-110">詳細については、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="e9e86-111">名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句を変数のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9e86-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="e9e86-112">既定値を使用して、データ型を指定しない場合:`Object`です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="e9e86-113">以下の`As`等号 (=) を含む句 (`=`) し、変数の初期値を等号 (=) に従います。</span><span class="sxs-lookup"><span data-stu-id="e9e86-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="e9e86-114">実行するたびに Visual Basic に変数に指定された値が割り当てられます、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e9e86-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="e9e86-115">Visual Basic を含むコードを最初に切り替わったときに、変数のデータ型の既定の初期値が割り当てられます、初期値を指定しない場合、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e9e86-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e9e86-116">含めることによって、このクラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード、`As`句。</span><span class="sxs-lookup"><span data-stu-id="e9e86-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="e9e86-117">使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e86-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e9e86-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9e86-118">See Also</span></span>  
 [<span data-ttu-id="e9e86-119">変数</span><span class="sxs-lookup"><span data-stu-id="e9e86-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="e9e86-120">変数宣言</span><span class="sxs-lookup"><span data-stu-id="e9e86-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="e9e86-121">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="e9e86-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="e9e86-122">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="e9e86-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="e9e86-123">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="e9e86-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e9e86-124">ステートメント</span><span class="sxs-lookup"><span data-stu-id="e9e86-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="e9e86-125">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="e9e86-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="e9e86-126">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="e9e86-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
