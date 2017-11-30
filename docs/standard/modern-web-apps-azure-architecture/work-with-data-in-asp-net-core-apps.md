---
title: "ASP.NET Core アプリケーションのデータを操作します。"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |asp でデータの操作"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: bcb8f7bbfa83db9c86cd1278a89750b9f02061d9
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a>ASP.NET Core アプリケーションのデータの操作

> 「データ貴重なこと、システム自体よりも長くなります。」

Tim Berners-lee

## <a name="summary"></a>概要

データ アクセスは、ほぼすべてのソフトウェア アプリケーションの重要な部分です。 ASP.NET Core では、さまざまなデータ アクセス オプション、Entity Framework Core (と同様に、Entity Framework 6) を含むをサポートし、任意の .NET データ アクセス フレームワークを使用できます。 データ アクセス フレームワークを使用する選択は、アプリケーションのニーズによって異なります。 抽象化して、ApplicationCore および UI プロジェクトから、これらの選択肢とインフラストラクチャでの実装の詳細をカプセル化は、疎結合、テスト可能なソフトウェアを生成するために役立ちます。

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (用リレーショナル データベース)

リレーショナル データを操作する必要がある新しい ASP.NET Core アプリケーションを作成する場合は、そのデータにアクセスするアプリケーションに対して推奨される方法は Entity Framework コア (EF) です。 EF Core とは、.NET 開発者は、データ ソースとの間のオブジェクトを保持するオブジェクト リレーショナル マッパー (O/RM) です。 これにより、開発者が作成することも通常、データ アクセス コードのほとんどの必要があります。 ASP.NET Core と同様に EF コア書き直しましたモジュール型プラットフォーム アプリケーションをサポートして一からです。 スタートアップ時に、構成すること、およびでも、必要な依存性の注入を通じて要求 NuGet パッケージとしてアプリケーションに追加します。

EF コアを SQL Server データベースを使用するのには、次の dotnet CLI コマンドを実行します。

dotnet は、Microsoft.EntityFrameworkCore.SqlServer のパッケージを追加します。

テストするため、InMemory データ ソースのサポートを追加します。

dotnet は、Microsoft.EntityFrameworkCore.InMemory のパッケージを追加します。

### <a name="the-dbcontext"></a>DbContext

EF コアを使用するには、DbContext のサブクラスを作成する必要があります。 このクラスは、アプリケーションの動作のエンティティのコレクションを表すプロパティを保持します。 EShopOnWeb サンプルには、項目、ブランド、および種類のコレクションで CatalogContext が含まれます。

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

DbContext は DbContextOptions を受け入れるコンス トラクターを持つし、基本 DbContext コンス トラクターにこの引数を渡す必要があります。 なお、アプリケーションで 1 つだけ DbContext がある場合、DbContextOptions のインスタンスを渡すことができますがある場合は、ジェネリック DbContextOptions を使用した 1 つ以上の必要があります<T>DbContext 型としてジェネリック パラメーターに渡す型。

### <a name="configuring-ef-core"></a>EF Core の構成

ASP.NET Core アプリケーションでは、通常 ConfigureServices メソッドで EF コアを構成します。 EF コアを使用、DbContextOptionsBuilder では、その構成を合理化するいくつかの便利な拡張メソッドをサポートします。 構成で定義されている接続文字列で、SQL Server データベースを使用する CatalogContext を構成するのには、ConfigureServices に次のコードを追加します。

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

メモリ内のデータベースを使用します。

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

DbContext の子の種類を作成、EF コアをインストールして、ConfigureServices で構成したが後、は、EF コアを使用する準備ができたらです。 必要とする任意のサービスで、DbContext 型のインスタンスを要求する場合と同様、コレクション内だけでは、LINQ を使用して、永続化されたエンティティの操作を開始することができます。 EF コアは、格納およびデータを取得する SQL クエリに、LINQ 式に変換する作業を行います。

ロガーを構成し、そのレベルが以上に設定ことを確認して EF Core を実行してクエリを表示については、図 8-1 に示すようにします。

![](./media/image8-1.png)

コンソールに図 8-1 EF コアのログのクエリ

### <a name="fetching-and-storing-data"></a>フェッチとデータを格納します。

