---
title: "パフォーマンスに関する考慮事項 (Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# パフォーマンスに関する考慮事項 (Entity Framework)
このトピックでは、ADO.NET Entity Framework のパフォーマンス特性を示し、Entity Framework アプリケーションのパフォーマンスを向上させるために役立つ注意事項について説明します。  
  
## クエリ実行の段階  
 Entity Framework でのクエリのパフォーマンスをより深く理解するには、概念モデルに対して実行されたクエリがデータをオブジェクトとして返す際の動作を知る必要があります。  この一連の動作を次の表に示します。  
  
|操作|相対コスト|頻度|コメント|  
|--------|-----------|--------|----------|  
|メタデータの読み込み|中|各アプリケーション ドメイン内で 1 回|Entity Framework が使用するモデルとマッピングのメタデータが、<xref:System.Data.Metadata.Edm.MetadataWorkspace> に読み込まれます。  このメタデータはグローバルにキャッシュされ、同じアプリケーション ドメイン内にある <xref:System.Data.Objects.ObjectContext> の他のインスタンスも使用できるようになります。|  
|データベース接続を開く|中<sup>1</sup>|必要時|データベースへの接続では貴重なリソースが消費されるので、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は必要な場合のみデータベース接続の開閉を行います。  接続は、明示的に開くこともできます。  詳細については、「[Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)」を参照してください。|  
|ビューの生成|High|各アプリケーション ドメイン内で 1 回  \(事前生成可能\)|Entity Framework が、概念モデルに対してクエリを実行したり変更内容をデータ ソースに保存したりできるようになるには、データベースにアクセスするためのローカル クエリ ビューのセットを事前に生成しておく必要があります。  このビューを生成する際のコストは高いため、設計時にビューを事前に作成してプロジェクトに追加しておくことができます。  詳細については、「[How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/ja-jp/b18a9d16-e10b-4043-ba91-b632f85a2579)」を参照してください。|  
|クエリの準備|中<sup>2</sup>|各一意のクエリに対して 1 回|クエリ コマンドを作成したり、モデルとマッピングのメタデータに基づいてコマンド ツリーを生成したり、返されるデータの形状を定義したりするためのコストが含まれます。  Entity SQL と LINQ の両方のクエリ コマンドがキャッシュされるため、同じクエリであれば、後続の実行は短時間で済みます。  後続の実行でさらにコストを削減するためにコンパイル済み LINQ クエリを使用でき、コンパイル済みクエリが自動的にキャッシュされる LINQ クエリよりも効率的である場合があります。  詳細については、「[コンパイル済みクエリ \(LINQ to Entities\)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)」を参照してください。  LINQ クエリの実行に関する一般的な情報については、「[LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。 **Note:**  メモリ内コレクションへ `Enumerable.Contains` 演算子を追加する LINQ to Entities クエリは自動的にキャッシュされません。  またコンパイル済み LINQ クエリのメモリ内コレクションをパラメーターで表すことは許可されていません。|  
|クエリの実行|低<sup>2</sup>|各クエリに対して 1 回|ADO.NET データ プロバイダーを使用してデータ ソースに対してコマンドを実行するコスト。  大半のデータ ソースではクエリ プランがキャッシュされるため、同じクエリであれば、後続の実行は短時間で済むことがあります。|  
|型の読み込みと検証|低<sup>3</sup>|各 <xref:System.Data.Objects.ObjectContext> インスタンスに対して 1 回|型が読み込まれ、概念モデルが定義する型に照らし合わせて検証されます。|  
|追跡|低<sup>3</sup>|クエリが返す各オブジェクトに対して 1 回  <sup>4</sup>|クエリが <xref:System.Data.Objects.MergeOption> のマージ オプションを使用する場合には、この段階でパフォーマンスが低下することはありません。<br /><br /> クエリが <xref:System.Data.Objects.MergeOption>、<xref:System.Data.Objects.MergeOption>、または <xref:System.Data.Objects.MergeOption> のいずれかのマージ オプションを使用する場合には、クエリ結果が <xref:System.Data.Objects.ObjectStateManager> で追跡されます。  クエリが返す追跡対象の各オブジェクトに対して <xref:System.Data.EntityKey> が生成され、<xref:System.Data.Objects.ObjectStateManager> に <xref:System.Data.Objects.ObjectStateEntry> を作成するために使用されます。  <xref:System.Data.EntityKey> に対応する既存の <xref:System.Data.Objects.ObjectStateEntry> がある場合には、既存のオブジェクトが返されます。  <xref:System.Data.Objects.MergeOption> または <xref:System.Data.Objects.MergeOption> オプションが指定されている場合、オブジェクトは更新後に返されます。<br /><br /> 詳細については、「[Identity Resolution, State Management, and Change Tracking](http://msdn.microsoft.com/ja-jp/3bd49311-0e72-4ea4-8355-38fe57036ba0)」を参照してください。|  
|オブジェクトの具体化|中<sup>3</sup>|クエリが返す各オブジェクトに対して 1 回  <sup>4</sup>|返された <xref:System.Data.Common.DbDataReader> オブジェクトを読み取ったり、オブジェクトを作成してプロパティ値を設定したりするプロセス。プロパティ値は、<xref:System.Data.Common.DbDataRecord> クラスの各インスタンスの値に基づきます。  オブジェクトが <xref:System.Data.Objects.ObjectContext> に既に存在しており、クエリに <xref:System.Data.Objects.MergeOption> または <xref:System.Data.Objects.MergeOption> マージ オプションが指定されている場合、この段階でパフォーマンスを低下することはありません。  詳細については、「[Identity Resolution, State Management, and Change Tracking](http://msdn.microsoft.com/ja-jp/3bd49311-0e72-4ea4-8355-38fe57036ba0)」を参照してください。|  
  
 <sup>1</sup> データ ソース プロバイダーが接続プールを実装している場合、接続を開くコストはプール全体に配分されます。  .NET Provider for SQL Server は、接続プールをサポートしています。  
  
 <sup>2</sup> クエリの複雑さが増すにつれて、コストも増大します。  
  
 <sup>3</sup> 総コストは、クエリによって返されるオブジェクトの数に比例して増大します。  
  
 <sup>4</sup> このオーバーヘッドは、EntityClient クエリでは必須ではありません。これは、EntityClient クエリはオブジェクトではなく <xref:System.Data.EntityClient.EntityDataReader> を返すからです。  詳細については、「[Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)」を参照してください。  
  
## その他の考慮事項  
 Entity Framework アプリケーションのパフォーマンスを低下させる可能性があるその他の考慮事項を次に示します。  
  
### クエリの実行  
 クエリがリソースを大量に消費することがあるので、コード内のどの個所で、またどのコンピューター上でクエリを実行するのかを検討してください。  
  
#### 遅延実行と即時実行  
 <xref:System.Data.Objects.ObjectQuery%601> クエリまたは LINQ クエリを作成しても、すぐには実行されないことがあります。  クエリの実行は、結果が必要になるまで遅延されます。たとえば、`foreach` \(C\#\) または `For Each` \(Visual Basic\) の列挙時や、<xref:System.Collections.Generic.List%601> コレクションに割り当てられた場合などです。  クエリがすぐに実行されるのは、<xref:System.Data.Objects.ObjectQuery%601> 上で <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> メソッドが呼び出されたときや、単一クエリを返す LINQ メソッド \(<xref:System.Linq.Enumerable.First%2A> や <xref:System.Linq.Enumerable.Any%2A> など\) が呼び出されたときです。  詳細については、「[Object Queries](http://msdn.microsoft.com/ja-jp/0768033c-876f-471d-85d5-264884349276)」および「[クエリの実行 \(LINQ to Entities\)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)」を参照してください。  
  
#### クライアント側での LINQ クエリの実行  
 LINQ クエリの実行は、データ ソースをホストするコンピューター上で行われますが、LINQ クエリは部分的にクライアント コンピューター上で評価されることがあります。  詳細については、「[クエリの実行 \(LINQ to Entities\)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)」の「ストア実行」の項を参照してください。  
  
### クエリとマッピングの複雑さ  
 個々のクエリの複雑さおよびエンティティ モデルのマッピングの複雑さは、クエリ パフォーマンスに大きな影響を及ぼします。  
  
#### マッピングの複雑さ  
 概念モデルのエンティティとストレージ モデルのテーブルとの間で、単純な一対一より複雑なマッピングのモデルは、一対一マッピングのモデルより複雑なコマンドを生成します。  
  
#### クエリの複雑さ  
 データソースに対して実行されるコマンド内に多数の結合を必要とするクエリや、データを大量に返すクエリは、次のようにパフォーマンスを低下させることがあります。  
  
-   単純に見える概念モデルに対してクエリを実行したところ、より複雑なクエリをデータ ソースに対して実行する結果になることがあります。  これは、Entity Framework が、概念モデルに対するクエリをデータ ソースに対する等価のクエリに変換するからです。  概念モデルの 1 つのエンティティ セットが、データ ソースの複数のテーブルにマップされている場合や、エンティティ間のリレーションシップが結合テーブルにマップされている場合には、データ ソース クエリに対して実行されるクエリ コマンドで 1 つ以上の結合が必要になる場合があります。  
  
    > [!NOTE]
    >  所定のクエリでデータ ソースに対して実行されるコマンドを表示するには、<xref:System.Data.Objects.ObjectQuery%601> クラスまたは <xref:System.Data.EntityClient.EntityCommand> クラスの <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> メソッドを使用します。  詳細については、「[How to: View the Store Commands](http://msdn.microsoft.com/ja-jp/f9771c6e-3b62-4b24-a5d4-55d68e14fa79)」を参照してください。  
  
-   Entity SQL クエリが入れ子になっていると、サーバー上で結合が作成され、その結果多数の行が返されることがあります。  
  
     projection 句内の入れ子になったクエリの例を次に示します。  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     さらに、このようなクエリでは、入れ子になったクエリ全体でオブジェクトを複製する単一クエリがクエリ パイプラインで生成されます。  そのため、1 つの列が複数回複製されることがあります。  SQL Server など、一部のデータベースでは、これによって TempDB テーブルのサイズが非常に大きくなり、サーバーのパフォーマンスに悪影響を及ぼす場合があります。  入れ子になったクエリを実行するときには、注意を払う必要があります。  
  
-   クライアントが、結果セットのサイズに比例してリソースを消費するような操作を実行している場合、データを大量に返すクエリを実行すると、パフォーマンスが低下することがあります。  このような場合には、クエリによって返されるデータの量を制限することを検討してください。  詳細については、「[How to: Page Through Query Results](http://msdn.microsoft.com/ja-jp/ffc0f920-e7de-42e0-9b12-ef356421d030)」を参照してください。  
  
 Entity Framework によって自動的に生成されるコマンドは、データベース開発者が明示的に記述した同様のコマンドより複雑になることがあります。  データ ソースに対して実行されるコマンドを明示的に制御する必要がある場合には、テーブル値関数またはストアド プロシージャへのマッピングを定義することを検討してください。  
  
#### 関係  
 クエリのパフォーマンスを最適化するには、エンティティ間のリレーションシップをエンティティ モデル内のアソシエーションとしてだけでなく、データ ソース内の論理リレーションシップとしても定義する必要があります。  
  
### クエリ パス  
 既定では、<xref:System.Data.Objects.ObjectQuery%601> を実行しても、関連オブジェクトは返されません \(リレーションシップ自体を表現するオブジェクトが存在する場合でも\)。  関連オブジェクトは、次の 3 つの方法のいずれかで読み込むことができます。  
  
1.  <xref:System.Data.Objects.ObjectQuery%601> が実行される前にクエリ パスを設定します。  
  
2.  オブジェクトが公開するナビゲーション プロパティに対して `Load` メソッドを呼び出します。  
  
3.  <xref:System.Data.Objects.ObjectContext> で <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> オプションを `true` に設定します。  [Entity Data Model Designer](http://msdn.microsoft.com/ja-jp/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf) を使用してオブジェクトレイヤー コードを生成すると、自動的に行われます。  詳細については、「[Generated Code Overview](http://msdn.microsoft.com/ja-jp/6a88ea38-6a90-4107-bc33-531b79ce5b6a)」を参照してください。  
  
 使用するオプションを検討する際には、データベースに対する要求数と 1 つのクエリで返されるデータ量の間でのトレードオフに注意してください。  詳細については、「[Loading Related Objects](http://msdn.microsoft.com/ja-jp/452347d2-7b3b-44cd-9001-231299a28cb1)」を参照してください。  
  
#### クエリ パスの使用  
 クエリ パスは、クエリによって返されるオブジェクトのグラフを定義します。  クエリ パスを定義する場合、データベースに対する 1 件の要求だけで、パスによって定義されたすべてのオブジェクトが返されます。  クエリ パスを使用すると、見かけ上は簡単なオブジェクト クエリのデータ ソースに対して複雑なコマンドが実行される可能性があります。  これは、1 つのクエリ内の関連オブジェクトを返すには、1 つまたは複数の結合が必要になるために発生します。  継承のあるエンティティや多対多のリレーションシップを含んだパスなど、複雑なエンティティ モデルに対してクエリを実行する場合は、さらに複雑になります。  
  
> [!NOTE]
>  <xref:System.Data.Objects.ObjectQuery%601> によって生成されるコマンドを表示するには、<xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> メソッドを使用します。  詳細については、「[How to: View the Store Commands](http://msdn.microsoft.com/ja-jp/f9771c6e-3b62-4b24-a5d4-55d68e14fa79)」を参照してください。  
  
 クエリ パスに含まれる関連オブジェクトが多すぎる場合や、オブジェクトに含まれる行データが多すぎる場合、データ ソースはクエリを完了できないことがあります。  これは、クエリでデータ ソースの機能を超える中間一時ストレージが必要になる場合に発生します。  この場合は、関連オブジェクトを明示的に読み込むと、データ ソース クエリの複雑さを軽減できます。  
  
#### 関連オブジェクトの明示的な読み込み  
 <xref:System.Data.Objects.DataClasses.EntityCollection%601> または <xref:System.Data.Objects.DataClasses.EntityReference%601> を返すナビゲーション プロパティ上で `Load` メソッドを呼び出すことによって、関連オブジェクトを明示的に読み込むことができます。  オブジェクトを明示的に読み込むには、`Load` を呼び出すたびにデータベースへのラウンドトリップが必要になります。  
  
> [!NOTE]
>  `foreach` ステートメント \(Visual Basic では `For Each`\) を使用するときなど、返されたオブジェクトのコレクションをループ処理しながら、`Load` を呼び出す場合、データ ソース固有のプロバイダーは 1 つの接続で複数のアクティブな結果セットをサポートする必要があります。  SQL Server データベースの場合、プロバイダー接続文字列に `MultipleActiveResultSets = true` の値を指定する必要があります。  
  
 エンティティに <xref:System.Data.Objects.DataClasses.EntityCollection%601> プロパティまたは <xref:System.Data.Objects.DataClasses.EntityReference%601> プロパティがない場合は、<xref:System.Data.Objects.ObjectContext.LoadProperty%2A> メソッドを使用することもできます。  これは、POCO エンティティを使用している場合に有効です。  
  
 関連オブジェクトを明示的に読み込むと、結合の数と冗長データの量が減少しますが、`Load` にはデータベースへの接続が繰り返し必要になります。多数のオブジェクトを明示的に読み込む場合には、高コストになることがあります。  
  
### 変更の保存  
 <xref:System.Data.Objects.ObjectContext> 上で <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> メソッドを呼び出すと、コンテキスト内で追加、更新、または削除された各オブジェクトに対して独立した作成、更新、または削除のコマンドが生成されます。  このコマンドは、1 つのトランザクションのデータ ソースで実行されます。  クエリの場合と同様に、作成、更新、および削除の操作は、概念モデルのマッピングの複雑さに依存します。  
  
### 分散トランザクション  
 明示的トランザクションでの操作で、分散トランザクション コーディネーター \(DTC: Distributed Transaction Coordinator\) によって管理されるリソースが必要とされることがありますが、このような操作は DTC を必要としない同様の操作より高コストになります。  DTC への昇格は、次の状況で発生します。  
  
-   明示的トランザクションを常に DTC に昇格する SQL Server 2000 データベースやその他のデータ ソースに対して、明示的トランザクションで操作を実行する場合。  
  
-   SQL Server 2005 に対して明示的トランザクションで操作を実行し、かつ接続が [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によって管理される場合。  これは、接続が閉じられてから同じトランザクション内で再度開かれると、SQL Server 2005 が DTC に必ず昇格するためです。この動作は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] の既定の動作です。  この DTC 昇格は、SQL Server 2008 使用時には生じません。SQL Server 2005 使用時にこの昇格を回避するには、明示的にトランザクション内で接続を開いたり閉じたりする必要があります。  詳細については、「[Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)」を参照してください。  
  
 明示的トランザクションが使用されるのは、1 つの <xref:System.Transactions> トランザクション内で操作を 1 つ以上実行するときです。  詳細については、「[Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)」を参照してください。  
  
## パフォーマンスを向上させるための戦略  
 次の戦略を使用すると、Entity Framework でのクエリの全体的なパフォーマンスを向上させることができます。  
  
#### ビューの事前生成  
 アプリケーションがクエリを初めて実行する際、エンティティ モデルに基づいたビュー生成は高コストになります。  EdmGen.exe ユーティリティを使用して、プロジェクトに追加できる Visual Basic または C\# のコード ファイルとして設計時に事前にビューを生成しておきます。  テキスト テンプレート変換ツールキットを使用して、事前にコンパイルされたビューを生成することもできます。  事前に生成したビューは、現在のバージョンの指定エンティティ モデルに対応することを確認するために、実行時に検証されます。  詳細については、「[How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/ja-jp/b18a9d16-e10b-4043-ba91-b632f85a2579)」および「[Entity Framework 4 のプリコンパイルまたは事前生成されたビューとパフォーマンスを分離する](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409)」を参照してください。  
  
 サイズが非常に大きいモデルで作業する場合は、次の点に注意してください。  
  
 .NET メタデータ形式では、特定のバイナリ内のユーザー文字列の数が 16,777,215 \(0xFFFFFF\) に制限されます。  サイズが非常に大きいモデルのビューを生成中に、ビュー ファイルがこのサイズ制限に達した場合、"ユーザー文字列を作成する論理スペースがありません。" というコンパイル エラーが表示されます。  このサイズ制限は、すべてのマネージ バイナリに適用されます。  詳細については、[ブログ](http://go.microsoft.com/fwlink/?LinkId=201476)を参照してください。ブログでは、大型の複雑なモデルでの操作時のエラーを回避する方法について説明しています。  
  
#### クエリの NoTracking マージ オプションの使用を検討する  
 オブジェクト コンテキスト内で返されたオブジェクトを追跡するにはコストが生じます。  オブジェクトに対する変更内容を検出したり、同じ論理エンティティに対する複数の要求で同じオブジェクト インスタンスが返されるようにするには、オブジェクトを <xref:System.Data.Objects.ObjectContext> インスタンスにアタッチする必要があります。  オブジェクトの更新または削除を行う予定がなく、ID 管理が不要である場合には、クエリ実行時に <xref:System.Data.Objects.MergeOption> マージ オプションを使用することを検討してください。  
  
#### 適量のデータを返す  
 シナリオによっては、<xref:System.Data.Objects.ObjectQuery%601.Include%2A> メソッドを使用してクエリ パスを指定する方がはるかに速いことがあります。データベースに対する必要なラウンド トリップ数が減るからです。  ただし、他のシナリオでは、関連オブジェクトを読み込むためにデータベースへのラウンド トリップを増やす方が速くなることがあります。これは、クエリが単純で結合数が少ないほど、データの冗長性が低下するからです。  したがって、関連オブジェクトを取得するためのさまざまな方法について、パフォーマンスをテストすることをお勧めします。  詳細については、「[Loading Related Objects](http://msdn.microsoft.com/ja-jp/452347d2-7b3b-44cd-9001-231299a28cb1)」を参照してください。  
  
 1 つのクエリで大量のデータが返されることを回避するには、クエリの結果を扱いやすいサイズのグループに分割してページングすることを検討してください。  詳細については、「[How to: Page Through Query Results](http://msdn.microsoft.com/ja-jp/ffc0f920-e7de-42e0-9b12-ef356421d030)」を参照してください。  
  
#### ObjectContext のスコープを制限する  
 通常は、`using` ステートメント \(Visual Basic では `Using End Using`\) 内に <xref:System.Data.Objects.ObjectContext> インスタンスを作成する必要があります。  これにより、パフォーマンスが向上します。これは、コードがステートメント ブロックを終了するときに、オブジェクト コンテキストに関連付けられたリソースが自動的に廃棄されるからです。  ただし、オブジェクト コンテキストによって管理されるオブジェクトにコントロールがバインドされている場合、バインドが必要とされる間は <xref:System.Data.Objects.ObjectContext> インスタンスを保持し、手動で廃棄する必要があります。  詳細については、「[Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)」を参照してください。  
  
#### データベース接続を手動で開くことを検討する  
 アプリケーションで、一連のオブジェクト クエリを実行する場合、またはデータ ソースに対する作成、更新、および削除操作を持続するために <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> を頻繁に呼び出す場合、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はデータ ソースに対する接続を連続的に開閉する必要があります。  このような状況では、操作の開始時に接続を手動で開いて、操作の完了時に接続を手動で閉じるか廃棄することを検討してください。  詳細については、「[Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)」を参照してください。  
  
## パフォーマンス データ  
 Entity Framework の一部のパフォーマンス データは、[ADO.NET チーム ブログ](http://go.microsoft.com/fwlink/?LinkId=91905) の次のブログ記事に公開されています。  
  
-   [ADO.NET Entity Framework のパフォーマンスを探索する \- パート 1](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [ADO.NET Entity Framework のパフォーマンスを探索する \- パート 2](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [ADO.NET Entity Framework パフォーマンスの比較](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## 参照  
 [開発および配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)