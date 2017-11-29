---
title: "方法: 新しい変数を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="f7705-102">方法: 新しい変数を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7705-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="f7705-103">変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7705-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="f7705-104">新しい変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="f7705-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="f7705-105">変数を宣言、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f7705-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="f7705-106">など、変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7705-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="f7705-107">詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7705-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="f7705-108">必要としない、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。</span><span class="sxs-lookup"><span data-stu-id="f7705-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="f7705-109">変数の名前は、従う必要がありますの仕様に従う[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]規則と規約。</span><span class="sxs-lookup"><span data-stu-id="f7705-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rules and conventions.</span></span> <span data-ttu-id="f7705-110">詳細については、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7705-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="f7705-111">名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句を変数のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7705-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="f7705-112">既定値を使用して、データ型を指定しない場合:`Object`です。</span><span class="sxs-lookup"><span data-stu-id="f7705-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="f7705-113">以下の`As`等号 (=) を含む句 (`=`) し、変数の初期値を等号 (=) に従います。</span><span class="sxs-lookup"><span data-stu-id="f7705-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="f7705-114">実行するたびに、指定した値を変数に代入、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f7705-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="f7705-115">初期値を指定しない場合[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を含むコードが最初に入ると、変数のデータ型の既定の初期値を割り当てます、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f7705-115">If you do not specify an initial value, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="f7705-116">含めることによって、このクラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード、`As`句。</span><span class="sxs-lookup"><span data-stu-id="f7705-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="f7705-117">使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7705-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f7705-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7705-118">See Also</span></span>  
 [<span data-ttu-id="f7705-119">変数</span><span class="sxs-lookup"><span data-stu-id="f7705-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="f7705-120">変数宣言</span><span class="sxs-lookup"><span data-stu-id="f7705-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="f7705-121">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="f7705-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="f7705-122">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="f7705-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="f7705-123">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="f7705-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="f7705-124">ステートメント</span><span class="sxs-lookup"><span data-stu-id="f7705-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="f7705-125">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="f7705-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f7705-126">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="f7705-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
