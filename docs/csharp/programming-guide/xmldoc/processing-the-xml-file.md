---
title: "XML ファイルの処理 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 610f3ac5c88fb41a4b55f2990fecdc4c13074e19
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="processing-the-xml-file-c-programming-guide"></a><span data-ttu-id="52f69-102">XML ファイルの処理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="52f69-102">Processing the XML File (C# Programming Guide)</span></span>
<span data-ttu-id="52f69-103">コンパイラは、ドキュメントを生成するためにタグ付けされたコードのコンストラクトごとに、ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="52f69-103">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="52f69-104">(コードをタグ付けする方法については、[ドキュメント コメント用の推奨タグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)に関するページを参照してください。)ID 文字列によって、コンストラクトは一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-104">(For information about how to tag your code, see [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="52f69-105">XML ファイルを処理するプログラムは、ID 文字列を使用して、対応する .NET Framework のメタデータまたはドキュメントを適用するリフレクション項目を識別できます。</span><span class="sxs-lookup"><span data-stu-id="52f69-105">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item that the documentation applies to.</span></span>  
  
 <span data-ttu-id="52f69-106">XML ファイルは、コードの階層表現ではなく、要素ごとに生成された ID のフラット リストです。</span><span class="sxs-lookup"><span data-stu-id="52f69-106">The XML file is not a hierarchical representation of your code; it is a flat list that has a generated ID for each element.</span></span>  
  
 <span data-ttu-id="52f69-107">コンパイラは、次の規則に基づいて ID 文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="52f69-107">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
-   <span data-ttu-id="52f69-108">文字列に空白は含まれません。</span><span class="sxs-lookup"><span data-stu-id="52f69-108">No whitespace is in the string.</span></span>  
  
-   <span data-ttu-id="52f69-109">ID 文字列の最初の部分は、単一の文字とそれに続くコロンで識別されるメンバー種類を示します。</span><span class="sxs-lookup"><span data-stu-id="52f69-109">The first part of the ID string identifies the kind of member being identified, by way of a single character followed by a colon.</span></span> <span data-ttu-id="52f69-110">使用されるメンバー型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="52f69-110">The following member types are used:</span></span>  
  
    |<span data-ttu-id="52f69-111">文字</span><span class="sxs-lookup"><span data-stu-id="52f69-111">Character</span></span>|<span data-ttu-id="52f69-112">説明</span><span class="sxs-lookup"><span data-stu-id="52f69-112">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="52f69-113">N</span><span class="sxs-lookup"><span data-stu-id="52f69-113">N</span></span>|<span data-ttu-id="52f69-114">名前空間</span><span class="sxs-lookup"><span data-stu-id="52f69-114">namespace</span></span><br /><br /> <span data-ttu-id="52f69-115">ドキュメント コメントを名前空間に追加することはできませんが、名前空間への cref 参照を行うことはできます (サポートされている場合)。</span><span class="sxs-lookup"><span data-stu-id="52f69-115">You cannot add documentation comments to a namespace, but you can make cref references to them, where supported.</span></span>|  
    |<span data-ttu-id="52f69-116">T</span><span class="sxs-lookup"><span data-stu-id="52f69-116">T</span></span>|<span data-ttu-id="52f69-117">型: クラス、インターフェイス、構造体、列挙、デリゲート</span><span class="sxs-lookup"><span data-stu-id="52f69-117">type: class, interface, struct, enum, delegate</span></span>|  
    |<span data-ttu-id="52f69-118">F</span><span class="sxs-lookup"><span data-stu-id="52f69-118">F</span></span>|<span data-ttu-id="52f69-119">フィールド</span><span class="sxs-lookup"><span data-stu-id="52f69-119">field</span></span>|  
    |<span data-ttu-id="52f69-120">P</span><span class="sxs-lookup"><span data-stu-id="52f69-120">P</span></span>|<span data-ttu-id="52f69-121">プロパティ (インデクサーまたはその他のインデックス付きプロパティを含む)</span><span class="sxs-lookup"><span data-stu-id="52f69-121">property (including indexers or other indexed properties)</span></span>|  
    |<span data-ttu-id="52f69-122">M</span><span class="sxs-lookup"><span data-stu-id="52f69-122">M</span></span>|<span data-ttu-id="52f69-123">メソッド (コンストラクター、演算子などの特殊なメソッドを含む)</span><span class="sxs-lookup"><span data-stu-id="52f69-123">method (including such special methods as constructors, operators, and so forth)</span></span>|  
    |<span data-ttu-id="52f69-124">E</span><span class="sxs-lookup"><span data-stu-id="52f69-124">E</span></span>|<span data-ttu-id="52f69-125">イベント</span><span class="sxs-lookup"><span data-stu-id="52f69-125">event</span></span>|  
    |<span data-ttu-id="52f69-126">!</span><span class="sxs-lookup"><span data-stu-id="52f69-126">!</span></span>|<span data-ttu-id="52f69-127">エラー文字列</span><span class="sxs-lookup"><span data-stu-id="52f69-127">error string</span></span><br /><br /> <span data-ttu-id="52f69-128">あとに続く文字列で、エラーの情報を示します。</span><span class="sxs-lookup"><span data-stu-id="52f69-128">The rest of the string provides information about the error.</span></span> <span data-ttu-id="52f69-129">C# コンパイラは、解決できないリンクのエラー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="52f69-129">The C# compiler generates error information for links that cannot be resolved.</span></span>|  
  
-   <span data-ttu-id="52f69-130">文字列の 2 番目の部分は、項目の完全修飾名で、名前空間のルートから始まります。</span><span class="sxs-lookup"><span data-stu-id="52f69-130">The second part of the string is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="52f69-131">項目の名前、それを囲む型、名前空間は、ピリオドで区切られます。</span><span class="sxs-lookup"><span data-stu-id="52f69-131">The name of the item, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="52f69-132">項目の名前自体にピリオドがある場合、名前のピリオドはハッシュ記号 ('#') に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="52f69-132">If the name of the item itself has periods, they are replaced by the hash-sign ('#').</span></span> <span data-ttu-id="52f69-133">項目の名前には、ハッシュ記号がないことが前提です。</span><span class="sxs-lookup"><span data-stu-id="52f69-133">It is assumed that no item has a hash-sign directly in its name.</span></span> <span data-ttu-id="52f69-134">たとえば、String コンストラクターの完全修飾名は "System.String.#ctor" です。</span><span class="sxs-lookup"><span data-stu-id="52f69-134">For example, the fully qualified name of the String constructor would be "System.String.#ctor".</span></span>  
  
-   <span data-ttu-id="52f69-135">プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。</span><span class="sxs-lookup"><span data-stu-id="52f69-135">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="52f69-136">引数がない場合は、かっこはありません。</span><span class="sxs-lookup"><span data-stu-id="52f69-136">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="52f69-137">引数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="52f69-137">The arguments are separated by commas.</span></span> <span data-ttu-id="52f69-138">各引数のエンコードは、次に示す .NET Framework のシグネチャでの引数のエンコーディング方法にそのまま従います。</span><span class="sxs-lookup"><span data-stu-id="52f69-138">The encoding of each argument follows directly how it is encoded in a .NET Framework signature:</span></span>  
  
    -   <span data-ttu-id="52f69-139">基本データ型。</span><span class="sxs-lookup"><span data-stu-id="52f69-139">Base types.</span></span> <span data-ttu-id="52f69-140">通常の型 (ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE) は、型の完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-140">Regular types (ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE) are represented as the fully qualified name of the type.</span></span>  
  
    -   <span data-ttu-id="52f69-141">組み込みの型 (たとえば、ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF や、</span><span class="sxs-lookup"><span data-stu-id="52f69-141">Intrinsic types (for example, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF.</span></span> <span data-ttu-id="52f69-142">ELEMENT_TYPE_VOID) は、対応する完全な型の完全修飾名として表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-142">and ELEMENT_TYPE_VOID) are represented as the fully qualified name of the corresponding full type.</span></span> <span data-ttu-id="52f69-143">たとえば、System.Int32 や System.TypedReference です。</span><span class="sxs-lookup"><span data-stu-id="52f69-143">For example, System.Int32 or System.TypedReference.</span></span>  
  
    -   <span data-ttu-id="52f69-144">ELEMENT_TYPE_PTR は、修飾される型に続けて '*' と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-144">ELEMENT_TYPE_PTR is represented as a '*' following the modified type.</span></span>  
  
    -   <span data-ttu-id="52f69-145">ELEMENT_TYPE_BYREF は、修飾される型に続けて '@' と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-145">ELEMENT_TYPE_BYREF is represented as a '@' following the modified type.</span></span>  
  
    -   <span data-ttu-id="52f69-146">ELEMENT_TYPE_PINNED は、修飾される型に続けて '^' と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-146">ELEMENT_TYPE_PINNED is represented as a '^' following the modified type.</span></span> <span data-ttu-id="52f69-147">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="52f69-147">The C# compiler never generates this.</span></span>  
  
    -   <span data-ttu-id="52f69-148">ELEMENT_TYPE_CMOD_REQ は、修飾される型に続けて "&#124;" と修飾子クラスの完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-148">ELEMENT_TYPE_CMOD_REQ is represented as a '&#124;' and the fully qualified name of the modifier class, following the modified type.</span></span> <span data-ttu-id="52f69-149">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="52f69-149">The C# compiler never generates this.</span></span>  
  
    -   <span data-ttu-id="52f69-150">ELEMENT_TYPE_CMOD_OPT は、修飾される型に続けて "!" と修飾子クラスの完全修飾名で表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-150">ELEMENT_TYPE_CMOD_OPT is represented as a '!' and the fully qualified name of the modifier class, following the modified type.</span></span>  
  
    -   <span data-ttu-id="52f69-151">ELEMENT_TYPE_SZARRAY は、配列の要素型に続けて "[]" と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-151">ELEMENT_TYPE_SZARRAY is represented as "[]" following the element type of the array.</span></span>  
  
    -   <span data-ttu-id="52f69-152">ELEMENT_TYPE_GENERICARRAY は、配列の要素型に続けて "[?]" と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-152">ELEMENT_TYPE_GENERICARRAY is represented as "[?]" following the element type of the array.</span></span> <span data-ttu-id="52f69-153">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="52f69-153">The C# compiler never generates this.</span></span>  
  
    -   <span data-ttu-id="52f69-154">ELEMENT_TYPE_ARRAY は、[*lowerbound*:`size`,*lowerbound*:`size`] の形式で表されます。ここで、コンマの個数はランク -1 個であり、各次元の下限とサイズは明らかな場合は、10 進数で表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-154">ELEMENT_TYPE_ARRAY is represented as [*lowerbound*:`size`,*lowerbound*:`size`] where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="52f69-155">下限またはサイズの指定がない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-155">If a lower bound or size is not specified, it is simply omitted.</span></span> <span data-ttu-id="52f69-156">特定の次元で下限およびサイズが省略されている場合は、':' も省略されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-156">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="52f69-157">たとえば、ある 2 次元配列の下限が 1 で、サイズの指定がない場合は、[1:,1:] と表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-157">For example, a 2-dimensional array with 1 as the lower bounds and unspecified sizes is [1:,1:].</span></span>  
  
    -   <span data-ttu-id="52f69-158">ELEMENT_TYPE_FNPTR は、"=FUNC:`type`(*signature*)" と表されます。ここで、`type` は戻り値の型であり、*signature* はメソッドの引数です。</span><span class="sxs-lookup"><span data-stu-id="52f69-158">ELEMENT_TYPE_FNPTR is represented as "=FUNC:`type`(*signature*)", where `type` is the return type, and *signature* is the arguments of the method.</span></span> <span data-ttu-id="52f69-159">引数がない場合、かっこは省略されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-159">If there are no arguments, the parentheses are omitted.</span></span> <span data-ttu-id="52f69-160">これは C# コンパイラでは生成されません。</span><span class="sxs-lookup"><span data-stu-id="52f69-160">The C# compiler never generates this.</span></span>  
  
     <span data-ttu-id="52f69-161">次に示すシグネチャ コンポーネントは、オーバーロードされるメソッドの区別には使用されることがないため、表されません。</span><span class="sxs-lookup"><span data-stu-id="52f69-161">The following signature components are not represented because they are never used for differentiating overloaded methods:</span></span>  
  
    -   <span data-ttu-id="52f69-162">呼び出し規則</span><span class="sxs-lookup"><span data-stu-id="52f69-162">calling convention</span></span>  
  
    -   <span data-ttu-id="52f69-163">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="52f69-163">return type</span></span>  
  
    -   <span data-ttu-id="52f69-164">ELEMENT_TYPE_SENTINEL</span><span class="sxs-lookup"><span data-stu-id="52f69-164">ELEMENT_TYPE_SENTINEL</span></span>  
  
-   <span data-ttu-id="52f69-165">変換演算子 (op_Implicit および op_Explicit) だけは、上記のエンコードと同様に、メソッドの戻り値が ”~” としてエンコードされ、それに続けて戻り値の型が表されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-165">For conversion operators only (op_Implicit and op_Explicit), the return value of the method is encoded as a '~' followed by the return type, as encoded above.</span></span>  
  
-   <span data-ttu-id="52f69-166">ジェネリック型では、型の名前の後に、バックチック、ジェネリック型パラメーターの数を示す数値が順に続きます。</span><span class="sxs-lookup"><span data-stu-id="52f69-166">For generic types, the name of the type will be followed by a back tick and then a number that indicates the number of generic type parameters.</span></span>  <span data-ttu-id="52f69-167">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="52f69-167">For example,</span></span>  
  
     <span data-ttu-id="52f69-168">`<member name="T:SampleClass`2">` is the tag for a type that is defined as `public class SampleClass\<T, U >'。</span><span class="sxs-lookup"><span data-stu-id="52f69-168">`<member name="T:SampleClass`2">` is the tag for a type that is defined as `public class SampleClass\<T, U>\`.</span></span>  
  
     <span data-ttu-id="52f69-169">パラメーターとしてジェネリック型を受け取るメソッドでは、ジェネリック型パラメーターは、バックチック付きの数値 (\`0、`1 など) として指定されます。</span><span class="sxs-lookup"><span data-stu-id="52f69-169">For methods taking generic types as parameters, the generic type parameters are specified as numbers prefaced with back ticks (for example \`0,`1).</span></span>  <span data-ttu-id="52f69-170">各数値は、型のジェネリック パラメーターに対する、0 から始まる配列表記を表しています。</span><span class="sxs-lookup"><span data-stu-id="52f69-170">Each number representing a zero-based array notation for the type's generic parameters.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="52f69-171">例</span><span class="sxs-lookup"><span data-stu-id="52f69-171">Examples</span></span>  
 <span data-ttu-id="52f69-172">次の例は、クラスおよびそのメンバーの ID 文字列を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52f69-172">The following examples show how the ID strings for a class and its members would be generated:</span></span>  
  
 <span data-ttu-id="52f69-173">[!code-cs[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/processing-the-xml-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="52f69-173">[!code-cs[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/processing-the-xml-file_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f69-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="52f69-174">See Also</span></span>  
 <span data-ttu-id="52f69-175">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="52f69-175">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="52f69-176">[/doc (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="52f69-176">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="52f69-177">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="52f69-177">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

