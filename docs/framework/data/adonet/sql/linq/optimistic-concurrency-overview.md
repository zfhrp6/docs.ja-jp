---
title: "Optimistic Concurrency: Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Optimistic Concurrency: Overview
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はオプティミスティック同時実行制御をサポートします。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ドキュメントでオプティミスティック同時実行の説明に使用している用語を次の表に示します。  
  
|用語|説明|  
|--------|--------|  
|同時実行|2 人以上のユーザーがデータベースの同じ行を同時に更新しようとした状況のことです。|  
|同時実行の競合|2 人以上のユーザーが、行の中の 1 つまたは複数の列に対し、互いに競合する値を送信しようとした状況のことです。|  
|同時実行制御|同時実行の競合を解決するために使用する手法のことです。|  
|オプティミスティック同時実行制御|他のトランザクションが行の値に変更を加えていないかどうかをまず調べたうえで変更の送信を許可する手法のことです。<br /><br /> これと対照的なのが*ペシミスティック同時実行制御*で、レコードをロックすることで同時実行の競合を防ぎます。<br /><br /> *オプティミスティック* \(楽観的\) という名前が付いているのは、トランザクションどうしが競合する可能性は小さいものと見なす方法であるためです。|  
|競合の解決|データベースを再度クエリしてから相違点を調整することによって競合する項目を更新する処理のことです。<br /><br /> オブジェクトを更新するときには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の変更トラッカーによって、以下のデータが記録されます。<br /><br /> -   データベースからもともと取得し、更新チェックに使用した値。<br />-   その後のクエリで取得した新しいデータベース値。<br /><br /> 次に [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトが競合しているかどうか \(つまり 1 つまたは複数のメンバー値が変更されているかどうか\) を判断します。  オブジェクトが競合している場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は次に、どのメンバーが競合しているかを判断します。<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が見つけたメンバーの競合は、競合の一覧に追加されます。|  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のオブジェクト モデルで*オプティミスティック同時実行の競合*が発生するのは、次の 2 つの条件が両方とも成り立つ場合です。  
  
-   クライアントがデータベースに変更を送信しようとした。  
  
-   データベースで、そのクライアントによる最後の読み取り以降に、1 つまたは複数の更新チェック値が更新されている。  
  
 この競合を解決するためには、オブジェクトのどのメンバーが競合しているかを判別し、どのように対処するかを決定することが必要です。  
  
> [!NOTE]
>  オプティミスティック同時実行のチェックに関与するのは、<xref:System.Data.Linq.Mapping.UpdateCheck> または <xref:System.Data.Linq.Mapping.UpdateCheck> として割り当てられているメンバーのみです。  <xref:System.Data.Linq.Mapping.UpdateCheck> と指定されているメンバーには、チェックは実行されません。  詳細については、「<xref:System.Data.Linq.Mapping.UpdateCheck>」を参照してください。  
  
## 例  
 次のシナリオは、ユーザー 1 が、更新の手始めとして、データベースの行をクエリした状況です。  ユーザー 1 が取得した行には、Alfreds、Maria、および Sales という値が入っています。  
  
 ユーザー 1 は、Manager 列の値を Alfred に、また Department 列の値を Marketing に、それぞれ変更しようと考えています。  しかし、ユーザー 1 がその変更を発行する前に、ユーザー 2 がデータベースに変更を送信しました。  その結果、Assistant 列の値は Mary に、また Department 列の値は Service に、それぞれ変更されました。  
  
 ここで、ユーザー 1 が変更を送信しようとすると、送信は失敗し、<xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。  このような結果になるのは、データベースの Assistant 列と Department 列の値が、予期した値と異なるためです。  Assistant 列と Department 列を表すメンバーが競合しています。  この状況をまとめると次の表のようになります。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|元の状態|Alfreds|Maria|Sales|  
|ユーザー 1|Alfred||Marketing|  
|ユーザー 2||Mary|サービス|  
  
 このような競合は、いくつかの方法で解決できます。  詳細については、「[How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)」を参照してください。  
  
## 競合の検出と解決のチェック リスト  
 競合の検出と解決は、さまざまな詳細レベルで行うことができます。  極端な方法としては、すべての競合を 3 つの方法 \(<xref:System.Data.Linq.RefreshMode> を参照\) のいずれかで 1 つで解決し、それ以外の考慮を一切加えないという方法もあります。  正反対の方法としては、競合している各メンバーについて、それぞれの競合の種類ごとに、特定の処理を指定するという方法もあります。  
  
-   オブジェクト モデルの <xref:System.Data.Linq.Mapping.UpdateCheck> オプションを指定または変更します。  
  
     詳細については、「[How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)」を参照してください。  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出しの try\/catch ブロックで、例外がどの時点でスローされるかを指定します。  
  
     詳細については、「[How to: Specify When Concurrency Exceptions are Thrown](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)」を参照してください。  
  
-   取得する競合の詳細さを判断し、それに応じたコードを try\/catch ブロックに記述します。  
  
     詳細については、「[How to: Retrieve Entity Conflict Information](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)」および「[How to: Retrieve Member Conflict Information](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)」を参照してください。  
  
-   `try`\/`catch` コードで、発見されたさまざまな競合を解決する方法を指定します。  
  
     詳細については、「[How to: Resolve Conflicts by Retaining Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)」、「[How to: Resolve Conflicts by Overwriting Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)」、および「[How to: Resolve Conflicts by Merging with Database Values](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)」を参照してください。  
  
## 競合の発見と解決をサポートする LINQ to SQL の型  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で、オプティミスティック同時実行の競合の解決をサポートするクラスと機能を以下に示します。  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=fullName>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=fullName>  
  
## 参照  
 [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)