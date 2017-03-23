---
title: "LINQ Querying2 のデータ ソースの有効化 |Microsoft ドキュメント"
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
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34bdc4e056d982799eac35eb2398dd3f23f6f351
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>データ ソースの LINQ クエリの有効化
さまざまな方法で拡張する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]でクエリを実行する任意のデータ ソースを有効にする、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]パターンです。 データ ソースは、いくつか例を挙げると、データ構造体、Web サービス、ファイル システム、またはデータベースの場合があります。 クエリの構文とパターンは変わらないため、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] パターンを使用すると、クライアントは [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリが有効になっているデータ ソースを簡単にクエリできます。 方法[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]を拡張できるこれらのデータをソースには、次が含まれます。  
  
-   実装する、<xref:System.Collections.Generic.IEnumerable%601>インターフェイスを有効にするのには、タイプで[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]その型のオブジェクトを照会します</xref:System.Collections.Generic.IEnumerable%601>。  
  
-   標準クエリ演算子メソッドのなど作成<xref:System.Linq.Enumerable.Where%2A>と<xref:System.Linq.Enumerable.Select%2A>ユーザー設定を有効にする、型を拡張する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]その型のクエリを実行します</xref:System.Linq.Enumerable.Select%2A></xref:System.Linq.Enumerable.Where%2A>。  
  
-   実装するデータ ソースのプロバイダーを作成する、<xref:System.Linq.IQueryable%601>インターフェイス</xref:System.Linq.IQueryable%601>。 このインターフェイスを実装したプロバイダーは、式ツリーの形式で [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを受け取ります。プロバイダーはこれをカスタマイズされた方法 (たとえばリモート) で実行できます。  
  
-   既存の活用、データ ソースのプロバイダーを作成する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]テクノロジです。 そのようなプロバイダーは、クエリだけでなく、挿入、更新、および削除などの操作や、ユーザー定義型のマッピングも有効にします。  
  
 このトピックでは、これらのオプションについて説明します。  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>データ ソースの LINQ クエリを有効にする方法  
  
### <a name="in-memory-data"></a>インメモリ データ  
 2 つの方法が有効にできます[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]メモリ内のデータのクエリを実行します。 実装する型の場合は、データ<xref:System.Collections.Generic.IEnumerable%601>を使用して、データを照会する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]オブジェクトにします</xref:System.Collections.Generic.IEnumerable%601>。 実装することで、型の列挙体を有効にする意味が行わないかどうか、<xref:System.Collections.Generic.IEnumerable%601>インターフェイスを定義できます[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]標準クエリ演算子メソッドをその型または作成[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]標準クエリ演算子メソッド型を拡張する</xref:System.Collections.Generic.IEnumerable%601>。 標準クエリ演算子のカスタム実装は、結果を返すために遅延実行を使用する必要があります。  
  
### <a name="remote-data"></a>リモート データ  
 有効にするための最適なオプション[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]を実装するのには、リモート データ ソースのクエリ、<xref:System.Linq.IQueryable%601>インターフェイス</xref:System.Linq.IQueryable%601>。 しかしこれは、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] などのプロバイダーをデータ ソースに対して拡張することとは別です。 既存の拡張するためにプロバイダー モデル[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]テクノロジなど[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] でその他の型のデータ ソースが利用[!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)]します。  
  
## <a name="iqueryable-linq-providers"></a>IQueryable LINQ プロバイダー  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]実装したプロバイダー<xref:System.Linq.IQueryable%601>複雑度に大きく異なることができます</xref:System.Linq.IQueryable%601>。 このセクションでは、さまざまなレベルの複雑度について説明します。  
  
 複雑度が低めの `IQueryable` プロバイダーは、多くの場合、Web サービスの単一のメソッドとやり取りします。 この種のプロバイダーは処理するクエリに特定の情報を受け取るので非常に高い固有性を持ちます。 クローズされた型システムを持ち、おそらく&1; つの結果型を公開します。 たとえばを使用するクエリの実行のほとんどがローカルで発生する、<xref:System.Linq.Enumerable>標準クエリ演算子の実装</xref:System.Linq.Enumerable>。 複雑度が低めのプロバイダーは、クエリを表す式ツリーのメソッド呼び出し式を&1; つだけ調べ、残りのクエリのロジックは他の場所で処理されるようにします。  
  
 複雑度が中レベルの `IQueryable` プロバイダーは、部分的に表現力が豊かなクエリ言語を持つデータ ソースを対象とします。 そのプロバイダーが Web サービスを対象とする場合、Web サービスの複数のメソッドとやり取りし、クエリが提示する問題に基づいて呼び出すメソッドを選択します。 中レベルの複雑度のプロバイダーは、簡単なプロバイダーより型システムが豊富ですが、それでもその種類は限られています。 たとえば、このレベルのプロバイダーは走査できる一対多リレーションシップを持つ型を公開する場合がありますが、ユーザー定義型のマッピング テクノロジは提供しません。  
  
 `IQueryable` プロバイダーなどの複雑な [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] プロバイダーは [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリ一式を、SQL などの表現力が豊かなクエリ言語に変換する場合があります。 複雑なプロバイダーは、それほど複雑でないプロバイダーより一般的です。これは、より多様な質問をクエリで処理できるためです。 さらに、オープンな型システムを持つため、ユーザー定義型をマップするために広範なインフラストラクチャを含める必要があります。 複雑なプロバイダーの開発には、多大な労力を要します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.IQueryable%601></xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
