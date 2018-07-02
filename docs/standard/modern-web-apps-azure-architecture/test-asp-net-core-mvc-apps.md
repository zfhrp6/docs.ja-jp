---
title: ASP.NET Core MVC アプリのテスト
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Core MVC アプリのテスト
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: b22e0e109144b4abd04cd4199cfdec244d8fa7af
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106503"
---
# <a name="test-aspnet-core-mvc-apps"></a>ASP.NET Core MVC アプリのテスト

> _"あなたが製品の単体テストを好まないと、あなたの顧客もテストを望まないでしょう。"_
>  _- 作者不明 -_

## <a name="summary"></a>まとめ

変更に対応するとき、複雑なソフトウェアには予想外のエラーが発生することがあります。 そのため、ほとんどの些細な (少なくとも重要性が最も低い) アプリケーションを除くすべてのアプリケーションで変更後のテストが必須となります。 手動テストはソフトウェアのテスト方法として最も遅く、信頼性がなく、高額です。 残念ながら、アプリケーションにテスト機能が付いていない場合、手動テストが唯一の手段になることがあります。 第 X 章に記載されているアーキテクチャ原則に基づいてアプリケーションが記述されている場合、単体テスト可能になるはずです。ASP.NET Core アプリケーションは、自動化統合と機能テストにも対応しています。

## <a name="kinds-of-automated-tests"></a>自動テストの種類

ソフトウェア アプリケーションでは、さまざまな種類のテストが自動化されています。 最も単純でレベルの低いテストが単体テストです。 少し上のレベルに統合テストや機能テストがあります。 UI テスト、ロード テスト、ストレス テスト、スモーク テストなど、他の種類のテストについては本書では取り上げません。

### <a name="unit-tests"></a>単体テスト

単体テストでは、アプリケーションのロジックの 1 つの部分をテストします。 単体テストに含まれない内容を列挙するして単体テストをさらに説明できます。 単体テストでは、依存関係やインフラストラクチャとのコードの連動をテストしません。それは統合テストの対象です。 単体テストでは、コード記述の基礎となるフレームワークをテストしません。フレームワークは動作すると想定してください。動作しないことが判明した場合、バグを提出するか、回避策となるコードを記述してください。 単体テストは、メモリとプロセスの中で完全に実行されます。 ファイル システム、ネットワーク、データベースとは通信しません。 単体テストはコードのみをテストします。

単体テストはコードの 1 単位のみをテストし、外部の依存関係が関与しないため、極めて短時間で実行されます。 そのため、何百という単体テストからなるテスト スイートを数秒で実行できます。 単体テストは頻繁に実行してください。共有ソース管理リポジトリにプッシュするたびに実行するのが理想です。ビルド サーバーで自動化ビルドを実行したときには、もちろん毎回実行してください。

### <a name="integration-tests"></a>統合テスト

データベースやファイル システムなど、インフラストラクチャとやり取りするコードをカプセル化することは良い考えですが、それでもカプセル化されないコードが残るので、それをテストすることになります。 また、アプリケーションの依存関係が完全に解決されるとき、コードの層が予想どおりにやり取りすることを検証してください。 これは統合テストの責務です。 統合テストには、単体テストより時間がかかり、設定が難しくなる傾向があります。外部の依存関係やインフラストラクチャに依存することが多いためです。 そのため、統合テストでは、単体テストでテストできるようなことはテストしないでください。 所与のシナリオを単体テストでテストできる場合、単体テストでテストしてください。 単体テストでテストできない場合、統合テストの利用を検討してください。

統合テストは多くの場合、セットアップと破棄のプロシージャが単体テストより複雑です。 たとえば、実際のデータベースに対して統合テストを行うとき、データベースをテスト実行前の既知の状態に戻す方法が必要になります。 新しいテストが追加され、運用データベース スキーマが拡大するにつれ、テスト スクリプトのサイズが増加し、より複雑になります。 大規模なシステムの多くでは、共有ソース管理の変更を調べる前に、開発者ワークステーションで完全な統合テスト スイートを実行することは実用的ではありません。 そのような場合、ビルド サーバーで統合テストを実行できることがあります。

実装クラス LocalFileImageService は、ID が与えられるとき、特定のフォルダーから画像ファイル データを取得し、返すロジックを実装します。

