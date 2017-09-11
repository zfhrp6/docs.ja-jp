---
title: "方法 : 文字列の内容を変更する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
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
ms.openlocfilehash: 114b6fdabd235d7e57947e77b672352e28aff11e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-string-contents-c-programming-guide"></a><span data-ttu-id="700b9-102">方法 : 文字列の内容を変更する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="700b9-102">How to: Modify String Contents (C# Programming Guide)</span></span>
<span data-ttu-id="700b9-103">文字列は*不変*であるため、作成後に文字列オブジェクトの値を (アンセーフ コードを使用せずに) 変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="700b9-103">Because strings are *immutable*, it is not possible (without using unsafe code) to modify the value of a string object after it has been created.</span></span> <span data-ttu-id="700b9-104">ただし、文字列の値を変更し、新しい文字列オブジェクトに結果を格納する方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="700b9-104">However, there are many ways to modify the value of a string and store the result in a new string object.</span></span> <span data-ttu-id="700b9-105"><xref:System.String?displayProperty=fullName> クラスでは、入力文字列を操作し、新しい文字列オブジェクトを返すメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="700b9-105">The <xref:System.String?displayProperty=fullName> class provides methods that operate on an input string and return a new string object.</span></span> <span data-ttu-id="700b9-106">多くの場合、元の文字列を保持する変数に新しいオブジェクトを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="700b9-106">In many cases, you can assign the new object to the variable that held the original string.</span></span> <span data-ttu-id="700b9-107"><xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> クラスでは、同じように動作する追加のメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="700b9-107">The <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> class provides additional methods that work in a similar manner.</span></span> <span data-ttu-id="700b9-108"><xref:System.Text.StringBuilder?displayProperty=fullName> クラスは、"埋め込み先" を変更できる文字バッファーを提供します。</span><span class="sxs-lookup"><span data-stu-id="700b9-108">The <xref:System.Text.StringBuilder?displayProperty=fullName> class provides a character buffer that you can modify "in-place."</span></span> <span data-ttu-id="700b9-109"><xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> メソッドを呼び出して、バッファーの現在の内容を含む新しい文字列オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="700b9-109">You call the <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> method to create a new string object that contains the current contents of the buffer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="700b9-110">例</span><span class="sxs-lookup"><span data-stu-id="700b9-110">Example</span></span>  
 <span data-ttu-id="700b9-111">次の例では、指定された文字列で部分文字列の置換や削除を行うさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="700b9-111">The following example shows various ways to replace or remove substrings in a specified string.</span></span>  
  
 <span data-ttu-id="700b9-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="700b9-112">[!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="700b9-113">例</span><span class="sxs-lookup"><span data-stu-id="700b9-113">Example</span></span>  
 <span data-ttu-id="700b9-114">配列表記を使用して文字列内の個々の文字にアクセスする場合は、<xref:System.Text.StringBuilder> オブジェクトを使用できます。このオブジェクトは、`[]` 演算子をオーバーロードして、その内部文字バッファーへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="700b9-114">To access the individual characters in a string by using array notation, you can use the <xref:System.Text.StringBuilder> object, which overloads the `[]` operator to provide access to its internal character buffer.</span></span> <span data-ttu-id="700b9-115">また、<xref:System.String.ToCharArray%2A> メソッドを使用して、文字列を文字配列に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="700b9-115">You can also convert the string to an array of chars by using the <xref:System.String.ToCharArray%2A> method.</span></span> <span data-ttu-id="700b9-116">次の例では、`ToCharArray` を使用して配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="700b9-116">The following example uses `ToCharArray` to create the array.</span></span> <span data-ttu-id="700b9-117">その後、この配列の一部の要素が変更されます。</span><span class="sxs-lookup"><span data-stu-id="700b9-117">Some elements of this array are then modified.</span></span> <span data-ttu-id="700b9-118">さらに、新しい文字列を作成するために、入力パラメーターとして文字配列を受け取る文字列コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="700b9-118">A string constructor that takes a char array as an input parameter is then called to create a new string.</span></span>  
  
 <span data-ttu-id="700b9-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="700b9-119">[!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="700b9-120">例</span><span class="sxs-lookup"><span data-stu-id="700b9-120">Example</span></span>  
 <span data-ttu-id="700b9-121">次の例は、C スタイルの文字配列と同様の方法で、アンセーフ コードを使用して埋め込み文字列を変更する、非常にまれな場合のために用意したものです。</span><span class="sxs-lookup"><span data-stu-id="700b9-121">The following example is provided for those very rare situations in which you may want to modify a string in-place by using unsafe code in a manner similar to C-style char arrays.</span></span> <span data-ttu-id="700b9-122">この例では、fixed キーワードを使用して、"埋め込まれている" 個々の文字にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="700b9-122">The example shows how to access the individual characters "in-place" by using the fixed keyword.</span></span> <span data-ttu-id="700b9-123">また、文字列に対してアンセーフ操作を実行すると発生する可能性のある副作用を示します。この副作用の原因は、C# コンパイラが文字列を内部に格納する (保持する) 方法にあります。</span><span class="sxs-lookup"><span data-stu-id="700b9-123">It also demonstrates one possible side effect of unsafe operations on strings that results from the way that the C# compiler stores (interns) strings internally.</span></span> <span data-ttu-id="700b9-124">通常、この方法は、特に必要な場合以外は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="700b9-124">In general, you should not use this technique unless it is absolutely necessary.</span></span>  
  
 <span data-ttu-id="700b9-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="700b9-125">[!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700b9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="700b9-126">See Also</span></span>  
 <span data-ttu-id="700b9-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="700b9-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="700b9-128">文字列</span><span class="sxs-lookup"><span data-stu-id="700b9-128">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

