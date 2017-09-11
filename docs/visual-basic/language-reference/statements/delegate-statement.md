---
title: "Delegate ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Delegate
dev_langs:
- VB
helpviewer_keywords:
- delegate keyword
- Delegate statement
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
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
ms.openlocfilehash: 052ef837dfe4f9d34081839eea47e35bc4824afd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-statement"></a><span data-ttu-id="59f18-102">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="59f18-102">Delegate Statement</span></span>
<span data-ttu-id="59f18-103">デリゲートを宣言するために使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-103">Used to declare a delegate.</span></span> <span data-ttu-id="59f18-104">デリゲートは、参照型を参照する、`Shared`メソッド、型またはオブジェクトのインスタンス メソッドにします。</span><span class="sxs-lookup"><span data-stu-id="59f18-104">A delegate is a reference type that refers to a `Shared` method of a type or to an instance method of an object.</span></span> <span data-ttu-id="59f18-105">パラメーターと戻り値の型が一致するプロシージャは、このデリゲート クラスのインスタンスを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-105">Any procedure with matching parameter and return types can be used to create an instance of this delegate class.</span></span> <span data-ttu-id="59f18-106">プロシージャし、後で呼び出せるデリゲート インスタンスの作成。</span><span class="sxs-lookup"><span data-stu-id="59f18-106">The procedure can then later be invoked by means of the delegate instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f18-107">構文</span><span class="sxs-lookup"><span data-stu-id="59f18-107">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a><span data-ttu-id="59f18-108">指定項目</span><span class="sxs-lookup"><span data-stu-id="59f18-108">Parts</span></span>  
  
