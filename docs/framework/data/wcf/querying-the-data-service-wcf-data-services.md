---
title: "データ サービスのクエリ (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, データへのアクセス"
  - "WCF Data Services, クライアント ライブラリ"
  - "WCF Data Services, 照会"
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# データ サービスのクエリ (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用すると、言語統合クエリ \(LINQ\) を含め、使い慣れた [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] プログラミング パターンを使用してデータ サービスに対してクエリを実行できます。  このクライアント ライブラリは、クライアント上で <xref:System.Data.Services.Client.DataServiceQuery%601> クラスのインスタンスとして定義されたクエリを HTTP GET 要求メッセージに変換します。  さらに応答メッセージを受け取り、クライアント データ サービス クラスのインスタンスに変換します。  これらのクラスは、<xref:System.Data.Services.Client.DataServiceQuery%601> が属する <xref:System.Data.Services.Client.DataServiceContext> によって追跡されます。  
  
## データ サービス クエリ  
 <xref:System.Data.Services.Client.DataServiceQuery%601> ジェネリック クラスは、0 個以上のエンティティ型インスタンスのコレクションを返すクエリを表します。  データ サービス クエリは、常に既存のデータ サービス コンテキストに属します。  このコンテキストにより、クエリの作成と実行に必要なサービス URI とメタデータ情報が維持されます。  
  
 **\[サービス参照の追加\]** ダイアログを使用してデータ サービスを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ベースのクライアント アプリケーションに追加すると、<xref:System.Data.Services.Client.DataServiceContext> クラスを継承するエンティティ コンテナー クラスが作成されます。  このクラスには、型指定された <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスを返すプロパティが含まれます。  データ サービスが公開するエンティティ セットごとに 1 つのプロパティがあります。  これらのプロパティを使用すると、型指定された <xref:System.Data.Services.Client.DataServiceQuery%601> のインスタンスを簡単に作成できます。  
  
 クエリは次のシナリオで実行されます。  
  
