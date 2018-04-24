---
title: 属性の適用
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 40932df61e48b0a3a6d99855d47e6b5f56f172aa
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="applying-attributes"></a><span data-ttu-id="7837b-102">属性の適用</span><span class="sxs-lookup"><span data-stu-id="7837b-102">Applying Attributes</span></span>
<span data-ttu-id="7837b-103">コードの要素に属性を適用するには、次のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7837b-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1.  <span data-ttu-id="7837b-104">新しい属性を定義するか、または .NET Framework から名前空間をインポートして既存の属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="7837b-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="7837b-105">属性をコード要素の直前に記述することで、その要素に属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="7837b-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="7837b-106">各言語には独自の属性構文があります。</span><span class="sxs-lookup"><span data-stu-id="7837b-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="7837b-107">C++ および C# では、属性が角かっこで囲まれ、要素とは空白で区切られます。属性と要素の間には改行を入れることもできます。</span><span class="sxs-lookup"><span data-stu-id="7837b-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="7837b-108">Visual Basic では、属性が山かっこで囲まれ、同じ論理行に記述されている必要があります。改行が必要な場合は、行連結文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7837b-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3.  <span data-ttu-id="7837b-109">属性に、位置指定パラメーターと名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="7837b-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="7837b-110">位置指定パラメーターは必須で、名前付きパラメーターの前に指定する必要があります。位置指定パラメーターは、属性のいずれかのコンストラクターのパラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="7837b-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="7837b-111">名前付きパラメーターは省略可能で、属性の読み取り/書き込みプロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="7837b-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="7837b-112">C++ と C# では、オプションのパラメーターごとに `name`=`value` を指定します。`name` はプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="7837b-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="7837b-113">Visual Basic では、`name`:=`value` を指定します。</span><span class="sxs-lookup"><span data-stu-id="7837b-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="7837b-114">コードをコンパイルすると属性がメタデータに格納され、ランタイム リフレクション サービスを通じて共通言語ランタイム、すべてのカスタム ツールやアプリケーションで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7837b-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="7837b-115">規則では、属性の名前の最後は Attribute にします。</span><span class="sxs-lookup"><span data-stu-id="7837b-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="7837b-116">ただし、Visual Basic や C# など、ランタイムを対象とする言語では、属性をフルネームで指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7837b-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="7837b-117">たとえば、<xref:System.ObsoleteAttribute?displayProperty=nameWithType> を初期化する場合は、**Obsolete** と指定するだけで参照できます。</span><span class="sxs-lookup"><span data-stu-id="7837b-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="7837b-118">メソッドへの属性の適用</span><span class="sxs-lookup"><span data-stu-id="7837b-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="7837b-119">次の例では、**System.ObsoleteAttribute** をどのように宣言するかを解説しています。これは、コードを Obsolete として記述しておくために使用します。</span><span class="sxs-lookup"><span data-stu-id="7837b-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="7837b-120">文字列 `"Will be removed in next version"` が属性に渡されます。</span><span class="sxs-lookup"><span data-stu-id="7837b-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="7837b-121">属性が記述されているコードが呼び出された時点で、渡された文字列を示すコンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7837b-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="7837b-122">アセンブリ レベルでの属性の適用</span><span class="sxs-lookup"><span data-stu-id="7837b-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="7837b-123">アセンブリ レベルで属性を適用する場合は、キーワード **assembly** (Visual Basic では `Assembly`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="7837b-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="7837b-124">**AssemblyTitleAttribute** をアセンブリ レベルで適用するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7837b-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="7837b-125">この属性が適用されると、ファイルのメタデータ部分のアセンブリ マニフェストの中に、文字列 `"My Assembly"` が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="7837b-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="7837b-126">この属性を表示するには、[MSIL 逆アセンブラー (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) を使用するか、または属性を取得するためのプログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="7837b-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7837b-127">参照</span><span class="sxs-lookup"><span data-stu-id="7837b-127">See Also</span></span>  
 [<span data-ttu-id="7837b-128">属性</span><span class="sxs-lookup"><span data-stu-id="7837b-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="7837b-129">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="7837b-129">Retrieving Information Stored in Attributes</span></span>](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="7837b-130">概念</span><span class="sxs-lookup"><span data-stu-id="7837b-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)  
 [<span data-ttu-id="7837b-131">属性</span><span class="sxs-lookup"><span data-stu-id="7837b-131">Attributes</span></span>](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
