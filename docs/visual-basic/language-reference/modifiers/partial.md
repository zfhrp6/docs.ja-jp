---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: c94c3bf1a1e3e4c724f90690f52e97e8216cb9a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604615"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="2f00b-102">Partial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f00b-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="2f00b-103">型宣言が、型の部分定義であることを示します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="2f00b-104">`Partial` キーワードを使用して、型の定義を複数の宣言に分割できます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="2f00b-105">部分宣言は必要に応じていくつでも使用でき、複数のソース ファイルとして作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="2f00b-106">ただし、すべての宣言は同じアセンブリおよび同じ名前空間にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f00b-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f00b-107">Visual Basic サポート*部分メソッド*、部分クラスで実装されているが一般的です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="2f00b-108">詳細については、次を参照してください。[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)と[Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f00b-109">構文</span><span class="sxs-lookup"><span data-stu-id="2f00b-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="2f00b-110">指定項目</span><span class="sxs-lookup"><span data-stu-id="2f00b-110">Parts</span></span>  
  
|<span data-ttu-id="2f00b-111">用語</span><span class="sxs-lookup"><span data-stu-id="2f00b-111">Term</span></span>|<span data-ttu-id="2f00b-112">定義</span><span class="sxs-lookup"><span data-stu-id="2f00b-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="2f00b-113">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-113">Optional.</span></span> <span data-ttu-id="2f00b-114">この型に適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="2f00b-115">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ (`< >`)。</span><span class="sxs-lookup"><span data-stu-id="2f00b-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="2f00b-116">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-116">Optional.</span></span> <span data-ttu-id="2f00b-117">どのようなコードから型にアクセスできるのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-117">Specifies what code can access this type.</span></span> <span data-ttu-id="2f00b-118">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="2f00b-119">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-119">Optional.</span></span> <span data-ttu-id="2f00b-120">参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="2f00b-121">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-121">Optional.</span></span> <span data-ttu-id="2f00b-122">参照してください[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="2f00b-123">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-123">Optional.</span></span> <span data-ttu-id="2f00b-124">参照してください[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="2f00b-125">必須。</span><span class="sxs-lookup"><span data-stu-id="2f00b-125">Required.</span></span> <span data-ttu-id="2f00b-126">この型の名前です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-126">Name of this type.</span></span> <span data-ttu-id="2f00b-127">同じ型の他のすべての部分宣言で定義されている名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f00b-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="2f00b-128">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-128">Optional.</span></span> <span data-ttu-id="2f00b-129">これがジェネリック型であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="2f00b-130">参照してください[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="2f00b-131">使用するかどうかは必ず[の](../../../visual-basic/language-reference/statements/of-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="2f00b-132">参照してください[のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="2f00b-133">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-133">Optional.</span></span> <span data-ttu-id="2f00b-134">参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="2f00b-135">`Inherits` を使用する場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="2f00b-136">このクラスの派生元のクラスまたはインターフェイスの名前です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="2f00b-137">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-137">Optional.</span></span> <span data-ttu-id="2f00b-138">参照してください[ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="2f00b-139">`Implements` を使用する場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-139">Required if you use `Implements`.</span></span> <span data-ttu-id="2f00b-140">この型が実装するインターフェイスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="2f00b-141">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-141">Optional.</span></span> <span data-ttu-id="2f00b-142">この型の追加の変数やイベントを宣言するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="2f00b-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="2f00b-143">任意。</span><span class="sxs-lookup"><span data-stu-id="2f00b-143">Optional.</span></span> <span data-ttu-id="2f00b-144">この型の追加のプロシージャを宣言および定義するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="2f00b-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="2f00b-145">`End Class` または `End Structure`</span><span class="sxs-lookup"><span data-stu-id="2f00b-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="2f00b-146">この `Class` または `Structure` の部分定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f00b-147">コメント</span><span class="sxs-lookup"><span data-stu-id="2f00b-147">Remarks</span></span>  
 <span data-ttu-id="2f00b-148">Visual Basic では、部分クラス定義を使用して、生成されたコードとユーザーが作成したコードとを別々のソース ファイルに分離します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="2f00b-149">たとえば、**Windows フォーム デザイナー**では、<xref:System.Windows.Forms.Form> などのコントロールに部分クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="2f00b-150">これらのコントロールでは、生成されたコードを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="2f00b-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="2f00b-151">部分型を作成する際、クラス、構造体、インターフェイス、およびモジュールの作成に関するすべての規則 (修飾子の利用法や継承に関する規則など) が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="2f00b-152">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="2f00b-152">Best Practices</span></span>  
  
-   <span data-ttu-id="2f00b-153">通常の状況では、1 つの型の開発を複数の宣言に分割しないようにします。</span><span class="sxs-lookup"><span data-stu-id="2f00b-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="2f00b-154">したがって、ほとんどの場合は、`Partial` キーワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2f00b-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="2f00b-155">読みやすくするために、型の部分宣言にはすべて、`Partial` キーワードを含めます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="2f00b-156">コンパイラでは、最大 1 つの部分宣言でキーワードを省略できますが、複数の部分宣言で省略するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="2f00b-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2f00b-157">動作</span><span class="sxs-lookup"><span data-stu-id="2f00b-157">Behavior</span></span>  
  
-   <span data-ttu-id="2f00b-158">**宣言の和集合です。**</span><span class="sxs-lookup"><span data-stu-id="2f00b-158">**Union of Declarations.**</span></span> <span data-ttu-id="2f00b-159">コンパイラは型を、すべての部分宣言の共用体として扱います。</span><span class="sxs-lookup"><span data-stu-id="2f00b-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="2f00b-160">すべての部分定義で使用されているすべての修飾子は、型全体に適用され、すべての部分定義のすべてのメンバーは、型全体で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="2f00b-161">**型の昇格のモジュール内の部分型は許可されていません。**</span><span class="sxs-lookup"><span data-stu-id="2f00b-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="2f00b-162">部分定義がモジュール内にある場合、その型の上位変換は自動的に失敗します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="2f00b-163">この場合、一連の部分定義によって、予期しない結果になったり、場合によってはコンパイラ エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2f00b-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="2f00b-164">詳細については、次を参照してください。[型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f00b-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="2f00b-165">コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。</span><span class="sxs-lookup"><span data-stu-id="2f00b-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="2f00b-166">キーワード `Partial` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f00b-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2f00b-167">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="2f00b-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2f00b-168">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="2f00b-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="2f00b-169">例</span><span class="sxs-lookup"><span data-stu-id="2f00b-169">Example</span></span>  
 <span data-ttu-id="2f00b-170">次の例では、クラス `sampleClass` の定義を 2 つの宣言に分割し、それぞれ別の `Sub` プロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="2f00b-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 <span data-ttu-id="2f00b-171">この例にある 2 つの部分定義は、同じソース ファイル内にあっても、別々のソース ファイル内にあってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2f00b-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f00b-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f00b-172">See Also</span></span>  
 [<span data-ttu-id="2f00b-173">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="2f00b-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="2f00b-174">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="2f00b-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="2f00b-175">型の上位変換</span><span class="sxs-lookup"><span data-stu-id="2f00b-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [<span data-ttu-id="2f00b-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="2f00b-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="2f00b-177">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="2f00b-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="2f00b-178">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="2f00b-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