EF コアからデータを取得するには、は、適切なプロパティにアクセスし、LINQ を使用して結果をフィルター処理します。 1 つの型から別の結果を変換する投影法を実行するのに LINQ を使用することもできます。 次の例は、CatalogBrands、名前順で、それぞれの Enabled プロパティでフィルター処理し、SelectListItem 型に投影されてを取得します。

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

上記の例をすぐにクエリを実行するのには、ToListAsync への呼び出しを追加する必要があります。 それ以外の場合、ステートメントは、IQueryable を割り当てます<SelectListItem>brandItems にこれは実行されません列挙されるまでです。 長所と短所メソッドから IQueryable 結果を返すには。 これにより、EF コアを構築に変更することもできます、実行時にのみ発生するエラーになり、操作が EF コアが変換できない、クエリに追加された場合にクエリできます。 フィルターはすべてをデータ アクセスを実行するメソッドに渡すには一般に安全であるし、戻り値は、メモリ内コレクションのバックアップ (たとえば、一覧<T>)、結果として。

EF コアは、永続化ストアからデータをフェッチするエンティティの変更を追跡します。 保存する変更追跡対象エンティティでは、エンティティのフェッチに使用されたものと同じ DbContext インスタンスであることを確認、DbContext で SaveChanges メソッドを呼び出すだけです。 追加して、エンティティの削除は、データベース コマンドを実行する savechanges メソッドの呼び出しを使用して、適切な DbSet プロパティに直接です。 次の例では、追加、更新、および永続化ストアからエンティティの削除を示します。

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

EF コアは、同期の両方をサポートし、フェッチして保存するための非同期メソッドです。 Web アプリケーション、ことをお勧め async と await パターンを使用して、非同期のメソッドとデータ アクセス操作の完了を待機中に web サーバーのスレッドがブロックされないようにします。

### <a name="fetching-related-data"></a>関連するデータのフェッチ

EF コアは、エンティティを取得するすべてのデータベースでは、そのエンティティに直接格納されているプロパティを設定します。 関連エンティティのリストなどのナビゲーション プロパティが作成されないとその値に設定がありますは null です。 これにより、EF コアをフェッチしていないデータは、必要なよりも多く、すばやく要求を処理および効率的な方法で応答を返す必要がある web アプリケーションに特に重要であります。 使用して、エンティティとの関係を含める*一括読み込み*、ように、クエリに含める拡張メソッドを使用して、プロパティを指定します。

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

複数のリレーションシップを含めることができ、サブ リレーションシップを含めることもできます ThenInclude を使用します。 EF コアでは、エンティティの結果セットを取得する 1 つのクエリを実行します。

関連するデータを読み込むための別のオプションは、使用する*明示的な読み込み*です。 明示的な読み込みを使用すると、既に取得されているエンティティに追加のデータを読み込むことができます。 このため、データベースを別の要求には、のでお勧めできませんデータベースの数を最小限に抑える必要があります、web アプリケーションの要求ごとのラウンド トリップされます。

*遅延読み込み*機能では、アプリケーションによって参照されているために、関連するデータを自動的に読み込まれます。 EF Core でサポートされていないとして明示的な読み込みを使用にする必要があります通常無効に web アプリケーション用。

### <a name="resilient-connections"></a>回復力のある接続

