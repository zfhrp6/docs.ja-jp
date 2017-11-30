---
title: "ASP.NET Core MVC アプリをテストします。"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |ASP.NET Core MVC アプリをテストします。"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 4611ffa8334e124946e849306d3281b695830eb1
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="test-aspnet-core-mvc-apps"></a>ASP.NET Core MVC アプリをテストします。

> _「単体テスト、製品がたくない場合ほとんどの場合、お客様はありませんしたいか、テストして、。」_
> _-匿名-

## <a name="summary"></a>概要

複雑なソフトウェアの変更に応答で予期しない方法で失敗します。 したがって、テストを変更した後が最も単純な (またはそれ以上、重要) のアプリケーションを除くすべての必要です。 手動テストは、ソフトウェアをテストする最も時間のかかる、最も信頼性の低いで最も負荷の高い方法です。 残念ながら、アプリケーションがあるテストが容易な設計されていません唯一の手段があることができます。 章 X で次のアーキテクチャの原則のレイアウトを記述されたアプリケーションは、単体テストが容易なをする必要があり、ASP.NET Core アプリケーションは自動統合および機能テストもサポートします。

## <a name="kinds-of-automated-tests"></a>自動テストの種類

ソフトウェア アプリケーションの自動テストのさまざまな種類があります。 最も単純で、最下位レベルのテストは単体テストします。 わずかに高いレベルでは、統合テストと機能のテストがあります。 UI テスト、ロード テスト、ストレス テスト、およびスモーク テストと同様に、テストの他の種類は、このドキュメントの範囲を超えています。

### <a name="unit-tests"></a>単体テスト

単体テストでは、1 つのアプリケーションのロジックの部分をテストします。 いないものを一覧表示するいずれかにさらに記述できます。 単体テストでは、方法は、コードの依存関係とはどのような統合をテストする – インフラストラクチャとの連携をテストしません。 単体テスト フレームワークで、コードを記述をテストしない – が動作するか、検索できる場合は、バグを報告およびコードの問題を回避するに想定する必要があります。 単体テストは、メモリ内とプロセスで完全に実行されます。 ファイル システム、ネットワーク、またはデータベースと通信しません。 単体テストは、コードをテストのみあります。

外部依存関係のないと、コードの 1 つの単位のみをテストすることにより、単体テストは非常に短時間で実行する必要があります。 したがって、数秒で何百もの単体テストのテスト スイートを実行することができます。 それらで頻繁に実行、理想的には、共有されているソース管理リポジトリへとすべての自動ビルドで確実にすべてのプッシュする前に、ビルド サーバー。

### <a name="integration-tests"></a>統合テスト

データベースおよびファイル システムなど、インフラストラクチャと対話するコードをカプセル化することをお勧めはできますが、必要があります、コードの一部とことをテストする可能性があります。 さらに、アプリケーションの依存関係が完全に解決されたときに期待どおりに、コードのレイヤーが対話することを確認する必要があります。 これは、統合テストの責任です。 統合テストでは、多くの場合、外部の依存関係とインフラストラクチャに依存している時間がかかりより、単体テストを設定することが困難である傾向があります。 したがって、テストと単体テストの統合テストでの可能性があることをテストを避ける必要があります。 単体テストを特定のシナリオをテストすることができる場合は、単体テストでテストする必要があります。 できない場合は、使用を検討して統合テストです。

複雑なセットアップと単体テストよりも teardown 手順、統合テストは必要多くの場合があります。 たとえば、実際のデータベースに対する統合テストでは、各テストの実行前に、既知の状態にデータベースを戻す方法を必要があります。 新しいテストが追加され、実稼働データベースのスキーマは進化、これらのテスト スクリプトがサイズと複雑さが増大する傾向があります。 多くの大規模なシステムで、共有ソース管理への変更をチェックインする前に開発者のワークステーションで完全統合テスト スイートを実行する実用的ではありません。 このような場合は、ビルド サーバーで統合テストを実行することがあります。

LocalFileImageService 実装クラスには、フェッチして、指定された id、特定のフォルダーからイメージ ファイルのバイト数を返すのためのロジックを実装します。

```cs
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
```

### <a name="functional-tests"></a>機能テスト

統合テストは、システムの一部のコンポーネント正常に動作する同時ことを確認する、開発者の観点から書き込まれます。 機能テストは、ユーザーの観点から書き込まれ、その要件に基づき、システムの正確性を確認します。 次の抜粋には、機能テスト、単体テストと比較してについて検討する方法についてわかりやすくが用意されています。