```csharp
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
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a>機能テスト

システムの一部のコンポーネントが正しく連動することを確認する目的で、統合テストは開発者の視点から記述されます。 機能テストはユーザーの視点から記述され、その要件に基づき、システムの正確性を検証します。 機能テストとは何か、単体テストとの比較で考えるとき、次の抜粋が類推として役に立ちます。

> "多くの場合、システムの開発は家の建築に例えられます。 この類推はまったく正しいというわけではありませんが、単体テストと機能テストの違いを理解する目的で拡大解釈できます。 単体テストは、建築調査官が家の建築現場を訪問する行為に似ています。 調査官は家のさまざまな内部システム、土台、骨組み、電気、配管を重点的に調べ、 家の各部分が正しく安全に機能すること、つまり、建築法規に準拠していることを確認 (テスト) します。 このシナリオにおける機能テストは、家主がこの同じ建築現場を訪問する行為に似ています。 家主は、内部システムが適切に動作し、建築調査官がその仕事を遂行しているものと想定し、 その家で生活することはどのような感じになるのかを重点的に確認します。 家はどのように見えるか、各部屋の大きさはちょうど良いか、家は家族の希望に合っているか、朝日を取り入れる場所に窓が取り付けられているかが重要となります。 家主は家に機能テストを実行します。 家主の視点はユーザーの視点です。 建築調査官は家に単体テストを実行します。 調査官の視点は開発者の視点です。"

出典: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (単体テストと機能テストの比較)

"開発者は 2 通りの失敗をします。間違った方法で開発することと間違ったものを開発することです。" というのは私の好きな表現です。 単体テストでは、正しい方法で開発していることを確認します。機能テストでは、正しいものを開発していることを確認します。

機能テストはシステム レベルで動作するため、ある程度の UI 自動化が必要になることがあります。 統合テストと同様に、通常、ある種のテスト インフラストラクチャとも連動します。 そのため単体テストや統合テストより遅くなり、不安定になります。 機能テストは、システムがユーザーの期待どおりに動作すると確信できるために必要な数だけ行ってください。

### <a name="testing-pyramid"></a>テストのピラミッド

Martin Fowler がテストをピラミッド図にしました。図 9-1 がその例です。

![](./media/image9-1.png)

図 9-1 テストのピラミッド

ピラミッドの各層はテストの種類を表し、その相対的な大きさはアプリケーションのために記述すべきテストの数を表します。 ご覧のように、単体テストの土台を大きくし、それより小さい統合テスト層が続き、さらに小さい機能テスト層が続くという構成が推奨されています。 各層には、理想的には、それより下の層では適切に実行できないテストのみを含めます。 特定のシナリオで必要とするテストの種類を決定するとき、このピラミッドを念頭に置いてください。

### <a name="what-to-test"></a>テストの内容。

自動化テストの記述経験がない開発者にとっては、何をテストするのかが共通の問題です。 理想的な出発点は条件ロジックをテストすることです。 条件文 (if-else、switch など) に基づいて変化する動作を持つメソッドが含まれる箇所で少なくとも 2、3 のテストが思い付くはずです。特定の条件に対して正しい動作を確認するテストです。 コードの条件に間違いがある場合、(エラーのない) コード経由で "Happy Path" のテストを少なくとも 1 つ記述し、(エラーがあるか、結果が不規則な) "Sad Path" のテストを少なくとも 1 つ記述し、エラーに直面したときにアプリケーションが予想どおりに動作することを確認することをお勧めします。 最後に、コード カバレッジなどの指標ではなく、エラーが起こりうるものに対するテストに集中的に取り組みます。 一般的に、カバレッジは少ないよりも多い方が良いとされます。 しかしながら、非常に複雑でビジネスクリティカルなメソッドのテストを 2、3 多く記述することは、テストのコード カバレッジ指標を改善するためだけに自動プロパティのテストを記述することより、通常、時間の使い方として優れています。

## <a name="organizing-test-projects"></a>テスト プロジェクトを整理する

テスト プロジェクトは、自分にとって最適に機能するように整理できます。 種類 (単体テストや統合テスト) やテスト内容 (プロジェクトや名前空間) に基づいてテストを分類することをお勧めします。 その分類が 1 つのテスト プロジェクト内のフォルダーで構成されるのか、複数のテスト プロジェクト内のフォルダーで構成されるのかは設計上の決定事項の 1 つです。 プロジェクトが 1 つであれば最も単純に整理されますが、大型のプロジェクトでさまざまなテストが含まれる場合、あるいはさまざまなテスト セットをより簡単に実行するには、複数のテスト プロジェクトが必要になることもあります。 多くのチームは、自分たちがテストしているプロジェクトに基づいてプロジェクトを整理します。アプリケーションに相当な数のプロジェクトが含まれるとき、テスト プロジェクトが大量になります。各プロジェクトに含まれるテストの種類に基づいてさらに細分化される場合は特に大量になります。 妥協案としては、テストの種類あたり、アプリケーションあたりプロジェクトを 1 つとし、テスト プロジェクトの中にフォルダーを置き、テスト対象のプロジェクト (とクラス) を示します。

一般的な方法は、‘src' フォルダーの下でアプリケーション プロジェクトを整理し、並列する ‘tests' フォルダーの下でアプリケーションのテスト プロジェクトを整理することです。 この整理方法が有効な場合、Visual Studio でこれに合ったソリューションを作成できます。

![](./media/image9-2.png)

図 9-2 ソリューションでテストを整理する

好きな方のテスト フレームワークを利用できます。 xUnit フレームワークは良好に動作し、ASP.NET Core と EF Core テストはすべてこれで記述されています。 図 9-3 のテンプレートを利用して Visual Studio で xUnit テスト プロジェクトを追加できます。あるいは、dotnet new xunit を利用し、CLI から追加できます。

![](./media/image9-3.png)

図 9-3 Visual Studio で xUnit テスト プロジェクトを追加する

### <a name="test-naming"></a>テストの命名規則

テストには一貫性のある名前を付けてください。それぞれのテストの内容を示す名前にします。 テストするクラスやメソッドに基づいてテスト クラスに名前を付けるという方法でうまく行ったことがあります。 結果的に小さなテスト クラスがたくさん作られますが、それぞれのテストが担当する内容は極めて明白になります。 テストするクラスやメソッドを識別するためにテスト クラスの名前を設定したら、テスト メソッド名を利用し、テストする動作を指定できます。 それにより、求められる動作と、その動作を生むための入力や前提が含まれます。 テスト名の例:

- CatalogControllerGetImage.CallsImageServiceWithId

- CatalogControllerGetImage.LogsWarningGivenImageMissingException

- CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

- CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

この方法のバリエーションとしては、それぞれのテスト クラスの名前の末尾を "Should" にして時制を少し変えます。

- CatalogControllerGetImage**Should**.**Call**ImageServiceWithId

- CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException

少しばかり冗長ですが、2 つ目の命名規則の方がわかりやすいと感じるチームもあるでしょう。 いずれにせよ、テストの動作がわかる命名規則を利用してください。テストが失敗したとき、何が失敗したのか名前から判断できます。 ControllerTests.Test1 のような曖昧な名前をテストに付けないでください。テスト結果に表示されたとき、何の有用性もありません。

小さなテスト クラスをたくさん生成する上記のような命名規則に従う場合、フォルダーや名前空間を利用し、テストをさらに整理することをお勧めします。 図 9-4 では、テスト プロジェクト内のフォルダー別にテストを整理している手法を確認できます。

![](./media/image9-4.png)

**図 9-4** テストされるクラスに基づき、テスト クラスをフォルダーで分けて整理します。

もちろん、特定のアプリケーション クラスにテスト対象メソッドがたくさんある (そのため、テスト クラスもたくさんある) 場合、アプリケーション クラスに対応するフォルダーにそれらを置く方が良いかもしれません。 その整理方法では、ファイルをどこか他の場所のフォルダーに入れて整理する場合と変わりません。 1 つのフォルダーの中に関連ファイルが 3 つもしくは 4 つ以上存在するとき、それぞれの下位フォルダーに移動させると便利なことがあります。

## <a name="unit-testing-aspnet-core-apps"></a>ASP.NET Core アプリを単体テストする

うまく設計された ASP.NET Core アプリケーションでは、ビジネス エンティティやさまざまなサービスにほとんどの複雑性やビジネス ロジックがカプセル化されます。 ASP.NET Core MVC アプリ自体とそのコントローラー、ビューモデル、ビューには単体テストはほとんど必要ありません。 アクションの機能性の多くは、アクション メソッド自体の外にあります。 ルーティングが正しく機能するかどうかのテストやグローバル エラーの処理は、単体テストで効果的に行うことができません。 同様に、モデル検証、認証、許可のフィルターなど、いかなるフィルターも単体テストできません。 動作の源がなければ、ほとんどのアクション メソッドは取るに足りないほど小さくなります。動作の源を利用するコントローラーに関係なくテストできるサービスに作業の大部分が委任されます。

場合によっては、単体テストする目的で、コードを改良する必要があります。 一般的には、インフラストラクチャに対して直接コード化せず、抽象化を特定し、依存関係挿入を利用し、テストするコードの抽象化にアクセスします。 たとえば、次の例をご覧ください。これは画像を表示する単純なアクション メソッドです。

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

このメソッドの単体テストは System.IO.File に直接依存することで難しくなります。System.IO.File はファイル システムから読み込むために利用されます。 この動作をテストし、予想どおり動くことを確認できますが、実際のファイルでそれをするのは統合テストです。 このメソッドのルートをテストできない点に注目してください。この後すぐ、機能テストでこれを行う方法について説明します。

ファイル システムの動作の単体テストが直接実行できないために、ルートをテストできない場合、どのようなテストが残されているのでしょうか? 改良して単体テストを可能にすると、テスト ケースや、エラー処理など、足りない動作が見つかることがあります。 ファイルが見つからないとき、メトリックは何を行うのでしょうか? 何をすべきでしょうか? この例では、改良後のメソッドは次のようになります。

```csharp
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

