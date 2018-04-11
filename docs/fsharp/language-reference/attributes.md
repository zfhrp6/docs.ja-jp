---
title: 属性 (F#)
description: F# の属性がプログラミング構成要素に適用するメタデータを有効にする方法について説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 95c001e6-3708-4d04-a850-d855f78eb51e
ms.openlocfilehash: 88098e51d19a86f501c35abe3408524378f147b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="attributes"></a><span data-ttu-id="fd430-104">属性</span><span class="sxs-lookup"><span data-stu-id="fd430-104">Attributes</span></span>

<span data-ttu-id="fd430-105">属性は、プログラミング構成要素に適用するメタデータを有効にします。</span><span class="sxs-lookup"><span data-stu-id="fd430-105">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd430-106">構文</span><span class="sxs-lookup"><span data-stu-id="fd430-106">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="fd430-107">コメント</span><span class="sxs-lookup"><span data-stu-id="fd430-107">Remarks</span></span>

<span data-ttu-id="fd430-108">前の構文では、*ターゲット*を省略して、存在する場合は、属性が適用されるプログラム エンティティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd430-108">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="fd430-109">有効な値*ターゲット*このドキュメントの後半に示す表に示します。</span><span class="sxs-lookup"><span data-stu-id="fd430-109">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="fd430-110">*属性名*またはサフィックスがない場合、有効な属性型の名前 (場合によっては名前空間を持つ修飾名) を指す`Attribute`属性の型名で通常使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd430-110">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="fd430-111">たとえば、型`ObsoleteAttribute`だけに簡略化`Obsolete`このコンテキストでします。</span><span class="sxs-lookup"><span data-stu-id="fd430-111">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="fd430-112">*引数*属性の型のコンス トラクターの引数します。</span><span class="sxs-lookup"><span data-stu-id="fd430-112">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="fd430-113">属性に既定のコンス トラクターがある場合、引数リストとかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="fd430-113">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="fd430-114">属性は、位置指定引数と名前付き引数の両方をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fd430-114">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="fd430-115">*位置指定引数*が出現する順序で使用される引数。</span><span class="sxs-lookup"><span data-stu-id="fd430-115">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="fd430-116">属性にパブリック プロパティが設定されている場合、名前付き引数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd430-116">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="fd430-117">引数リストで、次の構文を使用して、これらを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="fd430-117">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="fd430-118">このようなプロパティの初期化は、任意の順序で指定できますが、任意の位置指定引数に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd430-118">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="fd430-119">位置指定引数とプロパティの初期化を使用する属性の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fd430-119">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="fd430-120">属性は、この例では`DllImportAttribute`、ここで短縮形で使用します。</span><span class="sxs-lookup"><span data-stu-id="fd430-120">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="fd430-121">最初の引数が位置指定パラメーターで、2 番目はプロパティです。</span><span class="sxs-lookup"><span data-stu-id="fd430-121">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="fd430-122">属性は、.NET プログラミング構成要素と呼ばれるオブジェクトをできるようにする、*属性*型またはその他のプログラム要素に関連付ける。</span><span class="sxs-lookup"><span data-stu-id="fd430-122">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="fd430-123">属性が適用されるプログラム要素と呼ばれる、*属性ターゲット*です。</span><span class="sxs-lookup"><span data-stu-id="fd430-123">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="fd430-124">通常、属性には、そのターゲットに関するメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fd430-124">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="fd430-125">このコンテキストでのメタデータにそのフィールドとメンバー以外の型に関するデータが可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fd430-125">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="fd430-126">F# の属性は、次のプログラミング構成要素に適用できます: 関数、メソッド、アセンブリ、モジュール、型 (クラス、レコード、構造体、インターフェイス、デリゲート、列挙体、共用体、およびなど)、コンス トラクター、プロパティ、フィールド、パラメーター、パラメーターを入力し、値を返します。</span><span class="sxs-lookup"><span data-stu-id="fd430-126">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="fd430-127">属性が許可されていない`let`クラス、式、またはワークフローの式内のバインド。</span><span class="sxs-lookup"><span data-stu-id="fd430-127">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="fd430-128">通常、属性の宣言には、属性のターゲットの宣言の直前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd430-128">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="fd430-129">同時に、次のように、複数の属性の宣言を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd430-129">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="fd430-130">.NET リフレクションを使用して、実行時に属性を照会できます。</span><span class="sxs-lookup"><span data-stu-id="fd430-130">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="fd430-131">前のコード例では、個別に、複数の属性を宣言することができます。 またはでも宣言できます角かっこの 1 つのセットに次のように、個々 の属性と、コンス トラクターを分離する、セミコロンを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="fd430-131">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="fd430-132">属性によく発生、`Obsolete`属性、セキュリティに関する考慮事項については、属性の COM サポート、コードの所有権に関連する属性および属性の型をシリアル化できるかどうかを示す属性です。</span><span class="sxs-lookup"><span data-stu-id="fd430-132">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="fd430-133">次の例での使用、`Obsolete`属性。</span><span class="sxs-lookup"><span data-stu-id="fd430-133">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="fd430-134">属性の対象の`assembly`と`module`、最上位に属性を適用する`do`アセンブリにバインドします。</span><span class="sxs-lookup"><span data-stu-id="fd430-134">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="fd430-135">単語を含めることができます`assembly`または`module`属性宣言で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="fd430-135">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="fd430-136">適用する属性の属性のターゲットを省略したかどうか、`do`バインド、その属性の意味のある属性ターゲットを特定しようと試みます、f# コンパイラです。</span><span class="sxs-lookup"><span data-stu-id="fd430-136">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="fd430-137">多くの属性クラスは、型の属性を持つ`System.AttributeUsageAttribute`その属性のサポート可能なターゲットに関する情報を含むです。</span><span class="sxs-lookup"><span data-stu-id="fd430-137">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="fd430-138">場合、`System.AttributeUsageAttribute`属性には、ターゲットとしての関数がサポートされています、プログラムのメイン エントリ ポイントに適用する属性が作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="fd430-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="fd430-139">場合、`System.AttributeUsageAttribute`ことを示す属性がアセンブリをターゲットとしてをサポートしている、コンパイラはアセンブリに適用する属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="fd430-139">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="fd430-140">関数と、アセンブリの両方にほとんどの属性は適用されませんが、プログラムの main 関数に適用する場合で属性が実行されます。</span><span class="sxs-lookup"><span data-stu-id="fd430-140">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="fd430-141">属性ターゲットが明示的に指定されている場合は、属性が、指定したターゲットに適用されます。</span><span class="sxs-lookup"><span data-stu-id="fd430-141">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="fd430-142">属性がターゲットの有効な値で明示的に、通常を指定する必要はありませんが*ターゲット*属性での使用例と、次の表で表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd430-142">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="fd430-143">属性ターゲット</span><span class="sxs-lookup"><span data-stu-id="fd430-143">Attribute target</span></span></td>
    <th><span data-ttu-id="fd430-144">例</span><span class="sxs-lookup"><span data-stu-id="fd430-144">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-145">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="fd430-145">assembly</span></span></td>
    <td><span data-ttu-id="fd430-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="fd430-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-147">return</span><span class="sxs-lookup"><span data-stu-id="fd430-147">return</span></span></td>
    <td><span data-ttu-id="fd430-148">' function1 を x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="fd430-148">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-149">フィールド</span><span class="sxs-lookup"><span data-stu-id="fd430-149">field</span></span></td>
    <td><span data-ttu-id="fd430-150">' [<field: DefaultValue>] val mutable x: int'</span><span class="sxs-lookup"><span data-stu-id="fd430-150">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-151">property</span><span class="sxs-lookup"><span data-stu-id="fd430-151">property</span></span></td>
    <td><span data-ttu-id="fd430-152">' [<property: Obsolete>] このです。MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="fd430-152">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-153">Param</span><span class="sxs-lookup"><span data-stu-id="fd430-153">param</span></span></td>
    <td><span data-ttu-id="fd430-154">' メンバーこれです。MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</span><span class="sxs-lookup"><span data-stu-id="fd430-154">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="fd430-155">型</span><span class="sxs-lookup"><span data-stu-id="fd430-155">type</span></span></td>
    <td><span data-ttu-id="fd430-156">
        ```
        [<type: StructLayout(Sequential)>入力は構造体を = x: バイト y: int 終了```
    </span><span class="sxs-lookup"><span data-stu-id="fd430-156">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="fd430-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd430-157">See Also</span></span>

[<span data-ttu-id="fd430-158">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="fd430-158">F# Language Reference</span></span>](index.md)
