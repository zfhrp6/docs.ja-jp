---
title: "方法 : 文字列の内容を変更する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a><span data-ttu-id="8bdf2-102">方法 : 文字列の内容を変更する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8bdf2-102">How to: Modify String Contents (C# Programming Guide)</span></span>
<span data-ttu-id="8bdf2-103">文字列は*不変*であるため、作成後に文字列オブジェクトの値を (アンセーフ コードを使用せずに) 変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-103">Because strings are *immutable*, it is not possible (without using unsafe code) to modify the value of a string object after it has been created.</span></span> <span data-ttu-id="8bdf2-104">ただし、文字列の値を変更し、新しい文字列オブジェクトに結果を格納する方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-104">However, there are many ways to modify the value of a string and store the result in a new string object.</span></span> <span data-ttu-id="8bdf2-105"><xref:System.String?displayProperty=nameWithType> クラスでは、入力文字列を操作し、新しい文字列オブジェクトを返すメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-105">The <xref:System.String?displayProperty=nameWithType> class provides methods that operate on an input string and return a new string object.</span></span> <span data-ttu-id="8bdf2-106">多くの場合、元の文字列を保持する変数に新しいオブジェクトを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-106">In many cases, you can assign the new object to the variable that held the original string.</span></span> <span data-ttu-id="8bdf2-107"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> クラスでは、同じように動作する追加のメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-107">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides additional methods that work in a similar manner.</span></span> <span data-ttu-id="8bdf2-108"><xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスは、"埋め込み先" を変更できる文字バッファーを提供します。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-108">The <xref:System.Text.StringBuilder?displayProperty=nameWithType> class provides a character buffer that you can modify "in-place."</span></span> <span data-ttu-id="8bdf2-109"><xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> メソッドを呼び出して、バッファーの現在の内容を含む新しい文字列オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-109">You call the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> method to create a new string object that contains the current contents of the buffer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bdf2-110">例</span><span class="sxs-lookup"><span data-stu-id="8bdf2-110">Example</span></span>  
 <span data-ttu-id="8bdf2-111">次の例では、指定された文字列で部分文字列の置換や削除を行うさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-111">The following example shows various ways to replace or remove substrings in a specified string.</span></span>  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8bdf2-112">例</span><span class="sxs-lookup"><span data-stu-id="8bdf2-112">Example</span></span>  
 <span data-ttu-id="8bdf2-113">配列表記を使用して文字列内の個々の文字にアクセスする場合は、<xref:System.Text.StringBuilder> オブジェクトを使用できます。このオブジェクトは、`[]` 演算子をオーバーロードして、その内部文字バッファーへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-113">To access the individual characters in a string by using array notation, you can use the <xref:System.Text.StringBuilder> object, which overloads the `[]` operator to provide access to its internal character buffer.</span></span> <span data-ttu-id="8bdf2-114">また、<xref:System.String.ToCharArray%2A> メソッドを使用して、文字列を文字配列に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-114">You can also convert the string to an array of chars by using the <xref:System.String.ToCharArray%2A> method.</span></span> <span data-ttu-id="8bdf2-115">次の例では、`ToCharArray` を使用して配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-115">The following example uses `ToCharArray` to create the array.</span></span> <span data-ttu-id="8bdf2-116">その後、この配列の一部の要素が変更されます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-116">Some elements of this array are then modified.</span></span> <span data-ttu-id="8bdf2-117">さらに、新しい文字列を作成するために、入力パラメーターとして文字配列を受け取る文字列コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-117">A string constructor that takes a char array as an input parameter is then called to create a new string.</span></span>  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8bdf2-118">例</span><span class="sxs-lookup"><span data-stu-id="8bdf2-118">Example</span></span>  
 <span data-ttu-id="8bdf2-119">次の例は、C スタイルの文字配列と同様の方法で、アンセーフ コードを使用して埋め込み文字列を変更する、非常にまれな場合のために用意したものです。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-119">The following example is provided for those very rare situations in which you may want to modify a string in-place by using unsafe code in a manner similar to C-style char arrays.</span></span> <span data-ttu-id="8bdf2-120">この例では、fixed キーワードを使用して、"埋め込まれている" 個々の文字にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-120">The example shows how to access the individual characters "in-place" by using the fixed keyword.</span></span> <span data-ttu-id="8bdf2-121">また、文字列に対してアンセーフ操作を実行すると発生する可能性のある副作用を示します。この副作用の原因は、C# コンパイラが文字列を内部に格納する (保持する) 方法にあります。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-121">It also demonstrates one possible side effect of unsafe operations on strings that results from the way that the C# compiler stores (interns) strings internally.</span></span> <span data-ttu-id="8bdf2-122">通常、この方法は、特に必要な場合以外は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8bdf2-122">In general, you should not use this technique unless it is absolutely necessary.</span></span>  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8bdf2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bdf2-123">See Also</span></span>  
 [<span data-ttu-id="8bdf2-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8bdf2-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8bdf2-125">文字列</span><span class="sxs-lookup"><span data-stu-id="8bdf2-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
