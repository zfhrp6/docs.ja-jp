---
title: "方法: 新しい変数 (Visual Basic) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Dim statement
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 3b5aa4e5e0b84f41ac3df73bc70d8402d10b21a2
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="84590-102">方法: 新しい変数を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84590-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="84590-103">変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="84590-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="84590-104">新しい変数を作成するには</span><span class="sxs-lookup"><span data-stu-id="84590-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="84590-105">変数を宣言、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84590-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="84590-106">変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、[シャドウ](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)します。</span><span class="sxs-lookup"><span data-stu-id="84590-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="84590-107">詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)します。</span><span class="sxs-lookup"><span data-stu-id="84590-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="84590-108">必要としない、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。</span><span class="sxs-lookup"><span data-stu-id="84590-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="84590-109">従う必要があります変数の名前の仕様に従う[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]規則と規約。</span><span class="sxs-lookup"><span data-stu-id="84590-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rules and conventions.</span></span> <span data-ttu-id="84590-110">詳細については、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="84590-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="84590-111">名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句、変数のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="84590-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="84590-112">既定値を使用して、データ型を指定しない場合:`Object`です。</span><span class="sxs-lookup"><span data-stu-id="84590-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="84590-113">次の`As`等号 (=) を含む句 (`=`) 変数の初期値を等号 (=) に従います。</span><span class="sxs-lookup"><span data-stu-id="84590-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="84590-114">実行するたびに、指定した値を変数に代入、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84590-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="84590-115">初期値を指定しなかった場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を含むコードが最初に入ると、変数のデータ型の既定の初期値を割り当てる、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="84590-115">If you do not specify an initial value, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="84590-116">含めることによって、クラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)のキーワード、`As`句。</span><span class="sxs-lookup"><span data-stu-id="84590-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="84590-117">使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)します。</span><span class="sxs-lookup"><span data-stu-id="84590-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84590-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="84590-118">See Also</span></span>  
 <span data-ttu-id="84590-119">[変数](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="84590-119">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="84590-120"> [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="84590-120"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="84590-121"> [宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="84590-121"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="84590-122"> [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="84590-122"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="84590-123"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="84590-123"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="84590-124"> [ステートメント](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="84590-124"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="84590-125"> [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="84590-125"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="84590-126"> [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span><span class="sxs-lookup"><span data-stu-id="84590-126"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span></span>