-   次のように結果が暗黙的に列挙される場合  
  
    -   `foreach` \(C\#\) ループや `For Each` \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\) ループなどで、エンティティ セットを表す <xref:System.Data.Services.Client.DataServiceContext> のプロパティが列挙されているとき  
  
    -   `List` コレクションにクエリが割り当てられているとき  
  
-   <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> メソッドまたは <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> メソッドが明示的に呼び出されたとき  
  
-   <xref:System.Linq.Enumerable.First%2A> や <xref:System.Linq.Enumerable.Single%2A> などの LINQ クエリ実行演算子が呼び出されたとき。  
  
 次のクエリを実行すると、Northwind データ サービスのすべての `Customers` エンティティが返されます。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 詳細については、「[方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントでは遅延バインディング オブジェクトに対するクエリがサポートされていますが \(C\# で*動的*型を使用する場合など\)、  パフォーマンス上の理由から、データ サービスに対しては常に厳密に型指定されたクエリを作成するようにしてください。  <xref:System.Tuple> 型と動的オブジェクトはクライアントでサポートされていません。  
  
## LINQ クエリ  
 <xref:System.Data.Services.Client.DataServiceQuery%601> クラスは LINQ で定義された <xref:System.Linq.IQueryable%601> インターフェイスを実装するので、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリは、エンティティ セット データに対する LINQ クエリを、データ サービス リソースに対して評価されるクエリ式を表す URI に変換できます。  次の例は、前述の <xref:System.Data.Services.Client.DataServiceQuery%601> と同じ LINQ クエリです。ここでは、輸送費が 30 ドルを超える `Orders` を取得し、その結果を輸送費順に並べ替えます。  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 この LINQ クエリは、Northwind ベースの[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) データ サービスに対して実行される次のクエリ URI に変換されます。  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  LINQ 構文で表現できるクエリのセットは、データ サービスによって使用される REST \(Representational State Transfer\) ベースの URI 構文で有効なクエリのセットよりも範囲が広くなります。  クエリを対象データ サービスの URI にマップできない場合、<xref:System.NotSupportedException> が発生します。  
  
 詳細については、「[LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)」を参照してください。  
  
## クエリ オプションの追加  
 データ サービス クエリは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で提供されるすべてのクエリ オプションをサポートしています。  <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを呼び出して、クエリ オプションを <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスに追加します。  <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> は、新しい <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスを返します。このインスタンスは元のクエリと同等ですが、新しいクエリ オプション セットを含みます。  次のクエリを実行すると、`Freight` 値でフィルターされ、`OrderID` によって降順に並べ替えられた `Orders` が返されます。  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 `$orderby` クエリ オプションを使用すると、単一のプロパティに基づくクエリの並べ替えとフィルターの両方が可能です。次の例では、フィルターし、返された `Orders` オブジェクトを `Freight` プロパティの値に基づき並べ替えます。  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを連続して呼び出すと、複雑なクエリ式を作成できます。  詳細については、「[方法: データ サービス クエリにクエリ オプションを追加する](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)」を参照してください。  
  
 クエリ オプションを使用して、LINQ クエリの構文要素を表すことができます。  詳細については、「[LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用してクエリ URI に `$select` クエリ オプションを追加することはできません。  LINQ の <xref:System.Linq.Enumerable.Select%2A> メソッドを使用して、クライアントによって要求 URI に `$select` クエリ オプションが生成されるようにすることをお勧めします。  
  
<a name="executingQueries"></a>   
## クライアントでの実行とサーバーでの実行  
 クライアントによるクエリの実行は 2 つの部分に分かれています。  可能な限り、クエリ内の式は最初にクライアントで評価されます。その後、URI ベースのクエリが生成され、データ サービスに送信されて、サービス内のデータに対して評価されます。  次の LINQ クエリについて考えてみましょう。  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 この例では、式 `(basePrice – (basePrice * discount))` はクライアントで評価されます。  そのため、データ サービスに送信される実際のクエリ URI \(`http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)`\) のフィルター句に計算済みの 10 進値 `90` が含まれています。  部分文字列式を含むフィルター式のその他の部分は、データ サービスによって評価されます。  クライアントで評価される式は共通言語ランタイム \(CLR\) セマンティクスに従いますが、データ サービスに送信される式は [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのデータ サービスの実装に依存します。  また、このように別々に評価されることで予期しない結果が生じる場合があることにも注意する必要があります。たとえば、クライアントとサービスの両方で、異なるタイム ゾーンを使用して時間に基づく評価が実行される場合があります。  
  
## クエリ応答  
 <xref:System.Data.Services.Client.DataServiceQuery%601> を実行すると、要求したエンティティ型の <xref:System.Collections.Generic.IEnumerable%601> が返されます。  このクエリ結果は、次の例のように <xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトにキャストできます。  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 データ サービスのエンティティを表すエンティティ型インスタンスは、オブジェクトの具体化というプロセスによってクライアントで作成されます。  詳細については、「[オブジェクトの具体化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)」を参照してください。  <xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトは、<xref:System.Collections.Generic.IEnumerable%601> を実装してクエリ結果へのアクセスを提供します。  
  
 さらに、<xref:System.Data.Services.Client.QueryOperationResponse%601> には、クエリ結果に関する追加情報へのアクセスを可能にする次のメンバーが含まれます。  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> \- 発生すると、操作によってエラーがスローされます。  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> \- クエリ応答に関連する HTTP 応答ヘッダーのコレクションが含まれます。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> \- <xref:System.Data.Services.Client.QueryOperationResponse%601> を生成した元の <xref:System.Data.Services.Client.DataServiceQuery%601> を取得します。  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> \- クエリ応答の HTTP 応答コードを取得します。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> \- <xref:System.Data.Services.Client.DataServiceQuery%601> で <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> メソッドが呼び出されるとエンティティ セット内のエンティティの合計数を取得します。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> \- 結果の次のページの URI を含む <xref:System.Data.Services.Client.DataServiceQueryContinuation> オブジェクトを返します。  
  
 既定では、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] はクエリ URI によって明示的に選択されたデータのみを返します。  これにより、必要に応じてデータ サービスから追加のデータを明示的に読み込むことができます。  データ サービスからデータを明示的に読み込むたびに要求がデータ サービスに送られます。  明示的に読み込むことができるデータには、関連エンティティ、ページングされた応答データ、バイナリ データ ストリームがあります。  
  
> [!NOTE]
>  データ サービスはページングされた応答を返す場合があるので、アプリケーションではページングされたデータ サービス応答を処理するプログラミング パターンを使用することをお勧めします。  詳細については、「[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)」を参照してください。  
  
 エンティティの特定のプロパティのみが応答で返されるように指定することにより、クエリによって返されるデータの量を削減することもできます。  詳細については、「[クエリ射影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)」を参照してください。  
  
## セット内のエンティティの合計数の取得  
 一部のシナリオでは、クエリによって返される数だけではなく、エンティティ セット内のエンティティの合計数を知っておくと役立ちます。  このセット内のエンティティの合計数がクエリ結果に含まれるように要求するには、<xref:System.Data.Services.Client.DataServiceQuery%601> で <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> メソッドを呼び出します。  この場合、返された <xref:System.Data.Services.Client.QueryOperationResponse%601> の <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> プロパティが、セット内のエンティティの合計数を返します。  
  
 さらに、<xref:System.Linq.Enumerable.Count%2A> メソッドまたは <xref:System.Linq.Enumerable.LongCount%2A> メソッドを呼び出すことにより、それぞれ <xref:System.Int32> 値または <xref:System.Int64> 値として、セット内のエンティティの合計数のみを取得することもできます。  これらのメソッドを呼び出すと、<xref:System.Data.Services.Client.QueryOperationResponse%601> は返されず、カウント値のみが返されます。  詳細については、「[方法: クエリで返されたエンティティの数を確認する](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)」を参照してください。  
  
## このセクションの内容  
 [クエリ射影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [オブジェクトの具体化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [LINQ に関する留意点](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [方法: データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [方法: データ サービス クエリにクエリ オプションを追加する](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [方法: クエリで返されたエンティティの数を確認する](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [方法: データ サービス要求のクライアント資格情報を指定する](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [方法: クライアント要求のヘッダーを設定する](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [方法: クエリ結果を射影する](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)