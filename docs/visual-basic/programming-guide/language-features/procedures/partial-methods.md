---
title: "部分メソッド (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ebedd6f8173e3c349240d24ddaf16e4841f67a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="2a35e-102">部分メソッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a35e-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="2a35e-103">部分メソッドでは、開発者はカスタム ロジックをコードに挿入を有効にします。</span><span class="sxs-lookup"><span data-stu-id="2a35e-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="2a35e-104">通常、コードは、デザイナーで生成されたクラスの一部です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="2a35e-105">部分メソッドはコード ジェネレーターによって作成される部分クラスで定義され、何かが変更されたことを通知によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="2a35e-106">開発者は、変更に応じて、カスタム動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="2a35e-107">コード ジェネレーターのデザイナーは、メソッドのシグネチャのみと 1 つまたは複数のメソッドの呼び出しを定義します。</span><span class="sxs-lookup"><span data-stu-id="2a35e-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="2a35e-108">開発者は、生成されたコードの動作をカスタマイズする場合は、メソッドの実装を提供し、できます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="2a35e-109">実装を指定しない場合、メソッドの呼び出しは、追加のパフォーマンスのオーバーヘッドなしでその結果、コンパイラによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="2a35e-110">宣言</span><span class="sxs-lookup"><span data-stu-id="2a35e-110">Declaration</span></span>  
 <span data-ttu-id="2a35e-111">キーワードを配置することによって、生成されたコードは部分メソッドの定義をマーク`Partial`シグネチャ行の開始時にします。</span><span class="sxs-lookup"><span data-stu-id="2a35e-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="2a35e-112">定義には、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a35e-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="2a35e-113">メソッドである必要があります、`Sub`ではなく、`Function`です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="2a35e-114">メソッドの本文は空のままにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a35e-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="2a35e-115">アクセス修飾子がある必要があります`Private`です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="2a35e-116">実装</span><span class="sxs-lookup"><span data-stu-id="2a35e-116">Implementation</span></span>  
 <span data-ttu-id="2a35e-117">実装では、主に、部分メソッドの本体に入力します。</span><span class="sxs-lookup"><span data-stu-id="2a35e-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="2a35e-118">実装は、定義から別個の部分クラスでは、通常れ、生成されたコードを拡張する必要が開発者によって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="2a35e-119">前の例が、宣言内の署名を正確に複製がバリエーションが可能です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="2a35e-120">具体的には、その他の修飾子を追加できるように`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="2a35e-121">1 つだけ`Overrides`修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a35e-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="2a35e-122">メソッドの修飾子の詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="2a35e-123">用途</span><span class="sxs-lookup"><span data-stu-id="2a35e-123">Use</span></span>  
 <span data-ttu-id="2a35e-124">同じように呼び出します、他の部分メソッドを呼び出す`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="2a35e-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="2a35e-125">メソッドが実装されている場合、引数が評価され、メソッドの本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="2a35e-126">ただし、部分メソッドの実装が省略可能なことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2a35e-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="2a35e-127">メソッドが実装されていない場合それへの呼び出しも何も起こりません、およびメソッドに引数として渡された式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="2a35e-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a35e-128">例</span><span class="sxs-lookup"><span data-stu-id="2a35e-128">Example</span></span>  
 <span data-ttu-id="2a35e-129">Product.Designer.vb をという名前のファイル、定義、`Product`を持つクラス、`Quantity`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2a35e-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="2a35e-130">実装を提供 Product.vb をという名前のファイル、`QuantityChanged`です。</span><span class="sxs-lookup"><span data-stu-id="2a35e-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="2a35e-131">最後に、プロジェクトの Main メソッドで次のように宣言します。、`Product`インスタンスとの初期値を提供、`Quantity`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="2a35e-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="2a35e-132">このメッセージが表示されるメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a35e-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="2a35e-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a35e-133">See Also</span></span>  
 [<span data-ttu-id="2a35e-134">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2a35e-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2a35e-135">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="2a35e-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="2a35e-136">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="2a35e-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="2a35e-137">Partial</span><span class="sxs-lookup"><span data-stu-id="2a35e-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="2a35e-138">LINQ to SQL でのコード生成</span><span class="sxs-lookup"><span data-stu-id="2a35e-138">Code Generation in LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb399400)  
 [<span data-ttu-id="2a35e-139">部分メソッドを使用してビジネス ロジックを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a35e-139">Adding Business Logic By Using Partial Methods</span></span>](https://msdn.microsoft.com/library/bb546176)
