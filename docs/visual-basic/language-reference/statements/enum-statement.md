---
title: "Enum ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Enum
dev_langs:
- VB
helpviewer_keywords:
- enumerated constants
- Enum statement
- Private keyword, Enum statements
- Public keyword, in Enum statement
- variables [Visual Basic], enumeration
- constants, enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ff075349756bd4c568833d049b50b3c3721d1b08
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="324d0-102">Enum ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="324d0-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="324d0-103">列挙体を宣言し、そのメンバーの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="324d0-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="324d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="324d0-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="324d0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="324d0-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="324d0-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="324d0-106">Optional.</span></span> <span data-ttu-id="324d0-107">この列挙体に適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="324d0-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="324d0-108">囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこで ("`<`「と」`>`") です。</span><span class="sxs-lookup"><span data-stu-id="324d0-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="324d0-109"><xref:System.FlagsAttribute>属性は、列挙体のインスタンスの値が、複数の列挙型メンバーを含めることができ、各メンバーが列挙値のビット フィールドを表すことを示します</xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="324d0-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="324d0-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="324d0-110">Optional.</span></span> <span data-ttu-id="324d0-111">この列挙体にアクセスできるコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="324d0-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="324d0-112">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="324d0-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="324d0-113">Public</span><span class="sxs-lookup"><span data-stu-id="324d0-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="324d0-114">Protected</span><span class="sxs-lookup"><span data-stu-id="324d0-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="324d0-115">Friend</span><span class="sxs-lookup"><span data-stu-id="324d0-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="324d0-116">Private</span><span class="sxs-lookup"><span data-stu-id="324d0-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="324d0-117">指定できます`Protected``Friend`列挙型のクラスを派生クラスでは、または同じアセンブリ内のコードからのアクセスを許可するようにします。</span><span class="sxs-lookup"><span data-stu-id="324d0-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="324d0-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="324d0-118">Optional.</span></span> <span data-ttu-id="324d0-119">この列挙体を宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされた要素のセットを非表示にことを指定します。</span><span class="sxs-lookup"><span data-stu-id="324d0-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="324d0-120">指定できます[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)のみ列挙体自体ではなく、メンバーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="324d0-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="324d0-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="324d0-121">Required.</span></span> <span data-ttu-id="324d0-122">列挙体の名前です。</span><span class="sxs-lookup"><span data-stu-id="324d0-122">Name of the enumeration.</span></span> <span data-ttu-id="324d0-123">有効な名前については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。</span><span class="sxs-lookup"><span data-stu-id="324d0-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="324d0-124">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="324d0-124">Optional.</span></span> <span data-ttu-id="324d0-125">列挙体およびそのすべてのメンバーのデータ型。</span><span class="sxs-lookup"><span data-stu-id="324d0-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="324d0-126">必須です。</span><span class="sxs-lookup"><span data-stu-id="324d0-126">Required.</span></span> <span data-ttu-id="324d0-127">このステートメントで宣言されているメンバー定数の一覧です。</span><span class="sxs-lookup"><span data-stu-id="324d0-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="324d0-128">複数のメンバーは、個々 のソース コード行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="324d0-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="324d0-129">各`member`が次の構文とパーツ。`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="324d0-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="324d0-130">パーツ</span><span class="sxs-lookup"><span data-stu-id="324d0-130">Part</span></span>|<span data-ttu-id="324d0-131">説明</span><span class="sxs-lookup"><span data-stu-id="324d0-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="324d0-132">必須です。</span><span class="sxs-lookup"><span data-stu-id="324d0-132">Required.</span></span> <span data-ttu-id="324d0-133">このメンバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="324d0-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="324d0-134">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="324d0-134">Optional.</span></span> <span data-ttu-id="324d0-135">このメンバーに割り当てられているされ、コンパイル時に評価される式です。</span><span class="sxs-lookup"><span data-stu-id="324d0-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="324d0-136">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="324d0-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="324d0-137">`Enum` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="324d0-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="324d0-138">コメント</span><span class="sxs-lookup"><span data-stu-id="324d0-138">Remarks</span></span>  
 <span data-ttu-id="324d0-139">互いに論理的に関連付けられている不変の値のセットがあれば、列挙体で一緒に定義できます。</span><span class="sxs-lookup"><span data-stu-id="324d0-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="324d0-140">これは、列挙体とそのメンバーでは、それらの値よりも覚えやすく、わかりやすい名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="324d0-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="324d0-141">多くの場所で列挙型のメンバーを使用して、コードでことができますし、します。</span><span class="sxs-lookup"><span data-stu-id="324d0-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="324d0-142">列挙体を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="324d0-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="324d0-143">置き換えや数値の入力ミスによって発生したエラーを削減します。</span><span class="sxs-lookup"><span data-stu-id="324d0-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="324d0-144">値は、将来変更を簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="324d0-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="324d0-145">コードを読みやすくする可能性は低くなりますエラーが発生することを意味するようにします。</span><span class="sxs-lookup"><span data-stu-id="324d0-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="324d0-146">上位互換性を確認します。</span><span class="sxs-lookup"><span data-stu-id="324d0-146">Ensures forward compatibility.</span></span> <span data-ttu-id="324d0-147">列挙体を使用する場合、コードは、メンバーの名前に対応する値が変更された後で、エラーが発生する可能性は低くです。</span><span class="sxs-lookup"><span data-stu-id="324d0-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="324d0-148">列挙体は、名前、基のデータ型およびメンバーのセットを持ちます。</span><span class="sxs-lookup"><span data-stu-id="324d0-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="324d0-149">各メンバーは、定数を表します。</span><span class="sxs-lookup"><span data-stu-id="324d0-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="324d0-150">クラス、構造体、モジュール、または、プロシージャの外側のインターフェイス レベルで宣言された列挙型は、*メンバー列挙*します。</span><span class="sxs-lookup"><span data-stu-id="324d0-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="324d0-151">これは、クラス、構造体、モジュール、またはそれを宣言したインターフェイスのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="324d0-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="324d0-152">列挙体のメンバーは、クラス、構造体、モジュール、またはインターフェイス内の任意の場所からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="324d0-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="324d0-153">コードがクラスの外部構造体、またはモジュール必要がありますメンバー列挙体の名前で修飾するクラス、構造体、またはモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="324d0-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="324d0-154">追加することによって完全修飾名を使用する必要を避けることができます、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントをソース ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="324d0-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="324d0-155">任意のクラス、構造体、モジュール、またはインターフェイスの外部の名前空間レベルで宣言された列挙体が表示される名前空間のメンバーであります。</span><span class="sxs-lookup"><span data-stu-id="324d0-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="324d0-156">*宣言コンテキスト*列挙体は、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があり、プロシージャになることはできません。</span><span class="sxs-lookup"><span data-stu-id="324d0-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="324d0-157">詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="324d0-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="324d0-158">属性を適用できますのメンバーではなく、全体としての列挙体に個別にします。</span><span class="sxs-lookup"><span data-stu-id="324d0-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="324d0-159">属性は、アセンブリのメタデータに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="324d0-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="324d0-160">データ型</span><span class="sxs-lookup"><span data-stu-id="324d0-160">Data Type</span></span>  
 <span data-ttu-id="324d0-161">`Enum`ステートメントは、列挙型のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="324d0-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="324d0-162">各メンバーは、列挙型のデータ型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="324d0-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="324d0-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span><span class="sxs-lookup"><span data-stu-id="324d0-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="324d0-164">指定しない場合`datatype`、列挙体の各メンバーのデータ型を受け取り、`initializer`です。</span><span class="sxs-lookup"><span data-stu-id="324d0-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="324d0-165">両方を指定する場合は、`datatype`と`initializer`のデータ型`initializer`に変換できなければなりません`datatype`します。</span><span class="sxs-lookup"><span data-stu-id="324d0-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="324d0-166">どちらの場合`datatype`も`initializer`が含まれているデータ型の既定値は`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="324d0-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="324d0-167">メンバーの初期化</span><span class="sxs-lookup"><span data-stu-id="324d0-167">Initializing Members</span></span>  
 <span data-ttu-id="324d0-168">`Enum`ステートメントで選択したメンバーの内容を初期化できる`memberlist`です。</span><span class="sxs-lookup"><span data-stu-id="324d0-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="324d0-169">使用する`initializer`メンバーに割り当てられる式を指定します。</span><span class="sxs-lookup"><span data-stu-id="324d0-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="324d0-170">指定しない場合`initializer`メンバーの場合は、Visual Basic を初期化して&0; のいずれか (1 つ目である場合`member`で`memberlist`)、またはその直前のより&1; だけ大きい値に`member`します。</span><span class="sxs-lookup"><span data-stu-id="324d0-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="324d0-171">それぞれに指定する式`initializer`リテラル、既に定義されている他の定数と列挙型のメンバーは既に定義されている、この列挙体のメンバーの組み合わせにすることができます。</span><span class="sxs-lookup"><span data-stu-id="324d0-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="324d0-172">算術演算および論理演算子を使用すると、このような要素を結合します。</span><span class="sxs-lookup"><span data-stu-id="324d0-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="324d0-173">変数または関数では使用できません`initializer`します。</span><span class="sxs-lookup"><span data-stu-id="324d0-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="324d0-174">変換キーワードなどを使用する、`CByte`と`CShort`です。</span><span class="sxs-lookup"><span data-stu-id="324d0-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="324d0-175">使用することも`AscW`定数を呼び出した場合、`String`または`Char`引数、コンパイル時に計算できるためです。</span><span class="sxs-lookup"><span data-stu-id="324d0-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="324d0-176">列挙体には、浮動小数点値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="324d0-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="324d0-177">メンバーが浮動小数点値を割り当てられている場合、`Option Strict`に設定されている、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="324d0-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="324d0-178">場合`Option Strict`はオフで、値が自動的に変換する、`Enum`型です。</span><span class="sxs-lookup"><span data-stu-id="324d0-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="324d0-179">メンバーの値が、基になるデータ型の許容範囲を超えている場合、または基になるデータ型で許容される最大値に任意のメンバーを初期化する場合は、コンパイラはエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="324d0-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="324d0-180">修飾子</span><span class="sxs-lookup"><span data-stu-id="324d0-180">Modifiers</span></span>  
 <span data-ttu-id="324d0-181">クラス、構造体、モジュール、およびインターフェイス メンバーの列挙体の既定でパブリック アクセスです。</span><span class="sxs-lookup"><span data-stu-id="324d0-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="324d0-182">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="324d0-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="324d0-183">Namespace のフレンド アクセスを既定値の列挙体をメンバーです。</span><span class="sxs-lookup"><span data-stu-id="324d0-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="324d0-184">これらのアクセス レベルをパブリックがプライベートまたはプロテクトには調整できます。</span><span class="sxs-lookup"><span data-stu-id="324d0-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="324d0-185">詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="324d0-185">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="324d0-186">列挙型のすべてのメンバーは、パブリック アクセスを持ち、それらのアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="324d0-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="324d0-187">ただし、列挙体自体により厳しいアクセス レベルがある場合は、指定した列挙体のアクセス レベルが優先されます。</span><span class="sxs-lookup"><span data-stu-id="324d0-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="324d0-188">既定では、すべての列挙は型とそのフィールドは定数です。</span><span class="sxs-lookup"><span data-stu-id="324d0-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="324d0-189">したがって、 `Shared`、 `Static`、および`ReadOnly`列挙型またはそのメンバーを宣言するときに、キーワードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="324d0-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="324d0-190">複数の値を割り当てる</span><span class="sxs-lookup"><span data-stu-id="324d0-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="324d0-191">列挙体は、通常、相互に排他的な値を表します。</span><span class="sxs-lookup"><span data-stu-id="324d0-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="324d0-192">含めることによって、<xref:System.FlagsAttribute>属性、`Enum`宣言、代わりに複数の値に割り当てる列挙体のインスタンス</xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="324d0-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="324d0-193"><xref:System.FlagsAttribute>属性は、列挙体をビット フィールド、つまり、フラグのセットとして処理することを指定します</xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="324d0-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="324d0-194">これらと呼びます*ビット*列挙体です。</span><span class="sxs-lookup"><span data-stu-id="324d0-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="324d0-195">使用して列挙体を宣言する場合、<xref:System.FlagsAttribute>属性、お勧めの値は 2、1、2、4、8、16、およびの累乗を使用することです</xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="324d0-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="324d0-196">また、値が 0 のメンバーの名前を"None"ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="324d0-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="324d0-197">追加のガイドラインについては、「 <xref:System.FlagsAttribute> <xref:System.Enum>.</xref:System.Enum></xref:System.FlagsAttribute>の使用」を参照していますください。</span><span class="sxs-lookup"><span data-stu-id="324d0-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-198">例</span><span class="sxs-lookup"><span data-stu-id="324d0-198">Example</span></span>  
 <span data-ttu-id="324d0-199">次の例では、使用する方法、`Enum`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="324d0-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="324d0-200">メンバーと呼びます注`EggSizeEnum.Medium`ではなく`Medium`です。</span><span class="sxs-lookup"><span data-stu-id="324d0-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 <span data-ttu-id="324d0-201">[!code-vb[VbEnumsTask #&41;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-201">[!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-202">例</span><span class="sxs-lookup"><span data-stu-id="324d0-202">Example</span></span>  
 <span data-ttu-id="324d0-203">次の例では、メソッドが範囲外です、`Egg`クラスです。</span><span class="sxs-lookup"><span data-stu-id="324d0-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="324d0-204">したがって、`EggSizeEnum`として完全修飾`Egg.EggSizeEnum`します。</span><span class="sxs-lookup"><span data-stu-id="324d0-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 <span data-ttu-id="324d0-205">[!code-vb[VbEnumsTask #&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-205">[!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-206">例</span><span class="sxs-lookup"><span data-stu-id="324d0-206">Example</span></span>  
 <span data-ttu-id="324d0-207">次の例では、`Enum`という名前の定数値を関連のセットを定義するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="324d0-207">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="324d0-208">この場合、値は、色のデータベースのデータ入力フォームをデザインすることもできます。</span><span class="sxs-lookup"><span data-stu-id="324d0-208">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 <span data-ttu-id="324d0-209">[!code-vb[VbEnumsTask #&30;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-209">[!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-210">例</span><span class="sxs-lookup"><span data-stu-id="324d0-210">Example</span></span>  
 <span data-ttu-id="324d0-211">次の例では、正と負の両方の番号を含む値を示します。</span><span class="sxs-lookup"><span data-stu-id="324d0-211">The following example shows values that include both positive and negative numbers.</span></span>  
  
 <span data-ttu-id="324d0-212">[!code-vb[VbEnumsTask #&31;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-212">[!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-213">例</span><span class="sxs-lookup"><span data-stu-id="324d0-213">Example</span></span>  
 <span data-ttu-id="324d0-214">次の例では、`As`句を使用して指定、`datatype`列挙体の。</span><span class="sxs-lookup"><span data-stu-id="324d0-214">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 <span data-ttu-id="324d0-215">[!code-vb[VbEnumsTask&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-215">[!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-216">例</span><span class="sxs-lookup"><span data-stu-id="324d0-216">Example</span></span>  
 <span data-ttu-id="324d0-217">次の例では、ビットごとの列挙体の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="324d0-217">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="324d0-218">複数の値は、ビットごとの列挙型のインスタンスに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="324d0-218">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="324d0-219">`Enum`宣言が含まれる、<xref:System.FlagsAttribute>属性には、列挙型をフラグのセットとして扱えることを示します</xref:System.FlagsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="324d0-219">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 <span data-ttu-id="324d0-220">[!code-vb[VbEnumsTask&#61;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-220">[!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="324d0-221">例</span><span class="sxs-lookup"><span data-stu-id="324d0-221">Example</span></span>  
 <span data-ttu-id="324d0-222">次の例は、列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="324d0-222">The following example iterates through an enumeration.</span></span> <span data-ttu-id="324d0-223">使用して、 <xref:System.Enum.GetNames%2A>、列挙体のメンバー名の配列を取得するメソッドと<xref:System.Enum.GetValues%2A>メンバーの値の配列を取得する</xref:System.Enum.GetValues%2A></xref:System.Enum.GetNames%2A>。</span><span class="sxs-lookup"><span data-stu-id="324d0-223">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 <span data-ttu-id="324d0-224">[!code-vb[VbEnumsTask&51;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="324d0-224">[!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324d0-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="324d0-225">See Also</span></span>  
 <span data-ttu-id="324d0-226"><xref:System.Enum></xref:System.Enum></span><span class="sxs-lookup"><span data-stu-id="324d0-226"><xref:System.Enum></span></span>   
 <span data-ttu-id="324d0-227"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="324d0-227"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
<span data-ttu-id="324d0-228"> [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="324d0-228"> [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="324d0-229"> [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="324d0-229"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="324d0-230"> [明示的および暗黙的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="324d0-230"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="324d0-231"> [型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="324d0-231"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="324d0-232"> [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="324d0-232"> [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
