---
title: "データ ソースの LINQ クエリの有効化 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a5eaa6472c5fd7942f345dc5b4401b85c33504c9
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>データ ソースの LINQ クエリの有効化
[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] を拡張して、データ ソースを [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] パターンでクエリできるようにする方法はいくつかあります。 データ ソースは、いくつか例を挙げると、データ構造体、Web サービス、ファイル システム、またはデータベースの場合があります。 クエリの構文とパターンは変わらないため、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] パターンを使用すると、クライアントは [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリが有効になっているデータ ソースを簡単にクエリできます。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] は、次の方法によってこれらのデータ ソースに拡張することができます。  
  
-   型内で <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装して、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] でその型のオブジェクトを照会できるようにする。  
  
-   型を拡張する <xref:System.Linq.Enumerable.Where%2A> や <xref:System.Linq.Enumerable.Select%2A> などの標準クエリ演算子メソッドを作成して、その型のカスタム [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを有効にする。  
  
-   データ ソース用に、<xref:System.Linq.IQueryable%601> インターフェイスを実装したプロバイダーを作成する。 このインターフェイスを実装したプロバイダーは、式ツリーの形式で [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを受け取ります。プロバイダーはこれをカスタマイズされた方法 (たとえばリモート) で実行できます。  
  
-   データ ソース用に、既存の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] テクノロジを利用するプロバイダーを作成する。 そのようなプロバイダーは、クエリだけでなく、挿入、更新、および削除などの操作や、ユーザー定義型のマッピングも有効にします。  
  
 このトピックでは、これらのオプションについて説明します。  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>データ ソースの LINQ クエリを有効にする方法  
  
### <a name="in-memory-data"></a>インメモリ データ  
 インメモリ データの [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを有効にする方法は 2 つあります。 データ型が <xref:System.Collections.Generic.IEnumerable%601> を実装する型の場合、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to Objects を使用してデータをクエリすることができます。 <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装して型の列挙体を有効にしても意味がない場合は、その型の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 標準クエリ演算子メソッドを定義するか、または型を拡張する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 標準クエリ演算子メソッドを作成することができます。 標準クエリ演算子のカスタム実装は、結果を返すために遅延実行を使用する必要があります。  
  
### <a name="remote-data"></a>リモート データ  
 リモート データ ソースの [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを有効にするための最善の選択肢は、<xref:System.Linq.IQueryable%601> インターフェイスを実装することです。 しかしこれは、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] などのプロバイダーをデータ ソースに対して拡張することとは別です。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] では、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] などの既存の [!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)] テクノロジを別の型のデータ ソースに拡張するためにプロバイダー モデルを使用することができません。  
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ プロバイダー  
 <xref:System.Linq.IQueryable%601> を実装する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] プロバイダーの複雑度にはかなりのばらつきがあります。 このセクションでは、さまざまなレベルの複雑度について説明します。  
  
 複雑度が低めの `IQueryable` プロバイダーは、多くの場合、Web サービスの単一のメソッドとやり取りします。 この種のプロバイダーは処理するクエリに特定の情報を受け取るので非常に高い固有性を持ちます。 クローズされた型システムを持ち、おそらく 1 つの結果型を公開します。 クエリはほとんどの場合、標準クエリ演算子の <xref:System.Linq.Enumerable> 実装などを使用して、ローカルで実行されます。 複雑度が低めのプロバイダーは、クエリを表す式ツリーのメソッド呼び出し式を 1 つだけ調べ、残りのクエリのロジックは他の場所で処理されるようにします。  
  
 複雑度が中レベルの `IQueryable` プロバイダーは、部分的に表現力が豊かなクエリ言語を持つデータ ソースを対象とします。 そのプロバイダーが Web サービスを対象とする場合、Web サービスの複数のメソッドとやり取りし、クエリが提示する問題に基づいて呼び出すメソッドを選択します。 中レベルの複雑度のプロバイダーは、簡単なプロバイダーより型システムが豊富ですが、それでもその種類は限られています。 たとえば、このレベルのプロバイダーは走査できる一対多リレーションシップを持つ型を公開する場合がありますが、ユーザー定義型のマッピング テクノロジは提供しません。  
  
 `IQueryable` プロバイダーなどの複雑な [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] プロバイダーは [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリ一式を、SQL などの表現力が豊かなクエリ言語に変換する場合があります。 複雑なプロバイダーは、それほど複雑でないプロバイダーより一般的です。これは、より多様な質問をクエリで処理できるためです。 さらに、オープンな型システムを持つため、ユーザー定義型をマップするために広範なインフラストラクチャを含める必要があります。 複雑なプロバイダーの開発には、多大な労力を要します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable>   
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