> "システムの開発の回数は、家の構築にリンクします。 このとの類似性が非常に正しくないときに、単体テストと機能のテストの違いを理解するための目的で拡張おできます。 単体テストは、住宅の構築のサイトを訪問構築インスペクターに似ています。 彼は、家では、foundation、フレーム、電気を plumb およびなどのさまざまな内部システムで重点を置きます。 彼はにより、家の部分が正常に動作し、安全に構築コードには、対応は (テスト)。 このシナリオでは機能テストは、この同じ構築サイトを訪問した住宅所有者に似ています。 彼は、内部システムが適切に動作する、建物インスペクターがこのタスクを実行するいると仮定します。 住宅所有者は、どのようなことがのようにこの家に重視されています。 快適なサイズを室、さまざまな、家がファミリのニーズに合わせて、windows の適切なスポット朝 sun をキャッチするには、彼は、家の外観に関係します。 家に対して、住宅機能テストの実行中はします。 ユーザーの観点を持ち、します。 ビルド インスペクターは、家で単体テストを実行しています。 彼は builder のパースペクティブです。"

ソース:[単体テストのテストと機能のテスト](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

私は言うまでのフォント"2 つの方法で失敗する開発者は、: 正しくないことを構築するかが不適切な行為を構築する"。 単体テストでは、点右側を構築することを確認します。機能テストでは、正しいことを構築することを確認します。

機能テストは、システム レベルで動作するため、ある程度の UI オートメーションを必要な場合があります。 統合テストと同様に、機能は通常でテスト インフラストラクチャを同様のいくつかの種類。 これにより、低速と単位との統合のテストよりも不安定になります。 のみが必要に多くの機能テストようにユーザーが期待どおりに動作するシステムを保証する必要があります。

### <a name="testing-pyramid"></a>ピラミッドのテスト

Martin ファウラー書いています、テスト ピラミッド グラフ、図 9-1 にする例を示します。

![](./media/image9-1.png)

図 9-1 ピラミッドのテスト

ピラミッド グラフ、およびそれらの相対的なサイズの異なるレイヤーでは、さまざまな種類のテストと数を記述してください、アプリケーションを表します。 ご覧のように、単体テストをさらに小さく、機能テストの層で、統合テストの小さい層でサポートされての大規模なベースにお勧めします。 各レイヤー理想的のみがテストに下位層で適切に実行できることはできません。 特定のシナリオに必要なテストの種類を決定しようとしているときに、テスト、ピラミッドを注意してください。

### <a name="what-to-test"></a>テストの内容。

自動テストを作成した経験がある開発者にとっては一般的な問題は直近の見通しで何をテストします。 適切な開始点では、条件ロジックをテストします。 条件付きステートメントに基づいて、変更の動作を持つメソッドがある任意の場所 (if...else、スイッチなど) には、少なくともいくつかの特定の条件が正常に動作を確認するテストを考案することができます。 場合は、コード エラー条件には、(エラーや例外的な結果) でアプリケーション エラーの発生した場合に想定どおりの動作を確認する (エラーなしで)、コードを「満足パス」を少なくとも 1 つのテストと"悲しい path"を少なくとも 1 つのテストを記述することをお勧めします。 最後に、コード カバレッジのようなメトリックに焦点を当てたするのではなく、テストが失敗する可能性のある点に注目してください。 複数のコード カバレッジは通常より少ないです。 ただし、非常に複雑なビジネス クリティカルなメソッドには、さらに、いくつかのテストの記述は、通常時の自動テストのコード カバレッジ メトリックを向上させるためだけにプロパティのテストを記述するよりも効率的に使用します。

## <a name="organizing-test-projects"></a>テスト プロジェクトの整理

最適な動作が、テスト プロジェクトを編成できます。 テスト (単体テスト、統合テスト) の型によって、(名前空間でのプロジェクト) をテストすることによってを分離することをお勧めします。 設計上の判断は、この分離は、1 つのテスト プロジェクトでは、または複数のテスト プロジェクト内のフォルダーで構成されるかどうか。 1 つのプロジェクトは、最も簡単なが大きなプロジェクトの多くのテストやさまざまなテスト セットをより簡単に実行するために、複数の別のテスト プロジェクトをする可能性があります。 多くのチームは、複数のプロジェクトを持つアプリケーションにまだを分解してこれらの各プロジェクトでのテストの種類に応じて場合に特にテスト プロジェクトの数が多いことができます発生するは、テスト プロジェクトに基づくテスト プロジェクトを編成します。 セキュリティ侵害の手法では、テスト対象プロジェクト (およびクラス) を示すためにテスト プロジェクト内にあるフォルダーで、アプリケーションあたりのテストの種類ごとの 1 つのプロジェクトがあります。

並列 'テスト' フォルダーの下の 'src' フォルダーの下のアプリケーション プロジェクトおよびアプリケーションのテストを整理する一般的な方法です。 この組織を便利にする場合は、Visual Studio で、一致するためのソリューション フォルダーを作成できます。

![](./media/image9-2.png)

ソリューションのテスト組織を図 9-2

必要に応じていずれかのテスト フレームワークを使用することができます。 XUnit framework でも、新機能で記述されたすべての ASP.NET Core と EF コア テストします。 図 9-3、または dotnet 新しい xunit を使用して、CLI からテンプレートを使用して Visual Studio では、xUnit テスト プロジェクトを追加できます。

![](./media/image9-3.png)

図 9-3 は、Visual Studio で、xUnit テスト プロジェクトを追加します。

### <a name="test-naming"></a>テストの名前を付ける

各テストの実行内容を示す名前、一貫した方法で、テストの名前をする必要があります。 優れた成功に必要だった 1 つは、名前テスト クラスに従ってクラスとメソッドをテストすることです。 多くの小規模なテスト クラスでこの結果しますが、どのような各テストは、非常に明確になります。 クラスとメソッドをテストするを識別するように設定するテスト クラスの名前を持つテストされている動作を指定するテスト メソッドの名前を使用できます。 これには、想定される動作し、入力またはこの動作を生成する必要がある前提条件を含める必要があります。 一部の例のテスト名:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

このアプローチのバリエーションは、各テスト クラス名「は」を終了し、時制を少し変更します。

-   CatalogControllerGetImage**必要があります**.**呼び出す**ImageServiceWithId

-   CatalogControllerGetImage**必要があります**.**ログ**WarningGivenImageMissingException

一部のチームが明確になる 2 番目の名前付け方法を見つけるが少し詳細です。 いずれの場合は、どのようなケースが失敗した名前から明らかでは 1 つまたは複数のテストが失敗する場合、ようにテストの動作に関する洞察を提供する名前付け規則を使用する再試行してください。 これらを提供していない値テストの結果に表示される場合、名前付けするテスト漠然と、ControllerTests.Test1 などしないでください。

上に多数の小さなテスト クラスが生成するように 名前付け規則に従っている場合は、フォルダーおよび名前空間を使用して、テストをさらに整理することをお勧めします。 図 9-4 は、いくつかのテスト プロジェクト内のフォルダーでテストを整理する 1 つの方法を示しています。

![](./media/image9-4.png)

**図 9-4 です。** テスト対象のクラスに基づいてフォルダーで、テスト クラスを編成します。

もちろん、特定のアプリケーション クラスには多くのメソッドがテストされる (したがって多くのテスト クラス) 場合、ことは合理的でアプリケーションのクラスに対応するフォルダーを配置します。 この組織は、ファイルを別の場所のフォルダーに整理する方法と同じです。 3 つ以上ある場合、または 4 つの関連するその他の多くのファイルを含むフォルダーにファイル、お勧め多くの場合、独自のサブフォルダーに移動することです。

## <a name="unit-testing-aspnet-core-apps"></a>単体テストの ASP.NET Core アプリケーション

適切に設計された ASP.NET Core アプリケーションでは、ビジネス エンティティとのさまざまなサービスにほとんどの複雑さとビジネス ロジックをカプセル化されます。 ASP.NET Core MVC アプリ自体はコント ローラー、フィルター、viewmodels、ビュー、非常にいくつかの単体テストする必要があります。 特定のアクションの機能の多くは、アクション メソッド自体の外側にします。 ルーティングが正常に動作をするかどうかをテストまたはグローバルのエラー処理は、単体テストを効果的に実行できません。 同様に、任意のフィルターを含むモデルの検証と認証および承認フィルターは、単体テストをすることはできません。 これらの動作のソースでは、なしほとんどのアクション メソッドを小さな普通、それらを使用するコント ローラーの独立したテスト可能なサービスにその作業の大部分を委任することにする必要があります。

場合によって、単体テストを順序で自分のコードをリファクターする必要があります。 頻繁にこのエラーは、抽象化を識別して、抽象化をテストするには、コードにアクセスする依存関係の挿入を使用してコーディングよりインフラストラクチャに対して直接行われます。 たとえば、画像を表示するためには、この単純なアクション メソッドがあるとします。

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

単体テストのこのメソッドは System.IO.File を使用して、ファイル システムからの読み取りをへの直接依存性によってが困難になります。 、期待どおりに動作が、統合テストは、実際のファイルでこれを確認するには、この動作をテストすることができます。 このメソッドのルートをテストすることはできません: については、これを行う機能テストとすぐに注意します。

単体テスト、ファイル システムの動作を直接できませんし、ルートをテストすることはできない場合がありますをテストするとは 単体テストを可能にするリファクタリング、した後は、いくつかのテスト_ケースおよびエラー処理など、不足している動作を検出可能性があります。 メソッドは何のファイルが見つからないときにしますか。 何か。 この例では、リファクタリングされたメソッドは、これのようになります。

```cs
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

\_Logger と\_imageService は両方の依存関係として挿入します。 これで、アクション メソッドに渡されるのと同じ id が渡されるをテストすることができます、 \_imageService、および、FileResult の一部として返される結果のバイト。 テストすることも、想定どおりにエラーのログ記録が行われていることと、イメージが見つからない場合、NotFound 結果が返されることこれは重要なアプリケーションの動作 (いないだけ一時コードの問題の診断に追加する開発者は、) を想定します。 実際のファイル ロジックが別々 の実装のサービスに移動しが不足しているファイルの場合、アプリケーション固有の例外を返すが導入されました。 ことができますこの実装を個別にテスト、統合テストを使用します。

## <a name="integration-testing-aspnet-core-apps"></a>テスト ASP.NET Core アプリケーションの統合

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

このサービスは、コードが別のサービスにこれがリファクタリング前に、CatalogController と同様、IHostingEnvironment を使用します。 IHostingEnvironment を使用するコント ローラーのコードにのみ、このため、その依存関係が CatalogController のコンス トラクターから削除されました。

このサービスが正常に動作するかをテストするには、既知のテストのイメージ ファイルを作成し、サービスが、特定の入力を指定することで返すことを確認する必要があります。 モック オブジェクトを使用して、実際には (この場合、ファイル システムからの読み取り) をテストする動作にならない注意する必要があります。 ただし、モック オブジェクトはまだ統合テストを設定すると便利です。 この場合、その ContentRootPath が、テスト イメージに使用するフォルダーを指すように IHostingEnvironment を模擬表示できます。 完全な作業の統合テスト クラスを次に示します。

```cs
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";
    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }
    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
            var location = System.Reflection.Assembly.GetEntryAssembly().Location;
            return Path.GetDirectoryName(location);
        }

        [Fact]
        public void ReturnsFileContentResultGivenValidId()
        {
            var fileService = new LocalFileImageService(_mockEnvironment.Object);
            var result = fileService.GetImageBytesById(_testImageId);
            Assert.Equal(_testBytes, result);
        }
    }