\_logger と \_imageService はいずれも依存関係として挿入されています。 これで、アクション メソッドに渡される同じ ID が \_imageService に渡されることと、結果的に生成されるバイトが FileResult の一部として返されることをテストできます。 エラー ログが予想どおり行われることと、画像が足りない場合、NotFound 結果が返されることもテストできます。これが重要なアプリケーション動作である (つまり、問題を診断するために開発者が追加した一時的なコードではない) ことを前提とします。 実際のファイル ロジックは別個の実装サービスに移動しており、ファイルが足りない場合にアプリケーション固有の例外を返すように拡大されています。 統合テストを利用して、この実装を非依存でテストできます。

## <a name="integration-testing-aspnet-core-apps"></a>ASP.NET Core Apps を統合テストする

このサービスでは、別個のサービスに改良される前の CatalogController コードと同様に、IHostingEnvironment が使用されます。 これがコントローラーで IHostingEnvironment を使用した唯一のコードであったため、その依存関係は CatalogController のコンストラクターから削除されました。

このサービスが正しく機能することをテストするには、既知のテスト画像ファイルを作成し、特定の入力後、サービスがそのファイルを正しく返すことを検証する必要があります。 実際にテストする動作 (この場合、ファイル システムから読み込むこと) にはモック オブジェクトを使用しないでください。 ただし、統合テストの設定でもモック オブジェクトは役に立ちます。 この事例では、その ContentRootPath がテスト画像に使用するフォルダーを指すように IHostingEnvironment をモックできます。 完璧に動作する統合テスト クラスは次のようになります。

