---
title: 属性 (F#)
description: F# の属性がプログラミング構成要素に適用するメタデータを有効にする方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b8efc0cdc14e690bbc5c24456d0b1eaa3d55988e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="attributes"></a><span data-ttu-id="8a1b8-103">属性</span><span class="sxs-lookup"><span data-stu-id="8a1b8-103">Attributes</span></span>

<span data-ttu-id="8a1b8-104">属性は、プログラミング構成要素に適用するメタデータを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a1b8-105">構文</span><span class="sxs-lookup"><span data-stu-id="8a1b8-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="8a1b8-106">コメント</span><span class="sxs-lookup"><span data-stu-id="8a1b8-106">Remarks</span></span>

<span data-ttu-id="8a1b8-107">前の構文では、*ターゲット*を省略して、存在する場合は、属性が適用されるプログラム エンティティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="8a1b8-108">有効な値*ターゲット*このドキュメントの後半に示す表に示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="8a1b8-109">*属性名*またはサフィックスがない場合、有効な属性型の名前 (場合によっては名前空間を持つ修飾名) を指す`Attribute`属性の型名で通常使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="8a1b8-110">たとえば、型`ObsoleteAttribute`だけに簡略化`Obsolete`このコンテキストでします。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="8a1b8-111">*引数*属性の型のコンス トラクターの引数します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="8a1b8-112">属性に既定のコンス トラクターがある場合、引数リストとかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="8a1b8-113">属性は、位置指定引数と名前付き引数の両方をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="8a1b8-114">*位置指定引数*が出現する順序で使用される引数。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="8a1b8-115">属性にパブリック プロパティが設定されている場合、名前付き引数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="8a1b8-116">引数リストで、次の構文を使用して、これらを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="8a1b8-117">このようなプロパティの初期化は、任意の順序で指定できますが、任意の位置指定引数に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="8a1b8-118">位置指定引数とプロパティの初期化を使用する属性の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="8a1b8-119">属性は、この例では`DllImportAttribute`、ここで短縮形で使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="8a1b8-120">最初の引数が位置指定パラメーターで、2 番目はプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="8a1b8-121">属性は、.NET プログラミング構成要素と呼ばれるオブジェクトをできるようにする、*属性*型またはその他のプログラム要素に関連付ける。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="8a1b8-122">属性が適用されるプログラム要素と呼ばれる、*属性ターゲット*です。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="8a1b8-123">通常、属性には、そのターゲットに関するメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="8a1b8-124">このコンテキストでのメタデータにそのフィールドとメンバー以外の型に関するデータが可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="8a1b8-125">F# の属性は、次のプログラミング構成要素に適用できます: 関数、メソッド、アセンブリ、モジュール、型 (クラス、レコード、構造体、インターフェイス、デリゲート、列挙体、共用体、およびなど)、コンス トラクター、プロパティ、フィールド、パラメーター、パラメーターを入力し、値を返します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="8a1b8-126">属性が許可されていない`let`クラス、式、またはワークフローの式内のバインド。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="8a1b8-127">通常、属性の宣言には、属性のターゲットの宣言の直前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="8a1b8-128">同時に、次のように、複数の属性の宣言を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="8a1b8-129">.NET リフレクションを使用して、実行時に属性を照会できます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="8a1b8-130">前のコード例では、個別に、複数の属性を宣言することができます。 またはでも宣言できます角かっこの 1 つのセットに次のように、個々 の属性と、コンス トラクターを分離する、セミコロンを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="8a1b8-131">属性によく発生、`Obsolete`属性、セキュリティに関する考慮事項については、属性の COM サポート、コードの所有権に関連する属性および属性の型をシリアル化できるかどうかを示す属性です。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="8a1b8-132">次の例での使用、`Obsolete`属性。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="8a1b8-133">属性の対象の`assembly`と`module`、最上位に属性を適用する`do`アセンブリにバインドします。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="8a1b8-134">単語を含めることができます`assembly`または`module`属性宣言で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="8a1b8-135">適用する属性の属性のターゲットを省略したかどうか、`do`バインド、その属性の意味のある属性ターゲットを特定しようと試みます、f# コンパイラです。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="8a1b8-136">多くの属性クラスは、型の属性を持つ`System.AttributeUsageAttribute`その属性のサポート可能なターゲットに関する情報を含むです。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="8a1b8-137">場合、`System.AttributeUsageAttribute`属性には、ターゲットとしての関数がサポートされています、プログラムのメイン エントリ ポイントに適用する属性が作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="8a1b8-138">場合、`System.AttributeUsageAttribute`ことを示す属性がアセンブリをターゲットとしてをサポートしている、コンパイラはアセンブリに適用する属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="8a1b8-139">関数と、アセンブリの両方にほとんどの属性は適用されませんが、プログラムの main 関数に適用する場合で属性が実行されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="8a1b8-140">属性ターゲットが明示的に指定されている場合は、属性が、指定したターゲットに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="8a1b8-141">属性がターゲットの有効な値で明示的に、通常を指定する必要はありませんが*ターゲット*属性での使用例と、次の表で表示されます。</span><span class="sxs-lookup"><span data-stu-id="8a1b8-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="8a1b8-142">属性ターゲット</span><span class="sxs-lookup"><span data-stu-id="8a1b8-142">Attribute target</span></span></td>
    <th><span data-ttu-id="8a1b8-143">例</span><span class="sxs-lookup"><span data-stu-id="8a1b8-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-144">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="8a1b8-144">assembly</span></span></td>
    <td><span data-ttu-id="8a1b8-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="8a1b8-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-146">return</span><span class="sxs-lookup"><span data-stu-id="8a1b8-146">return</span></span></td>
    <td><span data-ttu-id="8a1b8-147">' function1 を x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="8a1b8-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-148">フィールド</span><span class="sxs-lookup"><span data-stu-id="8a1b8-148">field</span></span></td>
    <td><span data-ttu-id="8a1b8-149">' [<field: DefaultValue>] val mutable x: int'</span><span class="sxs-lookup"><span data-stu-id="8a1b8-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-150">property</span><span class="sxs-lookup"><span data-stu-id="8a1b8-150">property</span></span></td>
    <td><span data-ttu-id="8a1b8-151">' [<property: Obsolete>] このです。MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="8a1b8-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-152">Param</span><span class="sxs-lookup"><span data-stu-id="8a1b8-152">param</span></span></td>
    <td><span data-ttu-id="8a1b8-153">' メンバーこれです。MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</span><span class="sxs-lookup"><span data-stu-id="8a1b8-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="8a1b8-154">型</span><span class="sxs-lookup"><span data-stu-id="8a1b8-154">type</span></span></td>
    <td><span data-ttu-id="8a1b8-155">
        ```
        [<type: StructLayout(Sequential)>入力は構造体を = x: バイト y: int 終了 ```
    </span><span class="sxs-lookup"><span data-stu-id="8a1b8-155">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8a1b8-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a1b8-156">See Also</span></span>

[<span data-ttu-id="8a1b8-157">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="8a1b8-157">F# Language Reference</span></span>](index.md)
