---
title: "LINQ に関する留意点 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services、LINQ"
  - "クエリ (データ サービスに対する) [WCF Data Services]"
  - "WCF Data Services は、クエリを実行します。"
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# LINQ に関する留意点 (WCF Data Services)
このトピックでは、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントを使用しているときに LINQ クエリを作成および実行する方法と、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を実装するデータ サービスを LINQ で照会する場合の制限について説明します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]に対するクエリの実行を作成し、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのデータ サービスを参照してください[クエリ データ サービスに対する](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
## <a name="composing-linq-queries"></a>LINQ クエリの作成  
 LINQ を実装するオブジェクトのコレクションに対してクエリを作成できます。 <xref:System.Collections.Generic.IEnumerable%601>します。 両方、**サービス参照の追加** ダイアログ ボックスで[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]DataSvcUtil.exe ツールは、の形式の生成に使用されると、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]サービスから継承するエンティティ コンテナー クラスとして<xref:System.Data.Services.Client.DataServiceContext>、およびフィードで返されるエンティティを表すオブジェクトします。 これらのツールでは、サービスによってフィードとして公開されるコレクションに対応するエンティティ コンテナー クラスのプロパティも生成されます。 これらの各プロパティの戻り値のデータ サービスをカプセル化するクラス、 <xref:System.Data.Services.Client.DataServiceQuery%601>します。 <xref:System.Data.Services.Client.DataServiceQuery%601>クラスが実装する、 <xref:System.Linq.IQueryable%601> LINQ で定義されているインターフェイスは、クライアント ライブラリによってクエリ要求の実行時にデータ サービスに送信される URI に変換、データ サービスによって公開されるフィードに対する LINQ クエリを作成することができます。  
  
> [!IMPORTANT]
>  LINQ 構文で表現できるクエリのセットは、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] データ サービスによって使用される URI 構文で有効なクエリのセットよりも範囲が広くなります。 A <xref:System.NotSupportedException>クエリは、ターゲット データ サービスの URI にマップできない場合に発生します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][サポートされていない LINQ メソッド](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods)」を参照します。  
  
 次の例の LINQ クエリは、輸送費が&30; ドルを超える `Orders` を取得し、結果を出荷日の新しい順に並べ替えます。  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqSpecific)]  
  
 この LINQ クエリは次のクエリ、Northwind ベースに対して実行される URI に変換[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)データ サービス。  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 LINQ の概要については、次を参照してください。 [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)します。  
  
 LINQ を使用してクエリを作成する際には、前の例のような言語固有の宣言型のクエリ構文と、標準クエリ演算子と呼ばれる一連のクエリ メソッドの両方を使用できます。 したがって、次の例のように、前の例と同等のクエリをメソッド ベースの構文のみを使用して作成することもできます。  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqExpressionSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqExpressionSpecific)]  
  
 どちらの方法で作成したクエリも、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアントによってクエリ URI に変換されます。クエリ式にクエリ メソッドを追加して LINQ クエリを拡張することもできます。 クエリ式にメソッド構文を追加して LINQ クエリを作成した場合、または<xref:System.Data.Services.Client.DataServiceQuery%601>、操作をメソッドが呼び出される順序でのクエリ URI に追加します。 これは、呼び出すことと同じ、 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>というクエリ URI に各クエリ オプションを追加します。  
  
