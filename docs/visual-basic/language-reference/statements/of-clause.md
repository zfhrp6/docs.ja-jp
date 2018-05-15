---
title: Of 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 9ace0ad55d9eb1618dbdafb0d49d1ff4b169a877
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="5d4a3-102">Of 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d4a3-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="5d4a3-103">導入されています、`Of`句であることを識別、*パラメーター入力*上、*ジェネリック*クラス、構造体、インターフェイス、デリゲート、またはプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="5d4a3-104">ジェネリック型については、次を参照してください。 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="5d4a3-105">使用して、キーワードの</span><span class="sxs-lookup"><span data-stu-id="5d4a3-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="5d4a3-106">次のコード例では、`Of`キーワードを次の 2 つの型パラメーターを受け取るクラスの輪郭の定義します。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="5d4a3-107">これは、*制約*、`keyType`によってパラメーター、<xref:System.IComparable>インターフェイスで、利用側のコードを実装する型引数を指定する必要がありますを意味<xref:System.IComparable>です。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="5d4a3-108">これは、必要なできるように、`add`プロシージャを呼び出すことができます、<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5d4a3-109">制約の詳細については、次を参照してください。[型リスト](../../../visual-basic/language-reference/statements/type-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="5d4a3-110">上記のクラス定義を完了する場合は、さまざまなを構築できます`dictionary`からクラスです。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="5d4a3-111">指定する種類`entryType`と`keyType`エントリの種類、クラスを保持し、各エントリに関連付けるキーの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="5d4a3-112">制約のために指定する必要があります`keyType`を実装する型<xref:System.IComparable>です。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="5d4a3-113">次のコード例を保持するオブジェクトを作成する`String`エントリと関連付け、 `Integer` 1 つずつキー。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="5d4a3-114">`Integer` 実装する<xref:System.IComparable>し、そのために、制約を満たす`keyType`です。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="5d4a3-115">キーワード `Of` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d4a3-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5d4a3-116">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="5d4a3-117">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="5d4a3-118">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5d4a3-119">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="5d4a3-120">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="5d4a3-121">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4a3-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d4a3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d4a3-122">See Also</span></span>  
 <xref:System.IComparable>  
 [<span data-ttu-id="5d4a3-123">型リスト</span><span class="sxs-lookup"><span data-stu-id="5d4a3-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="5d4a3-124">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="5d4a3-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="5d4a3-125">In</span><span class="sxs-lookup"><span data-stu-id="5d4a3-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="5d4a3-126">Out</span><span class="sxs-lookup"><span data-stu-id="5d4a3-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
