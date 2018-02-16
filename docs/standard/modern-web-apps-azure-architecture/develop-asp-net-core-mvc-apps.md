---
title: "ASP.NET Core MVC アプリの開発"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |ASP.NET Core MVC アプリの開発"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a>ASP.NET Core MVC アプリを開発します。

> "重要ではありませんが、正しく理解する最初の時間です。 これはさせるために、前回の非常に重要です。"  
> _-Andrew 狩猟と David Thomas_

## <a name="summary"></a>まとめ

ASP.NET Core は、最新のクラウドに最適化された web アプリケーションを構築するためのプラットフォーム間、オープン ソース フレームワークです。 ASP.NET Core アプリケーションは、軽量なテストの容易性と保守容易性の向上で有効にすると、依存関係の挿入の組み込みサポートを備えた、モジュール型です。 MVC で、ビュー ベースのアプリだけでなく最新の web Api の構築をサポートするには、組み合わせる ASP.NET Core は、エンタープライズ web アプリケーションのビルドに使用する強力なフレームワークです。

## <a name="mapping-requests-to-responses"></a>応答への要求のマッピング

中心には、ASP.NET Core アプリケーションは、発信応答を受信した要求をマップします。 低レベルでミドルウェア、これし、可能性がありますがカスタム ミドルウェアののみで構成される単純な ASP.NET Core アプリケーションと microservices です。 ASP.NET Core MVC を使用するときに使用できるやや高度のレベルでの観点で考える*ルート*、*コント ローラー*、および*アクション*です。 アプリケーションのルーティング テーブルと各着信要求を比較し、一致するルートが見つかった場合、関連付けられたアクション (コント ローラーに属する) メソッドが要求を処理します。 一致するルートが見つからない場合は、(この場合、NotFound 結果を返す) をエラー ハンドラーが呼び出されます。

ASP.NET Core MVC アプリには、従来のルート、属性のルート、またはその両方を使用できます。 従来のルートがルーティングを指定する、コードで定義されている*規則*のような構文を使用して、次の例。

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

この例では"default"をという名前のルートがルーティング テーブルに追加されました。 定義のプレース ホルダーでルート テンプレート*コント ローラー*、*アクション*、および*id*です。コント ローラーとアクションのプレース ホルダーは、指定された既定値を持つ (「ホーム」と"Index"それぞれ)、id プレース ホルダーは省略可能 (のとなります。 したがって、、"?"を適用)。 規約ここで定義された状態は、要求の最初の部分と一致する 2 番目の部分には、アクション、コント ローラーの名前とし、必要に応じて、3 番目の部分を表す id パラメーター。 従来のルートは通常スタートアップ クラスのメソッドで、構成など、アプリケーションを 1 か所に定義されます。

属性ルートをグローバルに指定された代わりに直接、コント ローラーとアクションに適用されます。 これにより、ようにはるかに探索可能なときにする場合、特定のメソッドに参照しているわけでは、アプリケーションで 1 か所でルーティング情報が保持されないことの利点があります。 属性のルートを持つを簡単に特定のアクションに対して複数のルートを指定したりできるようコント ローラーとアクション間のルートを結合します。 例:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

[HttpGet] のルートを指定することができ、類似する属性を追加する必要がある分離 [ルート\]属性。 属性のルートでは、次に示すようにコント ローラーまたはアクションの名前を繰り返す必要性を減らすトークンも使用できます。

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

