---
title: ".NET の文字列からの文字のトリムと削除"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dac047c7efefcacb959401aedcb96080810f2278
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="6660a-102">.NET の文字列からの文字のトリムと削除</span><span class="sxs-lookup"><span data-stu-id="6660a-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="6660a-103">文章を個々の単語に分割すると、単語の先頭または末尾に空白が残る場合があります。</span><span class="sxs-lookup"><span data-stu-id="6660a-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="6660a-104">そのような場合は、**System.String** クラスのトリム メソッドのいずれかを使用して、文字列内の指定した位置から任意の数の空白またはその他の文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="6660a-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="6660a-105">使用できるトリム メソッドとその説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="6660a-106">メソッド名</span><span class="sxs-lookup"><span data-stu-id="6660a-106">Method name</span></span>|<span data-ttu-id="6660a-107">使用</span><span class="sxs-lookup"><span data-stu-id="6660a-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="6660a-108">文字列の先頭と末尾から、空白または文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="6660a-109">文字列の末尾から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="6660a-110">文字列の先頭から、文字配列で指定した文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="6660a-111">文字列内の指定したインデックス位置から、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="6660a-112">Trim</span><span class="sxs-lookup"><span data-stu-id="6660a-112">Trim</span></span>  
 <span data-ttu-id="6660a-113"><xref:System.String.Trim%2A?displayProperty=nameWithType> メソッドを使用すると、文字列の両端から空白を簡単に削除できます。メソッドの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="6660a-114">文字列の先頭と末尾から、文字配列で指定した文字を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="6660a-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="6660a-115">次に、空白文字、ピリオド、およびアスタリスクを削除する例を示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="6660a-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="6660a-116">TrimEnd</span></span>  
 <span data-ttu-id="6660a-117">**String.TrimEnd** メソッドは、文字列の末尾から文字を削除して新しい文字列オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6660a-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="6660a-118">このメソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="6660a-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="6660a-119">文字配列内での要素の順序は、トリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="6660a-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="6660a-120">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="6660a-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="6660a-121">**TrimEnd** メソッドを使用して文字列の末尾の数文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="6660a-122">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'r'` という文字と `'W'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="6660a-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="6660a-123">このコードは、`MyString` の最後の単語だけでなく、最初の単語の一部も削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="6660a-124">このコードは、コンソールに `He` と出力します。</span><span class="sxs-lookup"><span data-stu-id="6660a-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="6660a-125">**TrimEnd** メソッドを使用して、文字列の最後の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="6660a-126">このコードでは、`Hello` という単語の後にコンマがありますが、削除する文字の配列にコンマは指定されていないため、コンマの位置でトリムが停止します。</span><span class="sxs-lookup"><span data-stu-id="6660a-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="6660a-127">このコードは、コンソールに `Hello,` と出力します。</span><span class="sxs-lookup"><span data-stu-id="6660a-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="6660a-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="6660a-128">TrimStart</span></span>  
 <span data-ttu-id="6660a-129">**String.TrimStart** メソッドは **String.TrimEnd** メソッドと似ていますが、既存の文字列オブジェクトの先頭から文字を削除して新しい文字列を作成する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="6660a-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="6660a-130">**TrimStart** メソッドには、削除する文字を指定する文字配列が渡されます。</span><span class="sxs-lookup"><span data-stu-id="6660a-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="6660a-131">**TrimEnd** メソッドの場合と同様に、文字配列内での要素の順序はトリム操作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="6660a-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="6660a-132">トリム操作は、文字配列で指定された文字が見つからなくなった時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="6660a-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="6660a-133">文字列の最初の単語を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="6660a-134">この例では、文字配列内の文字の順序が操作に影響しないことを示すために、`'l'` という文字と `'H'` という文字の順序を逆にしてあります。</span><span class="sxs-lookup"><span data-stu-id="6660a-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="6660a-135">このコードは、コンソールに `World!` と出力します。</span><span class="sxs-lookup"><span data-stu-id="6660a-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="6660a-136">削除</span><span class="sxs-lookup"><span data-stu-id="6660a-136">Remove</span></span>  
 <span data-ttu-id="6660a-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> メソッドは、既存の文字列内の指定した位置を開始位置として、指定した数の文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="6660a-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="6660a-138">このメソッドは、インデックスが 0 から始まっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="6660a-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="6660a-139">文字列の 0 から始まる 5 番目のインデックスを開始位置として、10 文字を削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="6660a-140">また、<xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> メソッドを呼び出し、置換対象として空の文字列 (<xref:System.String.Empty?displayProperty=nameWithType>) を指定することで、文字列から指定した文字または部分文字列を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="6660a-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="6660a-141">文字列からすべてのコンマを削除する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6660a-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="6660a-142">参照</span><span class="sxs-lookup"><span data-stu-id="6660a-142">See Also</span></span>  
 [<span data-ttu-id="6660a-143">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="6660a-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