## <a name="executing-linq-queries"></a>LINQ クエリの実行  
 特定の LINQ などのメソッドのクエリ<xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>または<xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>、クエリに追加するときに、クエリを実行します。 クエリは、結果が暗黙的に列挙される場合 (`foreach` ループの間など) や、クエリが `List` コレクションに割り当てられている場合にも実行されます。 詳細については、次を参照してください。[クエリ データ サービスに対する](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
 クライアントによる LINQ クエリの実行は&2; つの部分に分かれています。 可能な限り、クエリ内の LINQ 式は最初にクライアントで評価されます。その後、URI ベースのクエリが生成され、データ サービスに送信されて、サービス内のデータに対して評価されます。 詳細については、セクションを参照してください。[クライアントとサーバーでの実行](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries)で[クエリ データ サービスに対する](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 準拠のクエリ URI で LINQ クエリを変換できない場合は、クエリを実行しようとすると例外が発生します。 詳細については、次を参照してください。[クエリ データ サービスに対する](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
## <a name="linq-query-examples"></a>LINQ クエリの例  
 以下のセクションの各例は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに対して実行できる LINQ クエリの種類を示しています。  
  
<a name="filtering"></a>   
### <a name="filtering"></a>フィルター処理  
 このセクションの LINQ クエリは、サービスによって返されるフィード内のデータをフィルター処理します。  
  
 以下の各例は、返された `Orders` エンティティをフィルター処理して、輸送費が&30; ドルを超える注文のみが返されるようにする同等のクエリを示しています。  
  
-   LINQ クエリ構文を使用する場合:  
  
      [Astoria NorthwindClient #LinqWhereClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereClauseSpecific)]  
  
-   LINQ クエリ メソッドを使用する場合:  
  
      [Astoria NorthwindClient #LinqWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereMethodSpecific)]  
  
-   URI クエリ文字列オプション `$filter`:  
  
      [Astoria NorthwindClient #ExplicitQueryWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryWhereMethodSpecific)]  
  
 上の例はすべて、`http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M` というクエリ URI に変換されます。  
  
<a name="sorting"></a>   
### <a name="sorting"></a>並べ替え  
 以下の各例は、返されたデータを会社名と郵便番号の降順で並べ替える同等のクエリを示しています。  
  
-   LINQ クエリ構文を使用する場合:  
  
      [Astoria NorthwindClient #LinqOrderByClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByClauseSpecific)]  
  
-   LINQ クエリ メソッドを使用する場合:  
  
      [Astoria NorthwindClient #LinqOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByMethodSpecific)]  
  
-   URI クエリ文字列オプション `$orderby`:  
  
      [Astoria NorthwindClient #ExplicitQueryOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryOrderByMethodSpecific)]  
  
 上の例はすべて、`http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc` というクエリ URI に変換されます。  
  
<a name="projection"></a>   
### <a name="projection"></a>射影  
 以下の各例は、返されたデータをより範囲の狭い `CustomerAddress` 型に射影する同等のクエリを示しています。  
  
-   LINQ クエリ構文を使用する場合:  
  
      [Astoria NorthwindClient #LinqSelectClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectClauseSpecific)]  
  
-   LINQ クエリ メソッドを使用する場合:  
  
      [Astoria NorthwindClient #LinqSelectMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectMethodSpecific)]  
  
> [!NOTE]
>  `$select`クエリ オプションを使用してクエリ URI に追加できません、 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>メソッドです。 LINQ を使用することをお勧め<xref:System.Linq.Enumerable.Select%2A>クライアントを生成するメソッド、`$select`クエリ要求 URI 内のオプション\</TSource, TResult>。  
  
 上の例はいずれも、`"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"` というクエリ URI に変換されます。  
  
<a name="paging"></a>   
### <a name="client-paging"></a>クライアントのページング  
 以下の各例は、25 件の注文を含む並べ替え済みの注文エンティティのページを、最初の 50 件の注文をスキップして要求する同等のクエリを示しています。  
  
-   LINQ クエリにクエリ メソッドを適用する場合:  
  
      [Astoria NorthwindClient #LinqSkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSkipTakeMethodSpecific)]  
  
-   URI クエリ文字列オプション `$skip` および `$top`:  
  
      [Astoria NorthwindClient #ExplicitQuerySkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQuerySkipTakeMethodSpecific)]  
  
 上の例はいずれも、`http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25` というクエリ URI に変換されます。  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] データ サービスを照会するときに、返されるフィードにクエリの対象のエンティティに関連するエンティティを含めるように要求することができます。 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>メソッドが、 <xref:System.Data.Services.Client.DataServiceQuery%601> LINQ クエリの対象となるエンティティ セットの関連するエンティティ セットの名前として、`path`パラメーター。 詳細については、次を参照してください。[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)します。  
  
 次の例は、使用する同等の方法を示して、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>クエリ内のメソッド。  
  
-   LINQ クエリ構文の場合:  
  
      [Astoria NorthwindClient #LinqQueryExpandSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandSpecific)]  
  
-   LINQ クエリ メソッドの場合:  
  
      [Astoria NorthwindClient #LinqQueryExpandMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandMethodSpecific)]  
  
 上の例はいずれも、`http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details` というクエリ URI に変換されます。  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>サポートされていない LINQ メソッド  
 次の表に含まれている LINQ メソッドはサポートされていません。[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスに対して実行されるクエリにこれらのメソッドを含めることはできません。  
  
|演算の種類|サポートされていないメソッド|  
|--------------------|------------------------|  
|集合演算子|すべての集合演算子はに対してサポートされている、 <xref:System.Data.Services.Client.DataServiceQuery%601>、次が含まれています。<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>\</TFirst, TSecond, TResult>|  
|順序付け演算子|次の順序付け演算子を必要とする<xref:System.Collections.Generic.IComparer%601>に対してサポートされていない、 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey>|  
|プロジェクション演算子とフィルター演算子|以下のプロジェクションと位置の引数を受け入れるフィルターの演算子がに対してサポートされていない、 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29> </TOuter, TInner, TResult> </TInner, TKey> </TOuter, TKey> </TOuter, TInner, TKey, TResult><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29> </TSource, Int32, TResult> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> \</TSource, TCollection, TResult> \</TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> </TSource, TCollection, TResult> </TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29> \</TSource, Int32, Boolean>|  
|グループ化演算子|に対するすべてのグループ化演算子がサポートされていない、 <xref:System.Data.Services.Client.DataServiceQuery%601>、次を含みます。<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A>\</TSource, TKey><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A>\</TOuter, TInner, TKey, TResult><br /><br /> グループ化の操作はクライアント側で実行する必要があります。|  
|集計演算子|に対するすべての集計演算子がサポートされていない、 <xref:System.Data.Services.Client.DataServiceQuery%601>、次を含みます。<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> 集計操作は、クライアント側で実行するか、サービス操作でカプセル化する必要があります。|  
|ページング演算子|に対して以下のページング演算子はサポートされていません、 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **注:** null、空のシーケンスで実行されるページング演算子を返します。|  
|その他の演算子|次に対して他の演算子がサポートされていない、 <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.<xref:System.Linq.Enumerable.Empty%2A><br />2.<xref:System.Linq.Enumerable.Range%2A><br />3.<xref:System.Linq.Enumerable.Repeat%2A><br />4.<xref:System.Linq.Enumerable.ToDictionary%2A></TSource, TKey><br />5.<xref:System.Linq.Enumerable.ToLookup%2A>\</TSource, TKey>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>サポートされている式の関数  
 共通言語ランタイム (CLR) の以下のメソッドおよびプロパティは、クエリ式で変換して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスへの要求 URI に含めることができるため、サポートされています。  
  
|<xref:System.String>メンバー|サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime>メンバー<sup>1</sup>|サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>と等価な日付と時刻のプロパティの<xref:Microsoft.VisualBasic.DateAndTime?displayProperty=fullName>、だけでなく、 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Visual Basic のメソッドもサポートされています。  
  
|<xref:System.Math>メンバー|サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:> System.Linq.Expressions.Expression?qualifyHint=False&autoUpgrade=Trueメンバー|サポートされている [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 関数|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 クライアント側でその他の CLR 関数を評価できる場合もあります。 A <xref:System.NotSupportedException>がクライアントで評価できないし、サーバー上での評価の有効な要求 URI に変換できない式に対して発生します。  
  
## <a name="see-also"></a>関連項目  
 [データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [クエリ射影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)   
 [オブジェクトの具体化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)   
 [OData: URI 規則](http://go.microsoft.com/fwlink/?LinkID=185564)