```csharp
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
> テスト自体は非常に単純です。コードの大部分はシステムを構成し、テスト インフラストラクチャを作成するために必要です (この場合、ディスクから読み取る実際のファイル)。 これは、通常は単体テストより複雑な設定作業を必要とする統合テストの特徴です。

## <a name="functional-testing-aspnet-core-apps"></a>ASP.NET Core アプリを機能テストする

ASP.NET Core アプリケーションの場合、TestServer クラスを利用すると、機能テストをとても簡単に記述できます。 アプリケーションに普通に行うように、WebHostBuilder を利用して TestServer を構成します。 この WebHostBuilder はアプリケーションの実際のホストと同じように構成すべきですが、テストが楽にするあらゆる側面を改良できます。 ほとんどの場合、さまざまなテスト ケースで同じ TestServer を再利用します。再利用可能メソッドでカプセル化できます (おそらく基底クラスで)。

```csharp
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
        .UseStartup<Startup>();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath メソッドは、Web プロジェクトの物理パスを返します (サンプル ソリューションをダウンロードする)。 この場合の WebHostBuilder は Web アプリケーションのコンテンツ ルートがある場所を指定し、実際の Web アプリケーションが使用する同じ Startup クラスを参照します。 TestServer と連動させるには、標準の System.Net.HttpClient 型を利用し、TestServer に要求します。 TestServer は便利な CreateClient メソッドを公開します。このメソッドが提供する事前構成済みのクライアントは、TestServer で実行されているアプリケーションにいつでも要求を出せます。 ASP.NET Core アプリケーションのために機能テストを記述するとき、このクライアントを使用します (上記の基本テストで保護 \_client メンバーに設定されています)。

```csharp
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

この機能テストは、配置されているあらゆるミドルウェア、フィルター、バインダーなど、完全な ASP.NET Core MVC アプリケーション スタックを行使します。 既知の場所にあるファイルに対して予想されるバイト配列を所与のルート ("/catalog/pic/1") が返すことを検証します。 これは実際の Web サーバーを設定せずに行い、実際の Web サーバーを利用して不安定になることを回避します (ファイアウォール設定の問題など)。 TestServer に対して実行される機能テストは通常、統合テストや単体テストより遅くなりますが、テスト Web サーバーのネットワークで実行されるテストよりはるかに速くなります。

>[!div class="step-by-step"]
[前へ](work-with-data-in-asp-net-core-apps.md)
[次へ](development-process-for-azure.md)
