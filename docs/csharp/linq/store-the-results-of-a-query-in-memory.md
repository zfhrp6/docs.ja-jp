---
title: "クエリ結果をメモリに格納する"
description: "結果の格納方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a>クエリ結果をメモリに格納する

クエリは、基本的に、データの取得方法と編成方法を指示するための一連の命令です。 結果の各項目は順次要求されるため、クエリは遅延実行されます。 `foreach` を使用して結果を反復すると、項目はアクセスのたびに返されます。 クエリを評価し、`foreach` のループを実行せずに結果を格納するには、クエリ変数で次のメソッドのいずれかを呼び出します。  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 クエリ結果を格納するときは、次の例に示すように、返されたコレクション オブジェクトを新しい変数に割り当てることをお勧めします。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)