SQL データベースなどの外部のリソースがときどき使用できません。 一時的な使用不可の場合は、アプリケーションは、例外の発生を回避する再試行ロジックを使用できます。 この手法は一般に呼ば*接続の回復*です。 実装することができます、[指数バックオフによる独自の再試行](https://docs.microsoft.com/azure/architecture/patterns/retry)しようとして待機時間が指数関数的に増加する再試行されるまで、最大再試行回数に達している手法です。 この手法は、クラウド リソースが断続的に使用できなくなることをいくつかの要求のエラーが発生しました、短い期間のファクトを採用します。

Azure SQL DB、Entity Framework のコアには、既に内部データベース接続の回復性と再試行ロジックが用意されています。 回復力のある EF コア接続する場合は、DbContext 接続ごとに、Entity Framework の実行方法を有効にする必要があります。

たとえば、EF コア接続レベルでは、次のコードは、接続に失敗した場合に再試行回復力のある SQL 接続を有効します。

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>実行方法と BeginTransaction と複数 DbContexts を使用して明示的なトランザクション 
  
  EF コア接続では、再試行が有効な場合、EF コアを使用して実行する各操作は、独自の再試行可能な操作になります。 一時的なエラーが発生した場合、各クエリおよび SaveChanges に対する各呼び出しが単位として再試行されます。
  
  ただし、コードでは、BeginTransaction を使用してトランザクションを開始する場合は、ユニットとして扱われる必要のある操作のグループを定義する — 障害が発生した場合に、トランザクション内のすべてロールバックされます。 EF の実行方法 (再試行ポリシー) を使用する場合は、そのトランザクションを実行しようとして、それらに含める複数 DbContexts からいくつかの SaveChanges いる場合、次のような例外が表示されます。

System.invalidoperationexception: 構成済みの実行方法 'SqlServerRetryingExecutionStrategy' はユーザーが開始したトランザクションをサポートしていません。 'DbContext.Database.CreateExecutionStrategy()' によって返される実行方法を使用して、再試行可能な単位としてトランザクション内のすべての操作を実行します。

ソリューションでは、手動で実行する必要があるすべてのものを表すデリゲートを使用して EF の実行方法を呼び出します。 一時的な障害が発生した場合、実行方法は、デリゲートをもう一度呼び出されます。 次のコードは、このアプローチを実装する方法を示しています。

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

First DbContext、\_内では、DbContext catalogContext と 2 番目、 \_integrationEventLogService オブジェクト。 最後に、複数 DbContexts と EF の実行方法を使用して、コミット操作が実行されます。

> ### <a name="references--entity-framework-core"></a>参照: Entity Framework Core
> - **EF コア ドキュメント**  
> <https://docs.microsoft.com/ef/>
> - **関連するデータの EF コア:**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **ASPNET アプリケーション内のエンティティの遅延読み込みを回避します。**  
> <http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF コアまたは MICRO-ORM しますか。

EF コアが永続化ストアの管理に最適の大部分はアプリケーションの開発者からのデータベースの詳細をカプセル化中にのみ選択ではありません。 別の一般的なオープン ソースの代替手段は[Dapper](https://github.com/StackExchange/Dapper)、いわゆる MICRO-ORM です。 MICRO-ORM は、以下のオブジェクトをデータ構造にマップするためのツールの全機能を備えた、軽量なです。 Dapper の場合は、完全を基になるカプセル化するクエリを実行してではなく、パフォーマンスの目標の中心の設計は、データを取得および更新使用します。 Developer から SQL を抽象にしないので、Dapper は「金属に最も近い」であり、開発者は、正確な記述できますクエリに指定されたデータを使用する操作にアクセスします。

EF コアで提供されます Dapper から分離するためが、またそのパフォーマンスのオーバーヘッドを追加する 2 つの重要な機能があります。 最初は、SQL に LINQ 式からの変換です。 これらの変換がキャッシュされるが、それでもオーバーヘッドで最初にそれらを実行します。 2 つ目は、変更の追跡エンティティ (できるようにする効率的な update ステートメントを生成できます) です。 この動作は AsNotTracking 拡張機能を使用して、特定のクエリをオフにすることができます。 EF Core では、通常は、非常に効率的ないずれの場合でもまったく問題ないパフォーマンスの観点から SQL クエリも生成されますが、実行するクエリを正確に制御を微調整する必要があるカスタム SQL で渡すことができます (またはストアド プロシージャを実行) EF を使用します。コアすぎます。 口ひげ静止が EF コアを上回るこの場合はごくわずかです。 自分の一部のパフォーマンス データが 2016 MSDN の記事 Julie Lerman 表示[Dapper、エンティティ フレームワーク、およびハイブリッド アプリ](https://msdn.microsoft.com/magazine/mt703432.aspx)です。 データ アクセス方法のさまざまな追加のパフォーマンス ベンチマーク データにあります[口ひげサイト](https://github.com/StackExchange/Dapper)です。

EF コアから Dapper の構文がどのように変化を表示するには、項目の一覧を取得するため、同じメソッドの 2 つのバージョンを考慮してください。

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

Dapper でより複雑なオブジェクト グラフを作成する必要がある場合は、(EF コアの場合とは、インクルードを追加) ではなく自分で関連付けられているクエリを作成する必要があります。 これは、さまざまな構文では、個々 の行を複数のマップされたオブジェクトにマップできるマルチ マッピングと呼ばれる機能を含むを通じてサポートされます。 たとえば、ユーザーの種類のプロパティの所有者で Post クラスを指定するには、次の SQL と返されますのすべての必要なデータ。

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

返される各行には、ユーザーとポストの両方のデータが含まれています。 ユーザー データは、その所有者のプロパティを使用して Post データにアタッチする必要があります、ため、次の関数は使用されます。

```csharp
(post, user) => { post.Owner = user; return post; }
```

完全なコード リストの Owner プロパティを関連付けられたユーザー データが設定されると投稿のコレクションを返すには次のようになります。

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

開発者は、そのデータの格納方法の詳細について以下のカプセル化を提供するため Dapper が必要です、効率的にクエリを実行して、それをフェッチするコードを書き込む方法です。 新しい移行 (EF コア、別の機能) を作成や、DbContext で 1 つの場所のマッピング情報を更新するだけではなく、モデルが変更されたときに、影響を受けるすべてのクエリを更新する必要があります。 これらのクエリがコンパイル時保証ないであるため、モデルまたはエラーを迅速に検出が困難なには、データベースに変更に応答実行時に中断する可能性があります。 これらのトレードオフと引き換えに Dapper は非常に高速パフォーマンスを提供します。

ほとんどのアプリケーションで、ほぼすべてのアプリケーションのほとんどの部分に対しては、EF コアは、許容されるパフォーマンスを提供します。 したがって、その開発者の生産性は、そのパフォーマンスのオーバーヘッドを上回る可能性があります。 キャッシュから利点を活用できるクエリの実際のクエリのみ実行できます比較的小さいため、時間の割合を小さなクエリのパフォーマンスの違い問題になりません。

## <a name="sql-or-nosql"></a>SQL または NoSQL

従来は、SQL Server などのリレーショナル データベースに永続的なデータ記憶域は、marketplace が左右されますが、使用可能な唯一のソリューションではありません。 などの NoSQL データベース[MongoDB](https://www.mongodb.com/what-is-mongodb)オブジェクトを格納するためのさまざまなアプローチを提供します。 オブジェクトをテーブルと行にマップするのではなく別のオプションは、オブジェクト グラフ全体をシリアル化して、結果を格納するです。 この方法のメリットは、簡潔さとパフォーマンスに少なくとも最初です。 更新プログラムおよび可能性がありますので、オブジェクトが最後に変更された行をデータベースから取得し、リレーションシップを持つ多数のテーブルにオブジェクトを分解するよりもキーを持つ 1 つのシリアル化されたオブジェクトを格納するは確かにシンプルです。 同様に、フェッチして、キー ベースのストアから 1 つのオブジェクトを逆シリアル化は通常より迅速かつ複雑な結合または完全に同じリレーショナル データベースからオブジェクトを作成するために必要な複数のデータベース クエリよりも簡単です。 ロックやトランザクションまたは固定スキーマがないことも、NoSQL データベース非常に大規模なデータセットをサポートする多数のマシン間でのスケーリングに非常に適したします。

その一方で、NoSQL データベース (ように、通常と呼ばれる) があるそれぞれの欠点です。 リレーショナル データベースでは、整合性を適用し、データの重複を避けるために正規化を使用します。 これにより、データベースの合計サイズが削減され、共有データへの更新プログラムがすぐに、データベース全体で使用可能であることを確認します。 リレーショナル データベース自体を更新することがなく、更新プログラムからアドレス レコードと効果的な国の名前が変更された場合になるよう、アドレス テーブルは ID を使用して国テーブルを参照する可能性があります。 ただし、NoSQL database でのアドレスおよびその関連付けられている国可能性がありますシリアル化する多くの保存されているオブジェクトの一部として。 国の名前に更新プログラムは、1 つの行ではなく、更新するすべてのオブジェクトを必要となります。 リレーショナル データベースでは、外部キーのようにルールを適用することでもリレーショナル整合性を確認できます。 通常、NoSQL データベースでは、そのデータには、このような制約は用意されません。

別の複雑な NoSQL データベースを扱う必要がありますが、バージョン管理します。 オブジェクトのプロパティを変更するときに、格納されていた過去のバージョンから逆シリアル化できません可能性があります。 したがって、オブジェクトのシリアル化された (以前の) バージョンがすべての既存のオブジェクトは、新しいスキーマに準拠するように更新しなければなりません。 これは概念的には、リレーショナル データベースから別ではなく、スキーマの変更も更新スクリプトを必要とまたは更新プログラムをマッピングします。 ただし、変更する必要があるエントリの数は多くの場合、ほとんどのデータの複数の重複があるため NoSQL のアプローチで大きくします。

通常何かの固定スキーマのリレーショナル データベースがサポートされていない場合は、NoSQL データベース オブジェクトの複数のバージョンを格納することも可能です。 ただし、ここでは、アプリケーション コードは以前のバージョンの複雑さを追加するオブジェクトの存在を考慮する必要があります。

通常 NoSQL データベースが適用されない[ACID](http://en.wikipedia.org/wiki/ACID)、リレーショナル データベースでパフォーマンスとスケーラビリティの両方の利点があることを意味します。 これらは、大量のデータセットとは正規化されたテーブルの構造内のストレージに適していないオブジェクトに最適です。 理由 1 つのアプリケーションを利用できません両方リレーショナルとを使用して各は、最適な NoSQL データベースが適しています理由はありません。

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB は、完全に管理された NoSQL データベース サービス スキーマのないデータのクラウド ベースの記憶域を提供します。 DocumentDB は、高速で予測可能なパフォーマンス、高可用性、柔軟なスケーリング、およびグローバル配布用に作成されています。 NoSQL database あるにもかかわらず、開発者は、JSON データの豊富な使い慣れた SQL のクエリ機能を使用できます。 DocumentDB のすべてのリソースは、JSON ドキュメントとして格納されます。 リソースとして管理*項目*する、メタデータを含むドキュメントと*フィード*項目のコレクションであります。 図 8-2 は、別の DocumentDB リソース間の関係を示しています。


![DocumentDB では、JSON の NoSQL データベース リソース間の階層関係](./media/image8-2.png)

**図 8-2 です。** DocumentDB リソース組織。

DocumentDB クエリ言語は、JSON ドキュメントを照会するための単純かつ強力なインターフェイスです。 言語は ANSI SQL の文法のサブセットをサポートし、JavaScript オブジェクト、配列、オブジェクトの構築、および関数の呼び出しの緊密な統合を追加します。

**参照: DocumentDB**

-   DocumentDB Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>その他の持続性オプション

リレーショナルへの追加と NoSQL 記憶域オプションで ASP.NET Core アプリケーションは、スケーラブルなクラウド ベースの方法でさまざまなデータ形式とファイルを保存するのに Azure ストレージを使用できます。 Azure ストレージは非常にスケーラブルな少量のデータと、アプリケーションで必要な場合は、数百またはテラバイトを格納する最大の小数点以下桁数を格納するアウトすることができます。 Azure ストレージには、次の 4 つの種類のデータがサポートしています。

-   非構造化テキストまたはオブジェクトの格納とも呼びますバイナリのストレージの blob ストレージです。

-   テーブル ストレージ構造化されたデータセットの場合、行キーを使用してアクセスできます。

-   信頼性の高いキュー ベースのメッセージング キューの記憶域。

-   Azure の仮想マシンと内部設置型アプリケーション間でファイル共有にファイル記憶域。

**– Azure ストレージの参照**

-   Azure ストレージ Introduction\
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>キャッシュ

Web アプリケーションで、各 web 要求をできるだけ短時間で完了する必要があります。 これを実現する方法の 1 つでは、サーバーが、要求を完了に加える必要が外部の呼び出しの数を制限します。 キャッシュは、サーバー上のデータのコピーを保存する (または別のデータを格納されているデータのソースよりも簡単にクエリの詳細)。 Web アプリケーション、および特に非 SPA 従来の web アプリケーションは、すべての要求による全体のユーザー インターフェイスを構築する必要があります。 これには、1 人のユーザーの要求から繰り返し、次に同じデータベースをクエリの多くを行う頻繁に行われます。 ほとんどの場合、このデータが変更されたまれに、データベースから常に要求したときに理由はほとんどがあるためです。 ASP.NET Core サポート全体のページ、およびデータのキャッシュをキャッシュに、応答のキャッシュをより詳細なキャッシュ動作をサポートします。

キャッシュを実装するときにすることが重要に関心の分離を考慮してください。 または、ユーザー インターフェイスで、データ アクセス ロジックでのキャッシュ ロジックを実装しないでください。 代わりに、独自のクラスでのキャッシュをカプセル化し、その動作を管理する構成を使用します。 これは、開く/解決済みと 1 つの役割の基本原則に従いますがやすくしたり拡張時に、アプリケーションでキャッシュを使用する方法を管理するためです。

### <a name="aspnet-core-response-caching"></a>ASP.NET Core 応答のキャッシュ

ASP.NET Core では、応答のキャッシュの 2 つのレベルをサポートします。 最初のレベルは、キャッシュ サーバーで、何もしませんが、クライアントと応答をキャッシュするプロキシ サーバーを指示する HTTP ヘッダーを追加します。 これは、個々 のコント ローラーやアクションに ResponseCache 属性を追加することによって実装されます。

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

応答のキャッシュ ミドルウェアは、一連のカスタマイズ可能な条件に基づいて応答を自動的にキャッシュされます。 既定では、GET または HEAD メソッドを使用して要求のみ 200 (OK) 応答がキャッシュされます。 さらに、要求がキャッシュ制御の応答をいる必要があります: パブリック ヘッダーは、承認または Set-cookie ヘッダーを含むことはできません。 参照してください、[応答のミドルウェアのキャッシュで使用されるキャッシュの条件の完全な一覧](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)です。

### <a name="data-caching"></a>データ キャッシュ

ではなく (またはそれらに加えて) 完全な web 応答のキャッシュ、個々 のデータのクエリの結果をキャッシュすることができます。 これは、web サーバー上のメモリ キャッシュの使用または使用[分散キャッシュ](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)です。 このセクションでは、メモリ キャッシュに実装する方法を示します。

メモリのサポートを追加 (または分散) ConfigureServices でのキャッシュします。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

同様に、Microsoft.Extensions.Caching.Memory NuGet パッケージを追加することを確認します。

サービスを追加したらを要求する IMemoryCache 依存関係の挿入を使用して、キャッシュにアクセスする必要がある場所にします。 この例では、CachedCatalogService がへのアクセス制御 (または動作を追加して) ICatalogService の代替実装を提供することで、プロキシ (またはデコレータ) のデザイン パターンを使用して基になる CatalogService 実装します。

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

サービスのキャッシュされたバージョンを使用する許可 CatalogService のコンス トラクターに必要なのインスタンスを取得するサービスを許可するアプリケーションを構成するのには、ConfigureServices で、次を追加します。

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

これで、カタログ データをフェッチするデータベースの呼び出しはできるだけのすべての要求ではなく、1 分ごと 1 回です。 によっては、サイトにトラフィックには、データベース、および現在このサービスによって公開されているクエリの 3 つすべてが依存するホーム ページの平均ページ読み込み時間に加えられたクエリの数に非常に大きく影響するこれがあります。

キャッシュが実装された場合に発生する問題は*古いデータ*: ソースが最新のバージョンで変更されたデータがキャッシュに保持する、します。 この問題を緩和する簡単な方法では、ビジー状態のアプリケーションのデータがキャッシュされる長さを拡張する制限の追加利点は小規模のキャッシュ期間を使用します。 たとえば、1 つのデータベース クエリを実行するページが 1 秒あたり 10 回要求されたとします。 このページは、1 分間キャッシュは、1 分あたり 1、99.8% の削減に 600 からドロップに対するデータベース クエリの数になります。 代わりにキャッシュの存続期間は 1 時間に加えられた場合、全体的な減少が 99.997% であっても今すぐ古いデータの尤度と潜在的な有効期間はどちらも大幅に増加します。

別の方法が含まれているデータが更新されたときに、キャッシュ エントリを能動的に削除を開始します。 そのキーがわかっている場合、任意の個々 のエントリを削除できます。

```csharp
_cache.Remove(cacheKey);
```

アプリケーションでは、キャッシュされたエントリを更新するための機能を公開する場合は、更新プログラムを実行するコードで、対応するキャッシュ エントリを削除できます。 場合によって特定のデータのセットに依存している多くの異なるエントリがあります。 その場合は、だということ、CancellationChangeToken を使用して、キャッシュ エントリ間の依存関係を作成すると便利です。 CancellationChangeToken とできます期限切れにする複数のキャッシュ エントリを一度にトークンをキャンセルしています。

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
[前](develop-asp-net-core-mvc-apps.md) [次へ] (test-asp-net-core-mvc-apps.md)
