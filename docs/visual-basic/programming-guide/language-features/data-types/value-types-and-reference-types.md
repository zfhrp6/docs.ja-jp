---
title: "値型と参照型 |Microsoft ドキュメント"
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
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
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
ms.openlocfilehash: 8136f58b2e7fce15e959e04b84b05f64d078d662
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="897ae-102">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="897ae-102">Value Types and Reference Types</span></span>
<span data-ttu-id="897ae-103">Visual basic でのデータ型は、分類に基づいて実装されます。</span><span class="sxs-lookup"><span data-stu-id="897ae-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="897ae-104">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型は、特定の型の変数が、独自のデータまたはデータへのポインターを格納するかどうかによって分類できます。</span><span class="sxs-lookup"><span data-stu-id="897ae-104">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="897ae-105">独自のデータを格納する場合、*値の型*別の場所ではメモリ内のデータへのポインターを保持している場合、*型を参照*します。</span><span class="sxs-lookup"><span data-stu-id="897ae-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="897ae-106">値型</span><span class="sxs-lookup"><span data-stu-id="897ae-106">Value Types</span></span>  
 <span data-ttu-id="897ae-107">データ型は、*値の型*独自のメモリ内のデータが保持している場合。</span><span class="sxs-lookup"><span data-stu-id="897ae-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="897ae-108">値型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="897ae-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="897ae-109">すべての数値データ型</span><span class="sxs-lookup"><span data-stu-id="897ae-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="897ae-110">`Boolean`、`Char`、および `Date`</span><span class="sxs-lookup"><span data-stu-id="897ae-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="897ae-111">そのメンバーが参照型である場合でも、すべての構造</span><span class="sxs-lookup"><span data-stu-id="897ae-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="897ae-112">列挙型、その基になる型は常にため`SByte`、 `Short`、 `Integer`、 `Long`、 `Byte`、 `UShort`、 `UInteger`、または`ULong`</span><span class="sxs-lookup"><span data-stu-id="897ae-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="897ae-113">参照型のメンバーが含まれている場合でも、すべての構造体は値の型です。</span><span class="sxs-lookup"><span data-stu-id="897ae-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="897ae-114">このため、値などの型`Char`と`Integer`.NET Framework の構造体によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="897ae-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="897ae-115">予約済みキーワードを使用して、値型を宣言できます`Decimal`します。</span><span class="sxs-lookup"><span data-stu-id="897ae-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="897ae-116">使用することも、`New`値型を初期化するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="897ae-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="897ae-117">これは、型のパラメーターを受け取るコンス トラクターがある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="897ae-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="897ae-118">この例は、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>コンス トラクターは、新しい`Decimal`指定した部分からの値</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>。</span><span class="sxs-lookup"><span data-stu-id="897ae-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="897ae-119">参照型</span><span class="sxs-lookup"><span data-stu-id="897ae-119">Reference Types</span></span>  
 <span data-ttu-id="897ae-120">A*型参照*データを保持する別のメモリ位置へのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="897ae-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="897ae-121">参照型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="897ae-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="897ae-122">その要素が値型の場合でも、すべての配列</span><span class="sxs-lookup"><span data-stu-id="897ae-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="897ae-123">などのクラス型します。<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="897ae-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="897ae-124">デリゲート</span><span class="sxs-lookup"><span data-stu-id="897ae-124">Delegates</span></span>  
  
 <span data-ttu-id="897ae-125">クラスは、*型参照*します。</span><span class="sxs-lookup"><span data-stu-id="897ae-125">A class is a *reference type*.</span></span> <span data-ttu-id="897ae-126">参照型など、このため、`Object`と`String`でサポートされている[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラスです。</span><span class="sxs-lookup"><span data-stu-id="897ae-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes.</span></span> <span data-ttu-id="897ae-127">場合でも、そのメンバーが値型は、すべての配列が参照型である注意してください。</span><span class="sxs-lookup"><span data-stu-id="897ae-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="897ae-128">使用する必要がありますので、すべての参照型は、基になる .NET Framework クラスを表す、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)初期化するときのキーワードです。</span><span class="sxs-lookup"><span data-stu-id="897ae-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="897ae-129">次のステートメントでは、配列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="897ae-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="897ae-130">型ではない要素</span><span class="sxs-lookup"><span data-stu-id="897ae-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="897ae-131">これらはいずれも、宣言された要素のデータ型として指定できないため、次のプログラミング要素は型とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="897ae-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="897ae-132">名前空間</span><span class="sxs-lookup"><span data-stu-id="897ae-132">Namespaces</span></span>  
  
-   <span data-ttu-id="897ae-133">モジュール</span><span class="sxs-lookup"><span data-stu-id="897ae-133">Modules</span></span>  
  
-   <span data-ttu-id="897ae-134">イベント</span><span class="sxs-lookup"><span data-stu-id="897ae-134">Events</span></span>  
  
-   <span data-ttu-id="897ae-135">プロパティとプロシージャ</span><span class="sxs-lookup"><span data-stu-id="897ae-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="897ae-136">変数、定数、およびフィールド</span><span class="sxs-lookup"><span data-stu-id="897ae-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="897ae-137">オブジェクトのデータ型の操作</span><span class="sxs-lookup"><span data-stu-id="897ae-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="897ae-138">変数に参照型または値型を割り当てることができます、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="897ae-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="897ae-139">`Object`変数は常に、データそのものでは決してでデータへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="897ae-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="897ae-140">ただし、値の型を割り当てる場合、`Object`変数、動作、独自のデータが保持している場合にします。</span><span class="sxs-lookup"><span data-stu-id="897ae-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="897ae-141">詳細については、次を参照してください。 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="897ae-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="897ae-142">かどうか調べることができます、`Object`に渡すことによって変数が参照型または値の型として機能する、<xref:Microsoft.VisualBasic.Information.IsReference%2A>メソッドで、<xref:Microsoft.VisualBasic.Information>のクラス、<xref:Microsoft.VisualBasic?displayProperty=fullName>名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName></xref:Microsoft.VisualBasic.Information></xref:Microsoft.VisualBasic.Information.IsReference%2A>。</span><span class="sxs-lookup"><span data-stu-id="897ae-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="897ae-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>返します`True`場合の内容、`Object`変数が参照型を表します。</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="897ae-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897ae-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="897ae-144">See Also</span></span>  
 <span data-ttu-id="897ae-145">[Null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="897ae-145">[Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="897ae-146"> [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="897ae-146"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="897ae-147"> [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="897ae-147"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="897ae-148"> [データ型の効率的な使用](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="897ae-148"> [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="897ae-149"> [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="897ae-149"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="897ae-150"> [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="897ae-150"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
