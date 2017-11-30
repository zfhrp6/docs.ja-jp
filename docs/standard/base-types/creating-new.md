---
title: ".NET での新しい文字列を作成します。"
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
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="a8336-102">.NET での新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="a8336-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]により、単純な代入を使用して作成される文字列とも異なるパラメーターの番号を使用して文字列の作成をサポートするクラスのコンス トラクター オーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="a8336-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="a8336-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]もいくつかのメソッドを提供、<xref:System.String?displayProperty=nameWithType>新しい文字列を作成するクラスがいくつかの文字列、文字列の配列を組み合わせることによってオブジェクトまたはオブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="a8336-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="a8336-105">割り当てを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="a8336-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="a8336-106">新しいを作成する最も簡単な方法<xref:System.String>オブジェクトを単に文字列リテラルを代入する<xref:System.String>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a8336-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="a8336-107">クラス コンストラクターを使用した文字列の作成</span><span class="sxs-lookup"><span data-stu-id="a8336-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="a8336-108">オーバー ロードを使用することができます、<xref:System.String>クラス コンス トラクターを文字配列から文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="a8336-109">また、指定した回数だけ特定の文字を複製することで、新しい文字列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8336-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="a8336-110">文字列を返すメソッド</span><span class="sxs-lookup"><span data-stu-id="a8336-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="a8336-111">次の表は、新しい文字列オブジェクトを返すいくつかの便利なメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8336-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="a8336-112">メソッド名</span><span class="sxs-lookup"><span data-stu-id="a8336-112">Method name</span></span>|<span data-ttu-id="a8336-113">用途</span><span class="sxs-lookup"><span data-stu-id="a8336-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="a8336-114">入力オブジェクトのセットから、書式設定された文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a8336-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="a8336-115">2 つ以上の文字列から文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a8336-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="a8336-116">文字列の配列を組み合わせることで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a8336-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="a8336-117">既存の文字列の指定のインデックスに文字列を挿入することで、新しい文字列をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a8336-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="a8336-118">文字配列内の指定の位置に、文字列内の指定の文字をコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8336-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="a8336-119">形式</span><span class="sxs-lookup"><span data-stu-id="a8336-119">Format</span></span>  
 <span data-ttu-id="a8336-120">使用することができます、 **String.Format**複数のオブジェクトを表す文字列を書式設定された文字列を作成し、連結します。</span><span class="sxs-lookup"><span data-stu-id="a8336-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="a8336-121">このメソッドは、渡されたすべてのオブジェクトを文字列に自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="a8336-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="a8336-122">たとえば、アプリケーションを表示する必要があります、 **Int32**値と**DateTime**値、ユーザーを使用してこれらの値を表す文字列を簡単に作成できる、**形式**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a8336-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="a8336-123">このメソッドで使用される書式設定規則については、[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8336-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="a8336-124">次の例では、**形式**整数変数を使用する文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="a8336-125">この例では<xref:System.DateTime.Now%2A?displayProperty=nameWithType>現在のスレッドに関連付けられているカルチャで指定された方法で現在の日付と時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="a8336-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="a8336-126">Concat</span><span class="sxs-lookup"><span data-stu-id="a8336-126">Concat</span></span>  
 <span data-ttu-id="a8336-127">**String.Concat**を簡単に 2 つ以上の既存のオブジェクトから、新しい文字列オブジェクトを作成するメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8336-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="a8336-128">言語に依存せずに文字列を連結する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="a8336-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="a8336-129">このメソッドから派生した任意のクラスを受け入れる**System.Object**です。</span><span class="sxs-lookup"><span data-stu-id="a8336-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="a8336-130">次の例では、2 つの既存の文字列オブジェクトおよび区切り文字から文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="a8336-131">Join</span><span class="sxs-lookup"><span data-stu-id="a8336-131">Join</span></span>  
 <span data-ttu-id="a8336-132">**先**メソッドは、文字列と区切り記号文字列の配列から新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="a8336-133">このメソッドは、複数の文字列を連結して、たとえばコンマで区切られたリストを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a8336-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="a8336-134">次の例では、スペースを使用して文字列の配列をバインドします。</span><span class="sxs-lookup"><span data-stu-id="a8336-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="a8336-135">挿入</span><span class="sxs-lookup"><span data-stu-id="a8336-135">Insert</span></span>  
 <span data-ttu-id="a8336-136">**String.Insert**メソッドは、文字列を別の文字列内の指定位置に挿入すると、新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="a8336-137">このメソッドは、0 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8336-137">This method uses a zero-based index.</span></span> <span data-ttu-id="a8336-138">次の例では、`MyString` の 5 番目のインデックス位置に文字列を挿入し、この値を持つ新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8336-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="a8336-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="a8336-139">CopyTo</span></span>  
 <span data-ttu-id="a8336-140">**String.CopyTo**メソッドは、文字列の一部分を文字の配列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8336-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="a8336-141">文字列の開始インデックスと、コピーする文字数の両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8336-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="a8336-142">このメソッドは、ソース インデックス、文字配列、コピー先のインデックス、およびコピーする文字数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a8336-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="a8336-143">すべてのインデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="a8336-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="a8336-144">次の例では、 **CopyTo**にオブジェクトの文字列「こんにちは」という語の文字を文字の配列の最初のインデックス位置にコピーする方法です。</span><span class="sxs-lookup"><span data-stu-id="a8336-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a8336-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8336-145">See Also</span></span>  
 [<span data-ttu-id="a8336-146">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="a8336-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="a8336-147">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="a8336-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
