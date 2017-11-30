---
title: "値型と参照型"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b54945d27d186771e8b5353e753afd74c56d71b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="f2ce4-102">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-102">Value Types and Reference Types</span></span>
<span data-ttu-id="f2ce4-103">Visual basic でのデータ型は、分類に基づいて実装します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="f2ce4-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]データ型は、特定の型の変数が、独自のデータまたはデータへのポインターを格納するかどうかによって分類できます。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="f2ce4-105">独自のデータを保管する場合は、*値の型*以外の場合は別の場所はメモリ内のデータへのポインターを保持、*型参照*です。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="f2ce4-106">値型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-106">Value Types</span></span>  
 <span data-ttu-id="f2ce4-107">データ型は、*値の型*独自のメモリ割り当て内のデータが保持している場合。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="f2ce4-108">値の型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="f2ce4-109">すべての数値データ型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="f2ce4-110">`Boolean`、`Char`、および `Date`</span><span class="sxs-lookup"><span data-stu-id="f2ce4-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="f2ce4-111">そのメンバーが参照型である場合でも、すべての構造</span><span class="sxs-lookup"><span data-stu-id="f2ce4-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="f2ce4-112">列挙体、その基になる型は常にため`SByte`、 `Short`、 `Integer`、 `Long`、 `Byte`、 `UShort`、 `UInteger`、または`ULong`</span><span class="sxs-lookup"><span data-stu-id="f2ce4-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="f2ce4-113">すべての構造は、値型、参照型のメンバーが含まれている場合でもです。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="f2ce4-114">このため、値などの型`Char`と`Integer`.NET Framework の構造体によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="f2ce4-115">たとえば、予約済みキーワードを使用して値の型を宣言する`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="f2ce4-116">使用することも、`New`値型を初期化するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="f2ce4-117">これは、型パラメーターを受け取るコンス トラクターがある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="f2ce4-118">この例は、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>コンス トラクターは、新しいビルド`Decimal`指定した部分からの値。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="f2ce4-119">参照型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-119">Reference Types</span></span>  
 <span data-ttu-id="f2ce4-120">A*型参照*データを保持する別のメモリ位置へのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="f2ce4-121">参照型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="f2ce4-122">その要素が値型である場合でも、すべての配列</span><span class="sxs-lookup"><span data-stu-id="f2ce4-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="f2ce4-123">などのクラス型します。<xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="f2ce4-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="f2ce4-124">デリゲート</span><span class="sxs-lookup"><span data-stu-id="f2ce4-124">Delegates</span></span>  
  
 <span data-ttu-id="f2ce4-125">クラスは、*型参照*です。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-125">A class is a *reference type*.</span></span> <span data-ttu-id="f2ce4-126">このためなどの参照型`Object`と`String`でサポートされている[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラスです。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="f2ce4-127">場合でも、そのメンバーは、値の型は、[すべての配列が参照型である注意してください。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="f2ce4-128">使用する必要がありますすべての参照型は、基になる .NET Framework クラスを表すため、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード初期化するときにします。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="f2ce4-129">次のステートメントでは、配列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="f2ce4-130">型ではない要素</span><span class="sxs-lookup"><span data-stu-id="f2ce4-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="f2ce4-131">宣言された要素のデータ型としてそれらのいずれかを指定できないため、次のプログラミング要素は、型とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="f2ce4-132">名前空間</span><span class="sxs-lookup"><span data-stu-id="f2ce4-132">Namespaces</span></span>  
  
-   <span data-ttu-id="f2ce4-133">モジュール</span><span class="sxs-lookup"><span data-stu-id="f2ce4-133">Modules</span></span>  
  
-   <span data-ttu-id="f2ce4-134">イベント</span><span class="sxs-lookup"><span data-stu-id="f2ce4-134">Events</span></span>  
  
-   <span data-ttu-id="f2ce4-135">プロパティやプロシージャ</span><span class="sxs-lookup"><span data-stu-id="f2ce4-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="f2ce4-136">変数、定数、およびフィールド</span><span class="sxs-lookup"><span data-stu-id="f2ce4-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="f2ce4-137">オブジェクトのデータ型の使用</span><span class="sxs-lookup"><span data-stu-id="f2ce4-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="f2ce4-138">変数に参照型または値型のいずれかを割り当てることができます、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="f2ce4-139">`Object`変数は常に、データをデータ自体では決してへのポインターを保持します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="f2ce4-140">ただし、値の型を割り当てる場合、`Object`変数、ように動作、独自のデータを保持します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="f2ce4-141">詳細については、次を参照してください。[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="f2ce4-142">かどうか調べることができます、`Object`に渡すことによって変数が参照型または値の型として機能する、<xref:Microsoft.VisualBasic.Information.IsReference%2A>メソッドで、<xref:Microsoft.VisualBasic.Information>のクラス、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f2ce4-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>返します`True`場合のコンテンツ、`Object`変数が参照型を表します。</span><span class="sxs-lookup"><span data-stu-id="f2ce4-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ce4-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2ce4-144">See Also</span></span>  
 [<span data-ttu-id="f2ce4-145">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="f2ce4-146">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="f2ce4-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="f2ce4-147">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="f2ce4-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="f2ce4-148">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="f2ce4-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="f2ce4-149">Object 型</span><span class="sxs-lookup"><span data-stu-id="f2ce4-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="f2ce4-150">データの種類</span><span class="sxs-lookup"><span data-stu-id="f2ce4-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
