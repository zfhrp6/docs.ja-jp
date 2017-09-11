---
title: "上位変換 (Visual Basic) を入力 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 383f4b1d29e9bbf81eee44bf78762a80aea9eb36
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="2e872-102">型の上位変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e872-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="2e872-103">モジュールでのプログラミング要素を宣言するときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュールを含む名前空間には、そのスコープを昇格させます。</span><span class="sxs-lookup"><span data-stu-id="2e872-103">When you declare a programming element in a module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="2e872-104">これと呼ばれます。*の上位変換の入力*します。</span><span class="sxs-lookup"><span data-stu-id="2e872-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="2e872-105">次の例では、モジュールのスケルトンの定義とモジュールの&2; つのメンバーを示します。</span><span class="sxs-lookup"><span data-stu-id="2e872-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 <span data-ttu-id="2e872-106">[!code-vb[VbVbalrDeclaredElements&#1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2e872-106">[!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span></span>  
  
 <span data-ttu-id="2e872-107">内で`projModule`プログラミング、モジュール レベルで宣言されている要素に昇格`projNamespace`します。</span><span class="sxs-lookup"><span data-stu-id="2e872-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="2e872-108">前の例で`basicEnum`と`innerClass`昇格されますが、`numberSub`モジュール レベルで宣言されていないためにではありません。</span><span class="sxs-lookup"><span data-stu-id="2e872-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="2e872-109">型の上位変換の効果</span><span class="sxs-lookup"><span data-stu-id="2e872-109">Effect of Type Promotion</span></span>  
 <span data-ttu-id="2e872-110">型の上位変換の効果は、修飾文字列がモジュール名を含める必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="2e872-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="2e872-111">次の例では、前の例では、手順&2; つの呼び出しをでいます。</span><span class="sxs-lookup"><span data-stu-id="2e872-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 <span data-ttu-id="2e872-112">[!code-vb[VbVbalrDeclaredElements&#2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2e872-112">[!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span></span>  
  
 <span data-ttu-id="2e872-113">前の例では、最初の呼び出しは、完全な修飾文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="2e872-113">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="2e872-114">ただし、これはないために必要な型の上位変換のためです。</span><span class="sxs-lookup"><span data-stu-id="2e872-114">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="2e872-115">もう&1; つを呼び出すもアクセス モジュールのメンバーを含めずに`projModule`修飾文字列。</span><span class="sxs-lookup"><span data-stu-id="2e872-115">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="2e872-116">型の上位変換の無効化</span><span class="sxs-lookup"><span data-stu-id="2e872-116">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="2e872-117">名前空間には、モジュール メンバーと同じ名前のメンバーが既に、型の上位変換は、モジュール メンバーの無効化です。</span><span class="sxs-lookup"><span data-stu-id="2e872-117">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="2e872-118">次の例では、列挙型と同じ名前空間内のモジュールのスケルトンの定義を示します。</span><span class="sxs-lookup"><span data-stu-id="2e872-118">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 <span data-ttu-id="2e872-119">[!code-vb[VbVbalrDeclaredElements&#3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2e872-119">[!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span></span>  
  
 <span data-ttu-id="2e872-120">前の例で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]クラスに昇格できません`abc`に`thisNameSpace`名前空間レベルで同じ名前の列挙型が既に存在します。</span><span class="sxs-lookup"><span data-stu-id="2e872-120">In the preceding example, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="2e872-121">アクセスする`abcSub`、完全修飾文字列を使用する必要があります`thisNamespace.thisModule.abc.abcSub`します。</span><span class="sxs-lookup"><span data-stu-id="2e872-121">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="2e872-122">ただし、クラス`xyz`はまだ昇格し、アクセスできる`xyzSub`短い修飾文字列`thisNamespace.xyz.xyzSub`します。</span><span class="sxs-lookup"><span data-stu-id="2e872-122">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="2e872-123">部分型の型の上位変換の無効化</span><span class="sxs-lookup"><span data-stu-id="2e872-123">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="2e872-124">クラスまたは構造体、モジュールの中で使用する場合、[部分](../../../../visual-basic/language-reference/modifiers/partial.md)キーワード、型の上位変換が自動的に無効化にそのクラスまたは構造体、名前空間には同じ名前のメンバーであるかどうか。</span><span class="sxs-lookup"><span data-stu-id="2e872-124">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="2e872-125">モジュールの他の要素は現在の型の上位変換します。</span><span class="sxs-lookup"><span data-stu-id="2e872-125">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="2e872-126">**結果。**</span><span class="sxs-lookup"><span data-stu-id="2e872-126">**Consequences.**</span></span> <span data-ttu-id="2e872-127">部分的な定義の型の上位変換の無効化には、予期しない結果とさらにコンパイル エラーがあります。</span><span class="sxs-lookup"><span data-stu-id="2e872-127">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="2e872-128">次の例では、うちの&1; つは、モジュール内のクラスのスケルトンの部分的な定義を示します。</span><span class="sxs-lookup"><span data-stu-id="2e872-128">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 <span data-ttu-id="2e872-129">[!code-vb[VbVbalrDeclaredElements&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2e872-129">[!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span></span>  
  
 <span data-ttu-id="2e872-130">前の例では、開発者は、コンパイラの&2; つの部分定義をマージする`sampleClass`です。</span><span class="sxs-lookup"><span data-stu-id="2e872-130">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="2e872-131">ただし、コンパイラが部分定義内のプロモーションを考慮されません`sampleModule`します。</span><span class="sxs-lookup"><span data-stu-id="2e872-131">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="2e872-132">その結果、2 つの個別のクラスをコンパイルしようという名前を`sampleClass`ですが、パスのさまざまな修飾します。</span><span class="sxs-lookup"><span data-stu-id="2e872-132">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="2e872-133">コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。</span><span class="sxs-lookup"><span data-stu-id="2e872-133">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="2e872-134">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2e872-134">Recommendations</span></span>  
 <span data-ttu-id="2e872-135">次の推奨事項は、プログラミング習慣を表します。</span><span class="sxs-lookup"><span data-stu-id="2e872-135">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="2e872-136">**一意の名前。**</span><span class="sxs-lookup"><span data-stu-id="2e872-136">**Unique Names.**</span></span> <span data-ttu-id="2e872-137">プログラミングの要素の名前付けを完全に制御がある場合は常には一意の名前をすべての場所で使用します。</span><span class="sxs-lookup"><span data-stu-id="2e872-137">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="2e872-138">同じ名前では、余分に修飾が必要し、するコードが読みにくくします。</span><span class="sxs-lookup"><span data-stu-id="2e872-138">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="2e872-139">微妙なエラーと予期しない結果になることもします。</span><span class="sxs-lookup"><span data-stu-id="2e872-139">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="2e872-140">**完全に修飾されます。**</span><span class="sxs-lookup"><span data-stu-id="2e872-140">**Full Qualification.**</span></span> <span data-ttu-id="2e872-141">モジュールと同じ名前空間の他の要素を使用している、最も安全な方法が、常にすべてのプログラミング要素を完全に修飾を使用します。</span><span class="sxs-lookup"><span data-stu-id="2e872-141">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="2e872-142">型の上位変換がモジュール メンバーの無効化すると、そのメンバーを完全修飾せず、別のプログラミング要素をアクセスしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e872-142">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e872-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e872-143">See Also</span></span>  
 <span data-ttu-id="2e872-144">[Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2e872-144">[Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="2e872-145"> [Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2e872-145"> [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="2e872-146"> [部分的です](../../../../visual-basic/language-reference/modifiers/partial.md) </span><span class="sxs-lookup"><span data-stu-id="2e872-146"> [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) </span></span>  
<span data-ttu-id="2e872-147"> [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="2e872-147"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="2e872-148"> [方法: 変数のスコープを制御します。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="2e872-148"> [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span></span>  
<span data-ttu-id="2e872-149"> [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="2e872-149"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