|<span data-ttu-id="59f18-109">用語</span><span class="sxs-lookup"><span data-stu-id="59f18-109">Term</span></span>|<span data-ttu-id="59f18-110">定義</span><span class="sxs-lookup"><span data-stu-id="59f18-110">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="59f18-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="59f18-111">Optional.</span></span> <span data-ttu-id="59f18-112">このデリゲートに適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="59f18-112">List of attributes that apply to this delegate.</span></span> <span data-ttu-id="59f18-113">複数の属性を指定するときは、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="59f18-113">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="59f18-114">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこで ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="59f18-114">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>|  
|`accessmodifier`|<span data-ttu-id="59f18-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="59f18-115">Optional.</span></span> <span data-ttu-id="59f18-116">デリゲートにアクセスできるコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="59f18-116">Specifies what code can access the delegate.</span></span> <span data-ttu-id="59f18-117">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="59f18-117">Can be one of the following:</span></span><br /><br /><span data-ttu-id="59f18-118"> -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)します。</span><span class="sxs-lookup"><span data-stu-id="59f18-118"> -   [Public](../../../visual-basic/language-reference/modifiers/public.md).</span></span> <span data-ttu-id="59f18-119">デリゲートを宣言した要素にアクセスするすべてのコードにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="59f18-119">Any code that can access the element that declares the delegate can access it.</span></span><br /><span data-ttu-id="59f18-120">-   [保護されている](../../../visual-basic/language-reference/modifiers/protected.md)します。</span><span class="sxs-lookup"><span data-stu-id="59f18-120">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md).</span></span> <span data-ttu-id="59f18-121">唯一のコードは、デリゲートのクラスまたは派生クラスでは、それにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="59f18-121">Only code within the delegate's class or a derived class can access it.</span></span><br /><span data-ttu-id="59f18-122">-   [フレンド](../../../visual-basic/language-reference/modifiers/friend.md)します。</span><span class="sxs-lookup"><span data-stu-id="59f18-122">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md).</span></span> <span data-ttu-id="59f18-123">デリゲートが同じアセンブリ内のコードだけにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="59f18-123">Only code within the same assembly can access the delegate.</span></span><br /><span data-ttu-id="59f18-124">-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)します。</span><span class="sxs-lookup"><span data-stu-id="59f18-124">-   [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="59f18-125">デリゲートを宣言する要素内のコードだけがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="59f18-125">Only code within the element that declares the delegate can access it.</span></span><br /><br /> <span data-ttu-id="59f18-126">指定できます`Protected Friend`デリゲートのクラスや派生クラスでは、同じアセンブリ内のコードからのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="59f18-126">You can specify `Protected Friend` to enable access from code within the delegate's class, a derived class, or the same assembly.</span></span>|  
|`Shadows`|<span data-ttu-id="59f18-127">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="59f18-127">Optional.</span></span> <span data-ttu-id="59f18-128">このデリゲートを宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされた要素のセットを非表示にすることを示します。</span><span class="sxs-lookup"><span data-stu-id="59f18-128">Indicates that this delegate redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="59f18-129">宣言された要素は、他の任意の種類の要素でシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="59f18-129">You can shadow any kind of declared element with any other kind.</span></span><br /><br /> <span data-ttu-id="59f18-130">シャドウされた要素は、その要素をシャドウする派生クラスからは使用できません。ただし、シャドウする要素がアクセスできない要素の場合は例外です。</span><span class="sxs-lookup"><span data-stu-id="59f18-130">A shadowed element is unavailable from within the derived class that shadows it, except from where the shadowing element is inaccessible.</span></span> <span data-ttu-id="59f18-131">たとえば場合、`Private`要素をシャドウする基本クラスの要素では、コードへのアクセス許可がない、`Private`要素は、基本クラスの要素を代わりにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="59f18-131">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>|  
|`Sub`|<span data-ttu-id="59f18-132">省略可能、ただし、いずれかの`Sub`または`Function`必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f18-132">Optional, but either `Sub` or `Function` must appear.</span></span> <span data-ttu-id="59f18-133">このプロシージャがデリゲートとしてを宣言`Sub`値を返さないプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="59f18-133">Declares this procedure as a delegate `Sub` procedure that does not return a value.</span></span>|  
|`Function`|<span data-ttu-id="59f18-134">省略可能、ただし、いずれかの`Sub`または`Function`必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f18-134">Optional, but either `Sub` or `Function` must appear.</span></span> <span data-ttu-id="59f18-135">このプロシージャがデリゲートとしてを宣言`Function`値を返すプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="59f18-135">Declares this procedure as a delegate `Function` procedure that returns a value.</span></span>|  
|`name`|<span data-ttu-id="59f18-136">必須です。</span><span class="sxs-lookup"><span data-stu-id="59f18-136">Required.</span></span> <span data-ttu-id="59f18-137">デリゲートの型の名前標準的な変数の名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="59f18-137">Name of the delegate type; follows standard variable naming conventions.</span></span>|  
|`typeparamlist`|<span data-ttu-id="59f18-138">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="59f18-138">Optional.</span></span> <span data-ttu-id="59f18-139">このデリゲートの型パラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="59f18-139">List of type parameters for this delegate.</span></span> <span data-ttu-id="59f18-140">複数の型パラメーターは、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="59f18-140">Multiple type parameters are separated by commas.</span></span> <span data-ttu-id="59f18-141">必要に応じて、それぞれの型パラメーター宣言できますバリアントを使用して`In`と`Out`汎用修飾子です。</span><span class="sxs-lookup"><span data-stu-id="59f18-141">Optionally, each type parameter can be declared variant by using `In` and `Out` generic modifiers.</span></span> <span data-ttu-id="59f18-142">囲む必要があります、[型リスト](../../../visual-basic/language-reference/statements/type-list.md)かっこで囲まれたを導入し、`Of`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="59f18-142">You must enclose the [Type List](../../../visual-basic/language-reference/statements/type-list.md) in parentheses and introduce it with the `Of` keyword.</span></span>|  
|`parameterlist`|<span data-ttu-id="59f18-143">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="59f18-143">Optional.</span></span> <span data-ttu-id="59f18-144">呼び出されると、プロシージャに渡されるパラメーターの一覧。</span><span class="sxs-lookup"><span data-stu-id="59f18-144">List of parameters that are passed to the procedure when it is called.</span></span> <span data-ttu-id="59f18-145">囲む必要があります、[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)かっこ内に示します。</span><span class="sxs-lookup"><span data-stu-id="59f18-145">You must enclose the [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) in parentheses.</span></span>|  
|`type`|<span data-ttu-id="59f18-146">指定するかどうかは必須、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="59f18-146">Required if you specify a `Function` procedure.</span></span> <span data-ttu-id="59f18-147">戻り値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="59f18-147">Data type of the return value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f18-148">コメント</span><span class="sxs-lookup"><span data-stu-id="59f18-148">Remarks</span></span>  
 <span data-ttu-id="59f18-149">`Delegate`ステートメントは、デリゲート クラスのパラメーターと戻り値の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="59f18-149">The `Delegate` statement defines the parameter and return types of a delegate class.</span></span> <span data-ttu-id="59f18-150">パラメーターと戻り値の型が一致するプロシージャは、このデリゲート クラスのインスタンスを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-150">Any procedure with matching parameters and return types can be used to create an instance of this delegate class.</span></span> <span data-ttu-id="59f18-151">プロシージャし、後で呼び出せるように、デリゲート インスタンスを使用して、デリゲートを呼び出すことによって`Invoke`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="59f18-151">The procedure can then later be invoked by means of the delegate instance, by calling the delegate's `Invoke` method.</span></span>  
  
 <span data-ttu-id="59f18-152">プロシージャ内ではありませんが、名前空間、モジュール、クラスまたは構造のレベルでは、デリゲートを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="59f18-152">Delegates can be declared at the namespace, module, class, or structure level, but not within a procedure.</span></span>  
  
 <span data-ttu-id="59f18-153">各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="59f18-153">Each delegate class defines a constructor that is passed the specification of an object method.</span></span> <span data-ttu-id="59f18-154">デリゲート コンス トラクターに渡す引数は、メソッドまたはラムダ式への参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f18-154">An argument to a delegate constructor must be a reference to a method, or a lambda expression.</span></span>  
  
 <span data-ttu-id="59f18-155">メソッドへの参照を指定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-155">To specify a reference to a method, use the following syntax:</span></span>  
  
 <span data-ttu-id="59f18-156">`AddressOf` [`expression`.]`methodname`</span><span class="sxs-lookup"><span data-stu-id="59f18-156">`AddressOf` [`expression`.]`methodname`</span></span>  
  
 <span data-ttu-id="59f18-157">コンパイル時の型、`expression`クラスまたはそのシグネチャがデリゲート クラスのシグネチャと一致する指定した名前のメソッドを格納しているインターフェイスの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f18-157">The compile-time type of the `expression` must be the name of a class or an interface that contains a method of the specified name whose signature matches the signature of the delegate class.</span></span> <span data-ttu-id="59f18-158">`methodname`共有メソッドまたはインスタンス メソッドのいずれかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="59f18-158">The `methodname` can be either a shared method or an instance method.</span></span> <span data-ttu-id="59f18-159">`methodname`クラスの既定のメソッドのデリゲートを作成した場合でも、省略可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="59f18-159">The `methodname` is not optional, even if you create a delegate for the default method of the class.</span></span>  
  
 <span data-ttu-id="59f18-160">ラムダ式を指定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-160">To specify a lambda expression, use the following syntax:</span></span>  
  
 <span data-ttu-id="59f18-161">`Function`([`parm` As `type`, `parm2` As `type2`, ...])`expression`</span><span class="sxs-lookup"><span data-stu-id="59f18-161">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span></span>  
  
 <span data-ttu-id="59f18-162">デリゲート型の関数の署名が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f18-162">The signature of the function must match that of the delegate type.</span></span> <span data-ttu-id="59f18-163">ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59f18-163">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="59f18-164">デリゲートの詳細については、次を参照してください。[デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="59f18-164">For more information about delegates, see [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f18-165">例</span><span class="sxs-lookup"><span data-stu-id="59f18-165">Example</span></span>  
 <span data-ttu-id="59f18-166">次の例では、`Delegate`の&2; つの数値で動作している数値を返すデリゲートを宣言するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="59f18-166">The following example uses the `Delegate` statement to declare a delegate for operating on two numbers and returning a number.</span></span> <span data-ttu-id="59f18-167">`DelegateTest`メソッドは、この型のデリゲートのインスタンスを使用し、番号のペアで動作するように使用します。</span><span class="sxs-lookup"><span data-stu-id="59f18-167">The `DelegateTest` method takes an instance of a delegate of this type and uses it to operate on pairs of numbers.</span></span>  
  
 <span data-ttu-id="59f18-168">[!code-vb[VbVbalrDelegates&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="59f18-168">[!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f18-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="59f18-169">See Also</span></span>  
 <span data-ttu-id="59f18-170">[AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-170">[AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="59f18-171"> [Of](../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-171"> [Of](../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="59f18-172"> [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-172"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="59f18-173"> [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-173"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="59f18-174"> [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-174"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="59f18-175"> [ジェネリックの共変性と反変性](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span><span class="sxs-lookup"><span data-stu-id="59f18-175"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span></span>  
<span data-ttu-id="59f18-176"> [で](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="59f18-176"> [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) </span></span>  
<span data-ttu-id="59f18-177"> [チェック アウトします。](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="59f18-177"> [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)</span></span>
