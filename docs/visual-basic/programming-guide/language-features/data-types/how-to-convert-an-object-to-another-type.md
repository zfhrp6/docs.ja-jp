---
title: '方法: Visual Basic でオブジェクトを別の型に変換する'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="76b18-102">方法: Visual Basic でオブジェクトを別の型に変換する</span><span class="sxs-lookup"><span data-stu-id="76b18-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="76b18-103">変換する、`Object`変数などの変換キーワードを使用して、別のデータ型を[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="76b18-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76b18-104">例</span><span class="sxs-lookup"><span data-stu-id="76b18-104">Example</span></span>  
 <span data-ttu-id="76b18-105">次の例では、変換、`Object`変数を`Integer`と`String`です。</span><span class="sxs-lookup"><span data-stu-id="76b18-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="76b18-106">わかっている場合の内容、`Object`変数は、特定のデータ型の方が優れている変数をそのデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="76b18-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="76b18-107">引き続き使用する場合、`Object`いずれかが発生する変数、*ボックス化*と*アンボックス*(の値型) または*遅延バインディング*(の参照型)。</span><span class="sxs-lookup"><span data-stu-id="76b18-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="76b18-108">これらの操作では追加の実行時間がかかるすべてで、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="76b18-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76b18-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76b18-109">Compiling the Code</span></span>  
 <span data-ttu-id="76b18-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="76b18-110">This example requires:</span></span>  
  
-   <span data-ttu-id="76b18-111"><xref:System?displayProperty=nameWithType> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="76b18-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b18-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="76b18-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="76b18-113">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="76b18-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="76b18-114">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="76b18-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="76b18-115">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="76b18-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="76b18-116">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="76b18-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="76b18-117">配列変換</span><span class="sxs-lookup"><span data-stu-id="76b18-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="76b18-118">構造体</span><span class="sxs-lookup"><span data-stu-id="76b18-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="76b18-119">データの種類</span><span class="sxs-lookup"><span data-stu-id="76b18-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="76b18-120">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="76b18-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
