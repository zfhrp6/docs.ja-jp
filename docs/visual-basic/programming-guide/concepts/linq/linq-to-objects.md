---
title: "LINQ to Objects (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 82094ee6232ef5b1884f1b4b15eacb635be758aa
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="ae8a7-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="ae8a7-103">「LINQ オブジェクト」とは、LINQ の使用をいずれかと照会<xref:System.Collections.IEnumerable>または<xref:System.Collections.Generic.IEnumerable%601>コレクション、中間の LINQ プロバイダーやなどの API を使用せず、直接[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)または[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> 。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="ae8a7-104">LINQ を使用するには任意の列挙可能なコレクションなどのクエリに<xref:System.Collections.Generic.List%601>、 <xref:System.Array>、または<xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="ae8a7-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="ae8a7-105">コレクションがユーザー定義か .NET Framework API によって返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="ae8a7-106">基本的な意味では、LINQ to Objects は、コレクションへの新しいアプローチを表します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="ae8a7-107">従来の方法では、複雑な `For Each` ループを記述して、コレクションからデータを取得する方法を指定する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="ae8a7-108">LINQ のアプローチでは、説明を取得する表す宣言コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="ae8a7-109">LINQ クエリがさらに、従来の経由での&3; つの主な利点を提供`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1.  <span data-ttu-id="ae8a7-110">簡潔で読みやすい (特に複数の条件をフィルター処理する場合)。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="ae8a7-111">強力なフィルター処理、並べ替え、およびグループ化機能を最小限のアプリケーション コードで実現できる。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="ae8a7-112">ほとんど、またはまったく変更せずに、他のデータ ソースに移植できる。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="ae8a7-113">一般より複雑なデータに対して実行する操作、LINQ を使用して、従来の反復処理の手法ではなく、実現が利点も増えます。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="ae8a7-114">このセクションの目的は、いくつかの選択の例で、LINQ アプローチを示すためにです。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="ae8a7-115">ただし、すべてを網羅したものではありません。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae8a7-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ae8a7-116">In This Section</span></span>  
 [<span data-ttu-id="ae8a7-117">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="ae8a7-118">LINQ を使用して、文字列および文字列のコレクションの照会し、変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="ae8a7-119">これらの基本原則を具体的に示すトピックへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="ae8a7-120">LINQ とリフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="ae8a7-121">LINQ がリフレクションを使用する方法を示すサンプルへのリンク。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="ae8a7-122">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="ae8a7-123">LINQ を使用して、ファイル システムと対話する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="ae8a7-124">これらの概念を具体的に示すトピックへのリンクも含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="ae8a7-125">方法: クエリ、LINQ で ArrayList を (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="ae8a7-126">C# の ArrayList を照会する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="ae8a7-127">方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加</span><span class="sxs-lookup"><span data-stu-id="ae8a7-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="ae8a7-128">LINQ クエリを使用する拡張メソッドを追加することでメソッドのセットを拡張する方法について説明します<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="ae8a7-129">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8a7-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="ae8a7-130">LINQ を説明し、クエリを実行するコードの例を紹介するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ae8a7-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
