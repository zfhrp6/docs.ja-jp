---
title: "Enum ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: "44"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a8244318e0be8e50f3384b56cf63e59182b6cda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="c6b95-102">Enum ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b95-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="c6b95-103">列挙体を宣言し、そのメンバーの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b95-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6b95-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="c6b95-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c6b95-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="c6b95-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-106">Optional.</span></span> <span data-ttu-id="c6b95-107">この列挙体に適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="c6b95-108">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="c6b95-109"><xref:System.FlagsAttribute>属性は、列挙型のインスタンスの値が、複数の列挙型メンバーを含めることができ、各メンバーが、列挙値のビット フィールドを表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="c6b95-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-110">Optional.</span></span> <span data-ttu-id="c6b95-111">この列挙体にアクセスできるコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="c6b95-112">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="c6b95-113">Public</span><span class="sxs-lookup"><span data-stu-id="c6b95-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="c6b95-114">Protected</span><span class="sxs-lookup"><span data-stu-id="c6b95-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="c6b95-115">Friend</span><span class="sxs-lookup"><span data-stu-id="c6b95-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="c6b95-116">Private</span><span class="sxs-lookup"><span data-stu-id="c6b95-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="c6b95-117">指定できます`Protected``Friend`列挙型のクラス、派生クラスでは、または同じアセンブリ内のコードからアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="c6b95-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-118">Optional.</span></span> <span data-ttu-id="c6b95-119">この列挙体を宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされる要素のセットを非表示にすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="c6b95-120">指定できます[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)のみ列挙体自体ではなく、メンバーのいずれか。</span><span class="sxs-lookup"><span data-stu-id="c6b95-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="c6b95-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-121">Required.</span></span> <span data-ttu-id="c6b95-122">列挙体の名前です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-122">Name of the enumeration.</span></span> <span data-ttu-id="c6b95-123">有効な名前については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="c6b95-124">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-124">Optional.</span></span> <span data-ttu-id="c6b95-125">列挙体およびそのすべてのメンバーのデータ型。</span><span class="sxs-lookup"><span data-stu-id="c6b95-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="c6b95-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-126">Required.</span></span> <span data-ttu-id="c6b95-127">このステートメントで宣言されているメンバー定数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="c6b95-128">複数のメンバーは、個々 のソース コード行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="c6b95-129">各`member`が次の構文とパーツ。`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="c6b95-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="c6b95-130">パーツ</span><span class="sxs-lookup"><span data-stu-id="c6b95-130">Part</span></span>|<span data-ttu-id="c6b95-131">説明</span><span class="sxs-lookup"><span data-stu-id="c6b95-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="c6b95-132">必須です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-132">Required.</span></span> <span data-ttu-id="c6b95-133">このメンバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="c6b95-134">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-134">Optional.</span></span> <span data-ttu-id="c6b95-135">式がコンパイル時に評価され、このメンバーに割り当てられているです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="c6b95-136">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="c6b95-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="c6b95-137">`Enum` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6b95-138">コメント</span><span class="sxs-lookup"><span data-stu-id="c6b95-138">Remarks</span></span>  
 <span data-ttu-id="c6b95-139">互いに論理的に関連付けられている不変の値のセットがあれば、それらを一緒に列挙で定義できます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="c6b95-140">これは、列挙体およびそのメンバーは、その値よりも覚えやすくにわかりやすい名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="c6b95-141">多くの場所で列挙型のメンバーを使用して、コードでことができますし、します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="c6b95-142">列挙体を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="c6b95-143">転置または番号の入力ミスによって発生したエラーが減少します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="c6b95-144">将来の値を変更するのには便利です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="c6b95-145">によりコードを読みやすくする可能性は低くなりますエラーが発生することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="c6b95-146">前方の互換性を確保します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-146">Ensures forward compatibility.</span></span> <span data-ttu-id="c6b95-147">列挙体を使用する場合、コードが後で、メンバー名に対応する値が変更された場合は失敗する可能性は低くします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="c6b95-148">列挙体は、名前、基のデータ型およびメンバーのセットがします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="c6b95-149">各メンバーは、定数を表します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="c6b95-150">クラス、構造体、モジュール、またはインターフェイス レベルでは、プロシージャの外部で宣言された列挙型は、*メンバー列挙*です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="c6b95-151">これは、クラス、構造体、モジュール、またはそれを宣言したインターフェイスのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="c6b95-152">列挙体のメンバーは、クラス、構造体、モジュール、またはインターフェイス内の任意の場所からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="c6b95-153">コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバーの列挙体の名前。</span><span class="sxs-lookup"><span data-stu-id="c6b95-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="c6b95-154">追加することによって完全修飾名を使用する必要を避けることができます、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントをソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="c6b95-155">任意のクラス、構造体、モジュール、またはインターフェイスの外部の名前空間レベルで宣言された列挙型が表示される名前空間のメンバーであります。</span><span class="sxs-lookup"><span data-stu-id="c6b95-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="c6b95-156">*宣言コンテキスト*列挙体のソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c6b95-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="c6b95-157">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6b95-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="c6b95-158">属性を適用できますがそのメンバーに、全体として列挙型には個別にします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="c6b95-159">属性は、アセンブリのメタデータに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="c6b95-160">データ型</span><span class="sxs-lookup"><span data-stu-id="c6b95-160">Data Type</span></span>  
 <span data-ttu-id="c6b95-161">`Enum`ステートメントは、列挙型のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="c6b95-162">各メンバーは、列挙型のデータ型を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="c6b95-163">指定できます`Byte`、 `Integer`、 `Long`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="c6b95-164">指定しない場合`datatype`列挙体の各メンバーのデータ型を受け取り、`initializer`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="c6b95-165">両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="c6b95-166">どちらの場合`datatype`も`initializer`が含まれているデータ型の既定値は`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="c6b95-167">メンバーの初期化</span><span class="sxs-lookup"><span data-stu-id="c6b95-167">Initializing Members</span></span>  
 <span data-ttu-id="c6b95-168">`Enum`ステートメントで選択したメンバーの内容を初期化できる`memberlist`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="c6b95-169">使用する`initializer`をメンバーに割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="c6b95-170">指定しない場合`initializer`のメンバーは、Visual Basic 初期化をゼロにするか (最初である場合`member`で`memberlist`)、またはその直前の場合よりも 1 だけ大きい数値の値に`member`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="c6b95-171">それぞれに指定する式`initializer`リテラル、既に定義されているその他の定数と列挙型のメンバーは既に定義されている、この列挙体のメンバーの組み合わせにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="c6b95-172">算術演算子および論理演算子を使用すると、このような要素を結合します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="c6b95-173">変数または関数を使用することはできません`initializer`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="c6b95-174">変換キーワードなどを使用するただし、`CByte`と`CShort`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="c6b95-175">使用することも`AscW`定数で呼び出す場合は、`String`または`Char`引数、コンパイル時に評価できるためです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="c6b95-176">列挙体には、浮動小数点値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="c6b95-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="c6b95-177">メンバーが浮動小数点値が割り当てられている場合と`Option Strict`on に設定する、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="c6b95-178">場合`Option Strict`に値が自動的に変換がオフ、`Enum`型です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="c6b95-179">メンバーの値は、基になるデータ型の許容範囲を超える場合、または基になるデータ型で許容される最大値の任意のメンバーを初期化する場合は、コンパイラはエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="c6b95-180">修飾子</span><span class="sxs-lookup"><span data-stu-id="c6b95-180">Modifiers</span></span>  
 <span data-ttu-id="c6b95-181">クラス、構造体、モジュール、およびインターフェイス メンバーの列挙体既定でパブリック アクセスです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="c6b95-182">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="c6b95-183">Namespace フレンド アクセスを既定値の列挙型をメンバーです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="c6b95-184">パブリックではプライベートまたはプロテクト メンバーのアクセス レベルを調整することができます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="c6b95-185">詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-185">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="c6b95-186">すべての列挙体メンバーは、パブリック アクセスを持ち、それらのアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c6b95-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="c6b95-187">ただし、列挙体自体にさらに制限されたアクセス レベルがある場合は、指定した列挙体のアクセス レベルが優先されます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="c6b95-188">既定では、すべての列挙体は、型とそのフィールドは定数です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="c6b95-189">したがって、 `Shared`、 `Static`、および`ReadOnly`列挙型またはそのメンバーを宣言するときに、キーワードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="c6b95-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="c6b95-190">複数の値を割り当てる</span><span class="sxs-lookup"><span data-stu-id="c6b95-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="c6b95-191">通常、列挙体は、相互に排他的な値を表します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="c6b95-192">含めることによって、<xref:System.FlagsAttribute>属性、`Enum`宣言、割り当てることができます代わりに複数の値、列挙型のインスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="c6b95-193"><xref:System.FlagsAttribute>属性は、列挙体をビット フィールド、つまりフラグのセットとして扱われることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="c6b95-194">いい*ビット*列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="c6b95-195">使用して列挙体を宣言する場合、<xref:System.FlagsAttribute>属性、ことをお勧めの値は 2、1、2、4、8、16、およびの累乗を使用することです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="c6b95-196">また、値が 0 のメンバーの名前にする"None"ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6b95-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="c6b95-197">その他のガイドラインについては、次を参照してください。<xref:System.FlagsAttribute>と<xref:System.Enum>です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b95-198">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-198">Example</span></span>  
 <span data-ttu-id="c6b95-199">次の例を使用する方法を示しています、`Enum`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="c6b95-200">メンバーと呼ばれる注`EggSizeEnum.Medium`とではなく`Medium`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-201">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-201">Example</span></span>  
 <span data-ttu-id="c6b95-202">次の例では、メソッドが範囲外、`Egg`クラスです。</span><span class="sxs-lookup"><span data-stu-id="c6b95-202">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="c6b95-203">したがって、`EggSizeEnum`として完全修飾されて`Egg.EggSizeEnum`です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-203">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-204">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-204">Example</span></span>  
 <span data-ttu-id="c6b95-205">次の例では、`Enum`を関連するセットを定義するステートメントが定数値をという名前です。</span><span class="sxs-lookup"><span data-stu-id="c6b95-205">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="c6b95-206">この例で値は、色、データベースのデータ エントリ フォームをデザインすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-206">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-207">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-207">Example</span></span>  
 <span data-ttu-id="c6b95-208">次の例では、正と負の値の両方の番号を含む値を示します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-208">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-209">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-209">Example</span></span>  
 <span data-ttu-id="c6b95-210">次の例で、`As`句が指定に使用される、`datatype`列挙体の。</span><span class="sxs-lookup"><span data-stu-id="c6b95-210">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-211">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-211">Example</span></span>  
 <span data-ttu-id="c6b95-212">次の例では、ビットごとの列挙を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-212">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="c6b95-213">複数の値は、ビットごとの列挙体のインスタンスに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b95-213">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="c6b95-214">`Enum`宣言が含まれる、<xref:System.FlagsAttribute>属性は、列挙体をフラグのセットとして扱えることを示します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-214">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b95-215">例</span><span class="sxs-lookup"><span data-stu-id="c6b95-215">Example</span></span>  
 <span data-ttu-id="c6b95-216">次の例は、列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-216">The following example iterates through an enumeration.</span></span> <span data-ttu-id="c6b95-217">使用して、 <xref:System.Enum.GetNames%2A> 、列挙メンバー名の配列を取得する方法と<xref:System.Enum.GetValues%2A>メンバー値の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6b95-217">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6b95-218">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6b95-218">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="c6b95-219">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="c6b95-219">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="c6b95-220">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="c6b95-220">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="c6b95-221">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="c6b95-221">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="c6b95-222">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="c6b95-222">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c6b95-223">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="c6b95-223">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
