---
title: 部分メソッド (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: a1708c1d953a60429c1bd87fd858da5c50a3e759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="bb8f7-102">部分メソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb8f7-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="bb8f7-103">部分メソッドでは、開発者はカスタム ロジックをコードに挿入を有効にします。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="bb8f7-104">通常、コードは、デザイナーで生成されたクラスの一部です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="bb8f7-105">部分メソッドはコード ジェネレーターによって作成される部分クラスで定義され、何かが変更されたことを通知によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="bb8f7-106">開発者は、変更に応じて、カスタム動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="bb8f7-107">コード ジェネレーターのデザイナーは、メソッドのシグネチャのみと 1 つまたは複数のメソッドの呼び出しを定義します。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="bb8f7-108">開発者は、生成されたコードの動作をカスタマイズする場合は、メソッドの実装を提供し、できます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="bb8f7-109">実装を指定しない場合、メソッドの呼び出しは、追加のパフォーマンスのオーバーヘッドなしでその結果、コンパイラによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="bb8f7-110">宣言</span><span class="sxs-lookup"><span data-stu-id="bb8f7-110">Declaration</span></span>  
 <span data-ttu-id="bb8f7-111">キーワードを配置することによって、生成されたコードは部分メソッドの定義をマーク`Partial`シグネチャ行の開始時にします。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="bb8f7-112">定義には、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="bb8f7-113">メソッドである必要があります、`Sub`ではなく、`Function`です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="bb8f7-114">メソッドの本文は空のままにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="bb8f7-115">アクセス修飾子がある必要があります`Private`です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="bb8f7-116">実装</span><span class="sxs-lookup"><span data-stu-id="bb8f7-116">Implementation</span></span>  
 <span data-ttu-id="bb8f7-117">実装では、主に、部分メソッドの本体に入力します。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="bb8f7-118">実装は、定義から別個の部分クラスでは、通常れ、生成されたコードを拡張する必要が開発者によって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="bb8f7-119">前の例が、宣言内の署名を正確に複製がバリエーションが可能です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="bb8f7-120">具体的には、その他の修飾子を追加できるように`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="bb8f7-121">1 つだけ`Overrides`修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="bb8f7-122">メソッドの修飾子の詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="bb8f7-123">使用</span><span class="sxs-lookup"><span data-stu-id="bb8f7-123">Use</span></span>  
 <span data-ttu-id="bb8f7-124">同じように呼び出します、他の部分メソッドを呼び出す`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="bb8f7-125">メソッドが実装されている場合、引数が評価され、メソッドの本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="bb8f7-126">ただし、部分メソッドの実装が省略可能なことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="bb8f7-127">メソッドが実装されていない場合それへの呼び出しも何も起こりません、およびメソッドに引数として渡された式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb8f7-128">例</span><span class="sxs-lookup"><span data-stu-id="bb8f7-128">Example</span></span>  
 <span data-ttu-id="bb8f7-129">Product.Designer.vb をという名前のファイル、定義、`Product`を持つクラス、`Quantity`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="bb8f7-130">実装を提供 Product.vb をという名前のファイル、`QuantityChanged`です。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="bb8f7-131">最後に、プロジェクトの Main メソッドで次のように宣言します。、`Product`インスタンスとの初期値を提供、`Quantity`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="bb8f7-132">このメッセージが表示されるメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb8f7-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="bb8f7-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb8f7-133">See Also</span></span>  
 [<span data-ttu-id="bb8f7-134">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="bb8f7-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="bb8f7-135">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="bb8f7-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="bb8f7-136">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="bb8f7-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="bb8f7-137">Partial</span><span class="sxs-lookup"><span data-stu-id="bb8f7-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="bb8f7-138">LINQ to SQL でのコード生成</span><span class="sxs-lookup"><span data-stu-id="bb8f7-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="bb8f7-139">部分メソッドによるビジネス ロジックの追加</span><span class="sxs-lookup"><span data-stu-id="bb8f7-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