```

> [!NOTE]
> コードの大部分はテスト自体が非常に単純な – は、システムを構成し、テスト用インフラストラクチャ (この場合は、実際ファイルにディスクから読み取られる) を作成するために必要です。 これは、通常の統合テストは、通常、単体テストよりも複雑な設定作業が必要です。

## <a name="functional-testing-aspnet-core-apps"></a>機能のテスト ASP.NET Core アプリ

ASP.NET Core アプリケーションの場合、TestServer クラスは、機能テストの記述は比較的簡単です。 通常、アプリケーションを行う場合と同様、WebHostBuilder を使用して TestServer を構成します。 この WebHostBuilder は、アプリケーションの実際のホストと同じように構成する必要がありますが、テストしやすいようにすることの側面を変更することができます。 ほとんどの場合を再利用する多くのテスト_ケースに対して同じ TestServer のため、再利用可能なメソッド (おそらく基底クラスの場合) 内にカプセル化することができます。

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath メソッドは、単に web プロジェクト (サンプル ソリューションのダウンロード) に物理パスを返します。 WebHostBuilder ここでは単を指定、web アプリケーションのコンテンツのルートがここでは、実際の web アプリケーションを使用して同じスタートアップ クラスを参照します。 TestServer を操作するに要求を行うに System.Net.HttpClient の標準型を使用します。 TestServer、TestServer で実行されているアプリケーションに要求する準備ができている構成済みクライアントを提供する、便利な CreateClient メソッドを公開します。 このクライアントを使用する (保護された設定\_上記の基本のテストでのクライアント メンバー) ASP.NET Core アプリケーションの機能のテストを記述する場合。

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

この機能のテストでは、すべてのミドルウェア、フィルター、バインダー、場所になることなどを含む完全な ASP.NET Core MVC アプリケーション スタックを実行します。 あることを確認、特定のルート (「/カタログ/pic/1」) は、既知の場所にファイルの予期されたバイト配列を返します。 実際の web サーバーをセットアップしなくても実行され、ため実際の web を使用してテストするためのサーバーが (たとえば、ファイアウォール設定の問題など) 発生する可能性がいる脆弱性の多くを回避できます。 TestServer に対して実行される機能のテスト通常統合と単体テストよりも遅くなりますが、テストの web サーバーにネットワーク経由で実行したテストよりもはるかに高速です。

>[!div class="step-by-step"]
[前](work-with-data-in-asp-net-core-apps.md) [次へ] (開発のプロセス-の-azure.md)