ASP.NET Core MVC は、特定の要求は、ルートに一致していないが、メソッドが呼び出されたアクションの前に、[モデル バインディング](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding)と[モデルの検証](https://docs.microsoft.com/aspnet/core/mvc/models/validation)要求でします。 モデル バインディングが呼び出されるアクション メソッドのパラメーターとして指定された .NET 型、入力方向の HTTP データを変換する役割を担当します。 たとえば、アクション メソッドには、int id パラメーターが必要ですが場合、モデル バインドは、要求の一部として指定された値からこのパラメーターを指定しようとします。 これを行うには、モデル バインディングは、ポストされたフォーム内の値、ルート、自体の値およびクエリ文字列の値を検索します。 Id 値があると仮定した場合、変換されますを整数アクション メソッドに渡される前にします。

モデルをバインドした後は、アクション メソッドを呼び出す前にモデルの検証が行われます。 モデルの検証では、モデルの種類、省略可能な属性を使用し、指定されたモデル オブジェクトが特定のデータ要件に準拠していることを確認できます。 特定の値として指定できるなどのために必要なまたは特定の長さまたは数値の範囲に制限されます、します。検証属性が指定されたモデルがその要件に準拠していない場合は、プロパティ ModelState.IsValid が false に設定され失敗する検証規則のセットは要求を行うクライアントに送信する使用可能です。

モデルの検証を使用している場合は、常にチェックするモデルが無効なデータでは、アプリが破損しないようにする、任意の状態変更コマンドを実行する前に有効であることを確認できます。 使用することができます、[フィルター](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)すべてのアクションでこのコードを追加する必要がなくなります。 ASP.NET Core MVC フィルターは、一般的なポリシーと横断的関心事は対象となるごとに適用できるように、要求のグループをインターセプトする方法を提供します。 または個々 のアクション、全体のコント ローラーにグローバルにアプリケーションのフィルターを適用できます。

ASP.NET Core MVC をサポートしている web Api、 [*コンテンツ ネゴシエーション*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting)応答を書式設定する方法を指定する要求を許可します。 要求で指定されたヘッダーに基づき、データを返すアクションは XML、JSON、または別のサポートされている形式で応答をフォーマットします。 この機能は、別のデータ形式の要件を持つ複数のクライアントによって使用される同じ API を使用します。

> ### <a name="references--mapping-requests-to-responses"></a>参照: 応答への要求のマッピング
> - **コント ローラー アクションへのルーティング**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **モデル バインディング**https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **モデルの検証**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **フィルター** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>依存関係の操作

ASP.NET Core の組み込みサポートがあり、内部的に使用すると呼ばれる手法[依存性の注入](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)です。 依存関係の挿入は、アプリケーションのさまざまな部分との間の疎結合を有効になっている手法です。 やすくテスト用または交換できるように、アプリケーションの部分に分離するためよりゆるやかに結合の使用をお勧めします。 また、アプリケーションの 1 つの部分で変更が、アプリケーションで別の場所に予期しない影響を与える必要がある可能性を低減します。 依存関係の挿入は依存関係の逆転原則に基づいて、多くの場合、開く/閉じる原則を達成するキー。 アプリケーションがその依存関係にどのように処理する方法を評価するときに注意してください、[静的窓](http://deviq.com/static-cling/)決まり、コードを格言を覚えておく"[新しいはグルー](http://ardalis.com/new-is-glue)"。

静的窓は、クラスは、静的メソッドへの呼び出しを加えるか、静的プロパティは、副作用または依存関係インフラストラクチャ上にあるアクセスに発生します。 たとえば、メソッドを静的メソッドをさらに、データベースに書き込むと、呼び出しがある場合、メソッドが密に結合されて、データベース。 メソッドをそのデータベースの呼び出しを中断しているものが中断します。 そのようなテスト、静的な呼び出しのモック作成商用のモック ライブラリ必要またはのいずれかの場所でテスト データベースをテストするため、このようなメソッドのテストは非常に困難です。 特には完全にステートレスで、インフラストラクチャの依存を持たない静的の呼び出しを呼び出すし、結合または (コードを静的な呼び出し自体に結合) を超えるテストの容易性に影響を与えるありませんしても問題ありません。

多くの開発者は、静的窓とグローバル状態は、のリスクを理解はまだ密コードの特定の実装を介して直接インスタンス化します。 「新しいはグルー」は目的としてこの結合のアラームと new キーワードの使用の一般的な condemnation されません。 同様、静的メソッドの呼び出しで外部の依存関係を通常がない型の新しいインスタンスは厳重に実装の詳細にコードを結合するまたはするテストが難しくします。 クラスがインスタンス化されるたびにすぐだけ簡単なをする意味がハード コードする特定のインスタンスを特定の場所であるかどうか、またはより優れた設計の依存関係としては、そのインスタンスを要求することが検討してください。

### <a name="declare-your-dependencies"></a>依存関係を宣言します。

ASP.NET Core が構築されています。 メソッドを持つし、クラスが引数としてそれらの要求、依存関係を宣言します。 ASP.NET アプリケーションがクラスでは、スタートアップ、セットアップして通常自体がいくつかの時点の依存関係の挿入をサポートするために構成されています。 依存関係のコンス トラクター、要求すること、スタートアップ クラスにコンス トラクターがある場合は、次のようにします。

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

スタートアップ クラスは、明示的な型の要件がないことに興味深いです。 特殊なスタートアップ基底クラスから継承されません。 また、特定のインターフェイスは実装。 付けることができます、コンス トラクターもそうでないと、必要な数だけ、コンス トラクターにパラメーターを指定できます。 アプリケーションを構成したら、web ホストの開始時にするように指示したを使用するスタートアップ クラスを呼び出すし、スタートアップ クラスに必要なすべての依存関係を設定する依存関係の挿入を使用します。 もちろん、ASP.NET Core によって使用されるサービス コンテナーで構成されていないパラメーターを要求すると、例外が表示されますが、依存関係にオプションを使用している限り、コンテナーが認識、自分の好きを要求することができます。

依存関係の挿入は、スタートアップ インスタンスを作成するときに、一から ASP.NET Core アプリケーションに組み込まれてです。 スタートアップ クラスの存在に停止しません。 Configure メソッド内の依存関係を要求することもできます。

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

ConfigureServices メソッドは、この動作を例外IServiceCollection 型のパラメーターを 1 つだけがかかる必要があります。 依存関係の挿入をサポートして一方で、サービス コンテナーにオブジェクトを追加する必要があり、IServiceCollection パラメーターを介して現在構成されているすべてのサービスへのアクセス権を持つ、別のために本当に必要はありません。 したがって、パラメーターとして必要なサービスを要求するか ConfigureServices で IServiceCollection で作業してスタートアップ クラスのすべての部分で ASP.NET Core services コレクションで定義されている依存関係を操作できます。

> [!NOTE]
> 特定のサービスがスタートアップ クラスで使用できることを確認する必要がある場合、それらを構成できます WebHostBuilder とその ConfigureServices メソッドを使用します。

スタートアップ クラスは、独自のサービスをフィルターするミドルウェアをコント ローラーから、ASP.NET Core アプリケーションの他の部分を構成する方法のモデルです。 いずれの場合に従う必要があります、[明示的な依存関係の原則](http://deviq.com/explicit-dependencies-principle/)、要求、依存関係はなく、直接、それらを作成して、アプリケーション全体の依存関係の挿入を活用することです。 実装では、特にサービスとインフラストラクチャを使用または副作用があるオブジェクトを直接インスタンス化する場所と方法に注意します。 アプリケーション主要で定義されているし、特定の実装の種類へのハードコード参照を引数として渡されたの抽象化の操作を優先します。

## <a name="structuring-the-application"></a>アプリケーションを構成します。

モノリシックなアプリケーションには、通常 1 つのエントリ ポイントがあります。 ASP.NET Core web アプリケーションの場合は、ASP.NET Core web プロジェクトがエントリ ポイントになります。 ただし、ことを意味して、ソリューションは、1 つのプロジェクトだけで構成される必要があります。 次の問題を分離するために別のレイヤーにアプリケーションを中断すると便利です。 レイヤーに分割した後を別個のカプセル化の向上を実現するのに役立てることができるプロジェクト フォルダーより先に進むことをお勧めします。 ASP.NET Core アプリケーションと、これらの目標を実現するために最適な方法は、第 5 章で説明したクリーン アーキテクチャの変形です。 この方法は、次のアプリケーションのソリューションで構成されます別個のライブラリの UI、インフラストラクチャ、および ApplicationCore 用です。

これらのプロジェクトだけでなく別のテスト プロジェクトが含まれますも (テストは 9 章で説明しています)。

アプリケーションのオブジェクト モデルとのインターフェイスは、ApplicationCore プロジェクトに配置する必要があります。 このプロジェクトは、できるだけ少ないの依存関係のあるし、ソリューション内の他のプロジェクトが参照されます。 永続化する必要があるビジネス エンティティは、直接依存していないインフラストラクチャ サービスにも、ApplicationCore プロジェクトで定義されます。

永続化を実行する方法や、ユーザーに通知を送信する方法など、実装の詳細は、インフラストラクチャのプロジェクトで保持されます。 このプロジェクトは、Entity Framework のコアなどの実装に固有のパッケージは、参照は、プロジェクト外部のこれらの実装に関する詳細情報を公開しないでください。 インフラストラクチャ サービスとのリポジトリが ApplicationCore プロジェクトで定義されているインターフェイスを実装する必要があります、永続化の実装を担当しています取得し、ApplicationCore で定義されたエンティティを格納します。

ASP.NET Core プロジェクト自体は、UI レベルの問題を担当するビジネス ロジックまたはインフラストラクチャの詳細を含めないでください。 実際には、理想的には、含めることはできませんでも、依存関係により、2 つのプロジェクト間の依存関係が追加されていない誤って、インフラストラクチャ プロジェクトでします。 これは、各プロジェクトのクラスをレジストリに DI ルールを定義することができる StructureMap のようにサード パーティ製 DI コンテナーを使用して実現できます。

実装の詳細からアプリケーションを分離する方法は、個々 の Docker コンテナーで、展開、アプリケーション呼び出し microservices をことです。 これは問題と 2 つのプロジェクト間 DI を活用することよりも分離のさらに大きく分離を提供が、複雑さが増大します。

### <a name="feature-organization"></a>組織の機能

既定では、ASP.NET Core アプリケーションは、コント ローラーとビュー、およびよく ViewModels を含めるには、そのフォルダー構造を整理します。 通常、これらのサーバー側の構造をサポートするためにクライアント側のコードは wwwroot フォルダーに個別に格納されます。 ただし、大規模なアプリケーションであっても、多くの場合、特定の機能で作業する場合は、これらのフォルダー間を移動する必要があるために、この組織に問題が発生可能性があります。 これは各フォルダーのファイルとサブフォルダーの数が増大すると、ソリューション エクスプ ローラーのスクロールの大量の結果として得られるより困難になってを取得します。 この問題の 1 つのソリューションは、アプリケーション コードを整理することです。*機能*ではなくファイルの種類。 この組織のスタイルを通常呼びます機能フォルダまたは機能のスライス (も参照してください:[垂直スライス](http://deviq.com/vertical-slices/))。

ASP.NET Core MVC には、この目的のための領域がサポートされています。 領域を使用して、コント ローラーとビュー (だけでなくフォルダー、関連付けられているモデル) 領域の各フォルダー内の個別セットを作成できます。 図 7-1 は、領域の使用例のフォルダー構造を示しています。

![](./media/image7-1.png)

図 7-1 サンプル領域組織

領域を使用する場合は、所属する領域の名前、コント ローラーを装飾する属性を使用する必要があります。

```csharp
[Area("Catalog")]
public class HomeController
{}
```

また、領域のサポートをルートに追加する必要があります。

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

領域の組み込みサポート、に加えてに独自のフォルダー構造、および属性とのカスタム ルートの代わりに規則を使用することもできます。 これは、ようにするとして、ビュー、コント ローラーなど、階層を平坦化に維持して、関連するすべての機能ごとに 1 つの場所にファイルを参照してください、簡単に別のフォルダーが含まれていなかった機能フォルダーです。

ASP.NET Core では、組み込みの規則の種類を使用して、その動作を制御します。 変更したり、これらの規則を置き換えます。 たとえば、その名前空間 (これは通常、コント ローラーが配置されているフォルダーに関連している) に基づく指定されたコント ローラーの機能名を自動的に取得する規則を作成できます。

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

として指定するこの規約オプション ConfigureServices でアプリケーションを MVC のサポートを追加する場合。

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC は、ビューの場所にも、規則を使用します。 ビューは、(上、FeatureConvention によって提供される機能名を使用)、機能のフォルダーで見つかることができるように、カスタム規則を含むメソッドをオーバーライドできます。 この方法の詳細し、MSDN の記事から実際のサンプルをダウンロードできます[ASP.NET Core MVC 用機能スライス](https://msdn.microsoft.com/magazine/mt763233.aspx)です。

### <a name="cross-cutting-concerns"></a>横断的な問題

アプリケーションが増すにつれて、重複を排除し、整合性を維持する横断的関心事取り出しをますます重要になります。 横断的関心事 ASP.NET Core アプリケーションでの例は、その他の多くを使用する必要がある場合、認証、モデルの検証規則、出力キャッシュ、およびエラー処理を示します。 ASP.NET Core MVC[フィルター](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters)にする前に、または要求処理パイプライン内の特定の手順の後にコードを実行できるようにします。 たとえば、フィルターでは、前におよび、操作の実行後、または前後にアクションの結果、モデル バインディングの前後を実行できます。 また、パイプラインの残りの部分へのアクセスを制御するのに承認フィルターを使用することができます。 図 7-2 に示します要求方法の実行フローのフィルターを構成されている場合。

![要求は、承認フィルター、リソース フィルター、モデル バインド、アクション フィルター、アクションの実行とアクション結果の変換、例外フィルター、結果フィルター、結果の実行を介して処理されます。 終了間際に、要求は結果フィルターとリソース フィルターのみで処理されてから、クライアントに送信される応答になります。](./media/image7-2.png)

フィルターと要求パイプラインを介して図 7-2 要求の実行。

フィルターをコント ローラーまたはアクションに適用できるように、通常、属性として実装されます。 この方法では、レベルの上書きをアクションまたはコント ローラー レベルで指定されたフィルターをベースに構築で指定されたフィルターで追加されたときにそれ自体はグローバル フィルターをオーバーライドします。 たとえば、\[ルート\]属性は、コント ローラーとアクション間のルートをビルドを使用することができます。 同様に、承認をコント ローラー レベルで構成されているし、次の例に示すように、個々 のアクションによってオーバーライドします。

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

最初のメソッドで、ログインは、コント ローラー レベルの設定、承認フィルターをオーバーライドするのに AllowAnonymous フィルター (属性) を使用します。 ForgotPassword アクション (およびその他のアクション AllowAnonymous 属性を持たないクラスで) には、認証された要求が必要です。

共通のエラー処理ポリシー Api の形式での重複を回避するのには、フィルターを使用できます。 たとえば、一般的な API ポリシーは、モデルの検証が失敗した場合、NotFound 応答が存在しないキーを参照している要求と BadRequest 応答を返すにです。 次の例では、これら 2 つのポリシーの動作を示しています。

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

次のように条件付きコードが散在し、アクション メソッドを許可しません。 代わりに、必要に応じてごとに適用できるフィルターにポリシーをプルします。 この例では、次の属性で、コマンドは、API に送られるたびに発生する必要があります、モデルの検証チェックを置き換えることができます。

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

同様に、レコードが存在し、アクションを実行すると、アクションでこれらのチェックを実行する必要がなくなる前に、404 エラーを返すかどうかにチェックするフィルターを使用できます。 取り込まれた一般的な規則と、UI からインフラストラクチャ コードとビジネス ロジックを分離するようにソリューションを構成した、MVC アクション メソッドがシン非常に高くする必要があります。

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

詳細を読み取ることができますフィルターを実装して、MSDN の記事から実際のサンプルのダウンロードについて[現実世界 ASP.NET Core MVC フィルター](https://msdn.microsoft.com/magazine/mt767699.aspx)です。

> ### <a name="references--structuring-applications"></a>参照: アプリケーションを構成します。
> - **領域**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN-ASP.NET core MVC 機能スライス**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **フィルター**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN-ASP.NET Core MVC フィルターの現実の世界**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>セキュリティ

Web アプリケーションの保護は、さまざまな考慮事項と、大規模なトピックです。 セキュリティには、その最も基本的なレベルでの特定の要求からのものとし、その要求はリソースへのアクセスのみがあることを確認するを把握することを確認が含まれます。 認証は、既知のエンティティから送信された要求を扱うかどうかに表示する、信頼できるデータ ストアの要求で指定された資格情報を比較するプロセスです。 承認は、ユーザー id に基づいて特定のリソースへのアクセスを制限するプロセスです。 3 番目のセキュリティ上の懸念をする必要がありますには、少なくとも、第三者に傍受からの要求を保護する[SSL は、アプリケーションによって使用されていることを確認してください。](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl)です。

### <a name="authentication"></a>認証

ASP.NET Core の Id とは、アプリケーションのログインの機能をサポートするために使用することができます、メンバーシップ システムです。 ローカル ユーザー アカウントのサポートと Microsoft アカウント、Twitter、Facebook、Google などのようなプロバイダーから外部ログイン プロバイダーのサポートがあります。 ASP.NET Core Id だけでなく、アプリケーションが windows 認証を使用して、またはサード パーティ id プロバイダーと同様に[Identity Server](https://github.com/IdentityServer/IdentityServer4)です。

ASP.NET Core の Id は、個々 のユーザー アカウント オプションが選択されている場合、新しいプロジェクト テンプレートに含まれます。 このテンプレートには、登録、ログイン、外部ログイン、パスワードを忘れた場合、および追加の機能のサポートが含まれています。

![](./media/image7-3.png)

図 7-3 選択個々 のユーザー アカウントをあらかじめ構成された Id を持っています。

Id のサポートは、スタートアップ時に、ConfigureServices と構成の両方で構成されます。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

構成メソッドに、その UseIdentity が UseMvc する前に表示されることが重要です。 Identity ConfigureServices でを構成する場合、AddDefaultTokenProviders への呼び出しがわかります。 これは、web 通信をセキュリティで保護するために使用する可能性がありますが、代わりに自身の id を確認するには、SMS またはそれらの順序で電子メールによってユーザーに送信できるメッセージを作成するプロバイダーを参照するトークンを行うには関係ありません。

詳細について[2 要素認証を構成する](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)と[外部ログイン プロバイダーを有効にする](https://docs.microsoft.com/aspnet/core/security/authentication/social/)公式の ASP.NET Core docs からです。

### <a name="authorization"></a>承認

承認の最も単純な形式では、匿名ユーザーにアクセスを制限する必要があります。 適用すると、これを行う、 \[Authorize\]属性を特定のコント ローラーまたはアクションにします。 ロールを使用している場合のように、特定のロールに属しているユーザーにアクセスを制限する属性をさらに拡張できます。

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

この場合、いずれか (または両方) の HRManager または Finance ロールに属しているユーザーは、SalaryController へのアクセスがあります。 (複数に 1 つだけでなく) 複数のロールにユーザーが属していることを必要とするには、適用できます属性を複数回ごとに必要な役割を指定します。

多くのさまざまなコント ローラーとアクションの文字列が望ましくない繰り返しにつながる可能性が特定のロールのセットを指定します。 承認規則をカプセル化、承認ポリシーを構成して適用するときに、個々 のロールではなく、ポリシーを指定、 \[Authorize\]属性。

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

この方法でポリシーを使用して、特定のロールまたはそれに適用される規則が制限されているアクションの種類を区切ることができます。 後で、特定のリソースへのアクセスを必要とする新しいロールを作成する場合だけ更新できますですべての役割の一覧を更新するのではなく、ポリシーをすべて\[Authorize\]属性。

#### <a name="claims"></a>クレーム

クレームは、認証済みユーザーのプロパティを表す名前値のペアです。 たとえば、クレームとしてユーザーの従業員数を格納する可能性があります。 クレームは、承認ポリシーの一部として使用できます。 "EmployeeOnly"と呼ばれるポリシーを作成することがこの例で示すように"EmployeeNumber"と呼ばれるクレームの存在を必要とします。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

このポリシーを使用し、でした、 \[Authorize\]上記とれたコント ローラーとアクションを保護する属性。

#### <a name="securing-web-apis"></a>Web Api をセキュリティで保護します。

ほとんどの web Api には、トークン ベースの認証システムを実装する必要があります。 トークンの認証です。 ステートレスおよび拡張できるよう設計されています。 認証プロバイダーを使用する必要があります、トークン ベースの認証システムでクライアントを認証最初。 成功した場合、クライアントには、これは単に意味のある暗号化された文字列の文字のトークンが発行されます。 クライアントは、API に要求を発行する必要があります、ときに、このトークンを要求のヘッダーとして追加します。 サーバーは、要求ヘッダーについては、要求が完了する前に、トークンを検証します。 図 7-4 では、この手順を示します。

![TokenAuth](./media/image7-4.png)

**図 7-4 です。** Web Api のトークン ベース認証。

> ### <a name="references--security"></a>参照: セキュリティ
> - **ドキュメントのセキュリティの概要**  
> https://docs.microsoft.com/aspnet/core/security/
> - **ASP.NET Core アプリケーションで SSL を適用します。**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Identity の概要**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **承認の概要**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Azure App Service で API アプリの認証と承認**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>クライアントとの通信

ページの提供とに加えて web Api を使用してデータの要求に応答して、ASP.NET Core アプリケーションは接続されているクライアントと直接通信できます。 この送信の通信には、さまざまなトランスポート テクノロジ、最も一般的なされている Websocket を使用できます。 ASP.NET Core SignalR は、ライブラリをアプリケーションにリアルタイムのサーバーからクライアントへの通信機能の種類に容易です。 SignalR では、さまざまなトランスポート テクノロジ、Websocket を含むをサポートしており、多くの開発者から実装の詳細を抽象化します。

ASP.NET Core SignalR は現在開発中および ASP.NET Core の次のリリースで提供されます。 ただし、他の[ソース Websocket ライブラリを開きます](https://github.com/radu-matei/websocket-manager)は現在使用できません。

リアルタイムのクライアントとの通信、Websocket を直接またはその他の手法を使用してがさまざまなアプリケーション シナリオで役に立つかどうか。 次に、それらの例の一部を示します。

-   ライブ チャット ルーム アプリケーション

-   アプリケーションの監視

-   ジョブの進行状況の更新

-   通知

-   対話型のフォーム アプリケーション

アプリケーションにクライアントとの通信を構築するときに、2 つのコンポーネントは通常があります。

-   サーバー側の接続マネージャー (SignalR ハブ、WebSocketManager WebSocketHandler)

-   クライアント側ライブラリ

クライアントがブラウザー-モバイル アプリ、コンソール アプリに制限されて、他のネイティブ アプリは、SignalR/Websocket を使用しても通信できます。 次の簡単なプログラムには、WebSocketManager サンプル アプリケーションの一部として、コンソールにチャット アプリケーションに送信されるすべての内容がエコーされます。

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }
    
    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }
    
    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
```

発生する、アプリケーションがクライアント アプリケーションと直接通信およびリアルタイム コミュニケーションがアプリのユーザーを向上させるかどうかを検討する方法を検討してください。

> ### <a name="references--client-communication"></a>参照: クライアントとの通信
> - **ASP.NET Core SignalR**  
> <https://github.com/aspnet/SignalR>
> - **WebSocket マネージャー**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>ドメイン Driven Design: を適用することですか。

ドメインに基づくデザイン (DDD) に注目することを重視するソフトウェアの構築を柔軟な方法は、*ビジネス ドメイン*です。 通信およびビジネス ドメイン expert(s)、実際のシステムのしくみ、開発者に関連付けることができるユーザーとの対話に重点を置きます。 たとえば、株取引を処理するシステムを構築する場合、ドメインの専門家には、経験豊富な株式仲買可能性があります。 DDD 大規模で複雑なビジネス問題に対処するように設計されたされ、ほとんどの場合より小さいより簡単なアプリケーションでは、適切なとはへの投資を理解して、ドメインのモデリングが価値はありません。

(非技術的な利害関係者およびコントリビューターを含む)、チームが開発する必要があります DDD 手法に従ってソフトウェアを作成するときに、*ユビキタス言語*問題領域にします。 つまり、モデル化される実際の概念、ソフトウェアと同じと概念 (データベース テーブルなど) の保持に存在する構造体を同じ用語を使用してください。 したがって、ユビキタス言語で説明する概念の基礎を成して必要があります、*ドメイン モデル*です。

ドメイン モデルは、相互作用するか、システムの動作を表すオブジェクトで構成されます。 これらのオブジェクトは、次のカテゴリに分類されます可能性があります。

-   [エンティティ](http://deviq.com/entity/)id のスレッドを持つオブジェクトとして表示されています。 エンティティは、通常は、後で取得できるキーを使用して永続化に格納します。

-   [集計](http://deviq.com/aggregate-pattern/)、単位として永続化するオブジェクトのグループとして表示されています。

-   [オブジェクトの値](http://deviq.com/value-object/)、そのプロパティ値の合計に基づいて比較できる概念として表示されています。 たとえば、最初と最後の日付から成る DateRange です。

-   [ドメインのイベント](https://martinfowler.com/eaaDev/DomainEvent.html)システムで起こっているか、システムの他の部分に関心のあるものとして表示されています。

DDD ドメイン モデルがモデル内で複雑な動作をカプセル化する必要があることに注意してください。 エンティティ、具体的には、だけを実行することはできませんのプロパティのコレクション。 ドメイン モデルでは、動作がないし、システムの状態を表す単、ときと呼ばれます、 [anemic モデル](http://deviq.com/anemic-model/)が指定されて DDD のことをお勧めします。

これらの種類のモデルだけでなく DDD は通常、さまざまなパターンを使用します。

-   [リポジトリ](http://deviq.com/repository-pattern/)、永続化の詳細情報を抽出します。

-   [ファクトリ](https://en.wikipedia.org/wiki/Factory_method_pattern)、複雑なオブジェクトの作成をカプセル化するためです。

-   依存する動作の動作をトリガーから分離することをドメインで構成するイベント。

-   [サービス](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)インフラストラクチャの実装の詳細をカプセル化する複雑な動作、またはその両方です。

-   [コマンド](https://en.wikipedia.org/wiki/Command_pattern)を切り離すためには、コマンドを発行、およびそれ自体のコマンドを実行します。

-   [仕様](http://deviq.com/specification-pattern/)クエリの詳細をカプセル化するためです。

DDD では、疎結合、カプセル化、およびコードの単体テストを使用して簡単に検証できるようにする、先ほど説明したクリーンなアーキテクチャを使用することも推奨します。

### <a name="when-should-you-apply-ddd"></a>DDD するときに適用する必要があります。

DDD は重要なビジネス (だけ技術ではない) の複雑さに大規模なアプリケーションに最適です。 アプリケーションは、ドメインの専門家が認識する必要があります。 ドメイン モデル自体で、ビジネス ルールとだけを格納して、データ ストアからさまざまなレコードの現在の状態を取得する以外の相互作用を表すは重要な動作をする必要があります。

### <a name="when-shouldnt-you-apply-ddd"></a>DDD はならないときに適用します。

DDD には、モデリング、アーキテクチャ、および可能性がありますいないことを示しますより小さい、アプリケーションまたは CRUD (作成/読み取り/更新/削除) だけでは基本的にアプリケーションの通信への投資が含まれます。 DDD, の後、アプリケーションが動作を持たない anemic のモデルがドメインにあることを確認する場合は、実際のアプローチを再検討する必要があります。 アプリケーションでは、DDD, は必要はありませんか、データベース、またはユーザー インターフェイスではなく、ドメイン モデルでビジネス ロジックをカプセル化する、アプリケーションのリファクタリングのサポートが必要な場合があります。

アプリケーションのトランザクションまたはより複雑な領域だけのシンプルな CRUD またはアプリケーションの部分は読み取り専用ため DDD をのみを使用するハイブリッド アプローチになります。 たとえば、レポートを表示する、またはダッシュ ボードにデータを視覚化するデータのクエリを実行している場合、集計の制約がある必要はありません。 このような要件については、独立した、シンプルな読み取りモデルがまったく問題ありませんが。

> ### <a name="references--domain-driven-design"></a>– ドメイン ドリブン デザインの参照
> - **DDD 簡潔な表現 (StackOverflow Answer).**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>配置

ホストされる場所に関係なく、ASP.NET Core アプリケーションを展開するプロセスでは、いくつかの手順があります。 最初の手順が実行すると、アプリケーションを発行するには CLI コマンドを発行、dotnet を使用します。 アプリケーションをコンパイルし、すべての指定したフォルダに、アプリケーションの実行に必要なファイルの配置このされます。 Visual Studio から展開するときにこの手順は自動的を実行します。 発行フォルダーには、アプリケーションとその依存関係の .exe と .dll ファイルが含まれています。 自己完結型アプリケーションでは、.NET ランタイムのバージョンも含まれます。 ASP.NET Core アプリケーションには、構成ファイル、静的クライアント資産、および MVC ビューも含まれます。

ASP.NET Core アプリケーションはコンソール アプリケーション、サーバーが起動し、アプリケーション (またはサーバー) がクラッシュした場合の再起動と同時に起動する必要があります。 プロセス マネージャは、このプロセスの自動化に使用できます。 ASP.NET Core の最も一般的なプロセス マネージャーは、Nginx Linux および IIS での Apache や Windows 上の Windows サービスです。

プロセス マネージャーだけでなく Kestrel web サーバーでホストされる ASP.NET Core アプリケーションがリバース プロキシ サーバーを使用する必要があります。 リバース プロキシ サーバーでは、インターネットから HTTP 要求を受け取り、いくつかの予備処理後に Kestrel に転送します。 リバース プロキシ サーバーは、アプリケーションのセキュリティ レイヤーを提供し、(インターネットからのトラフィックに対して公開) のエッジ展開に必要な。 Kestrel は比較的新しいし、ある種の攻撃に対する防御がまだ提供していません。 Kestrel もサポートされていません、同じポートで複数のアプリケーションをホストしているため、同じポートと IP アドレスで複数のアプリケーションをホストできるようにしてホスト ヘッダーなどの手法を使用することはできません。

![インターネットに kestrel](./media/image7-5.png)

図 7-5 リバース プロキシ サーバーの背後に Kestrel でホストされる ASP.NET

もう 1 つのシナリオをリバース プロキシは役に立ちます SSL または HTTPS を使用して複数のアプリケーションをセキュリティで保護を開始します。 この例では、リバース プロキシのみは SSL を構成する必要があります。 リバース プロキシ サーバーと Kestrel 間の通信でした HTTP 上で行わ、図 7-6 に示すようにします。

![](./media/image7-6.png)

図 7-6 リバース プロキシの HTTPS で保護されたサーバーの背後にホストされている ASP.NET

急速に普及アプローチ、ASP.NET Core アプリケーションでホストし、ローカル ホストまたはクラウド ベースをホストするために、Azure にデプロイされた Docker コンテナーを開始します。 Docker コンテナーでは、Kestrel で実行されている、アプリケーション コードが含まれ、リバース プロキシ サーバーの背後に配置できるように上記のようにします。

Azure でアプリケーションをホストしている場合は、いくつかのサービスを提供する専用の仮想アプライアンスとして Microsoft Azure アプリケーション ゲートウェイを使用できます。 個々 のアプリケーションに対してリバース プロキシとして動作しているだけでなく、アプリケーション ゲートウェイは、次の機能を提供することも。

-   HTTP の負荷分散

-   SSL オフロード (インターネットのみに SSL)

-   エンド ツー エンドの SSL

-   複数のサイトのルーティング (1 つのアプリケーション ゲートウェイ上の最大 20 件までのサイトを統合)

-   Web アプリケーション ファイアウォール

-   Websocket のサポート

-   高度な診断

*章 10 での Azure のデプロイ オプションについて説明します。*

> ### <a name="references--deployment"></a>-展開の参照
> - **ホストと展開の概要**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **リバース プロキシで Kestrel を使用する場合**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Docker での ASP.NET Core アプリケーションのホスト**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Azure アプリケーション ゲートウェイの概要**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[前](一般的なのクライアント-側-web-technologies.md) [次へ] (work-with-data-in-asp-net-core-apps.md)
