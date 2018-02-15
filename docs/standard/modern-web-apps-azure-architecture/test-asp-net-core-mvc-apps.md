---
title: "ASP.NET Core MVC アプリをテストします。"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |ASP.NET Core MVC アプリをテストします。"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d23d0accc33fb8335dff602d6e1d6c8689972906
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="283cf-103">ASP.NET Core MVC アプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-103">Test ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="283cf-104">_「単体テスト、製品がたくない場合ほとんどの場合、お客様はありませんしたいか、テストして、。」_</span><span class="sxs-lookup"><span data-stu-id="283cf-104">_"If you don't like unit testing your product, most likely your customers won't like to test it, either."_</span></span>
> <span data-ttu-id="283cf-105">_-匿名-</span><span class="sxs-lookup"><span data-stu-id="283cf-105">_- Anonymous-</span></span>

## <a name="summary"></a><span data-ttu-id="283cf-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="283cf-106">Summary</span></span>

<span data-ttu-id="283cf-107">複雑なソフトウェアの変更に応答で予期しない方法で失敗します。</span><span class="sxs-lookup"><span data-stu-id="283cf-107">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="283cf-108">したがって、テストを変更した後が最も単純な (またはそれ以上、重要) のアプリケーションを除くすべての必要です。</span><span class="sxs-lookup"><span data-stu-id="283cf-108">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="283cf-109">手動テストは、ソフトウェアをテストする最も時間のかかる、最も信頼性の低いで最も負荷の高い方法です。</span><span class="sxs-lookup"><span data-stu-id="283cf-109">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="283cf-110">残念ながら、アプリケーションがあるテストが容易な設計されていません唯一の手段があることができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-110">Unfortunately, if applications are not designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="283cf-111">章 X で次のアーキテクチャの原則のレイアウトを記述されたアプリケーションは、単体テストが容易なをする必要があり、ASP.NET Core アプリケーションは自動統合および機能テストもサポートします。</span><span class="sxs-lookup"><span data-stu-id="283cf-111">Applications written following the architectural principles laid out in chapter X should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="283cf-112">自動テストの種類</span><span class="sxs-lookup"><span data-stu-id="283cf-112">Kinds of Automated Tests</span></span>

<span data-ttu-id="283cf-113">ソフトウェア アプリケーションの自動テストのさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="283cf-114">最も単純で、最下位レベルのテストは単体テストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="283cf-115">わずかに高いレベルでは、統合テストと機能のテストがあります。</span><span class="sxs-lookup"><span data-stu-id="283cf-115">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="283cf-116">UI テスト、ロード テスト、ストレス テスト、およびスモーク テストと同様に、テストの他の種類は、このドキュメントの範囲を超えています。</span><span class="sxs-lookup"><span data-stu-id="283cf-116">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="283cf-117">単体テスト</span><span class="sxs-lookup"><span data-stu-id="283cf-117">Unit Tests</span></span>

<span data-ttu-id="283cf-118">単体テストでは、1 つのアプリケーションのロジックの部分をテストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="283cf-119">いないものを一覧表示するいずれかにさらに記述できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="283cf-120">単体テストでは、方法は、コードの依存関係とはどのような統合をテストする – インフラストラクチャとの連携をテストしません。</span><span class="sxs-lookup"><span data-stu-id="283cf-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="283cf-121">単体テスト フレームワークで、コードを記述をテストしない – が動作するか、検索できる場合は、バグを報告およびコードの問題を回避するに想定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="283cf-122">単体テストは、メモリ内とプロセスで完全に実行されます。</span><span class="sxs-lookup"><span data-stu-id="283cf-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="283cf-123">ファイル システム、ネットワーク、またはデータベースと通信しません。</span><span class="sxs-lookup"><span data-stu-id="283cf-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="283cf-124">単体テストは、コードをテストのみあります。</span><span class="sxs-lookup"><span data-stu-id="283cf-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="283cf-125">外部依存関係のないと、コードの 1 つの単位のみをテストすることにより、単体テストは非常に短時間で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="283cf-126">したがって、数秒で何百もの単体テストのテスト スイートを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="283cf-127">それらで頻繁に実行、理想的には、共有されているソース管理リポジトリへとすべての自動ビルドで確実にすべてのプッシュする前に、ビルド サーバー。</span><span class="sxs-lookup"><span data-stu-id="283cf-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="283cf-128">統合テスト</span><span class="sxs-lookup"><span data-stu-id="283cf-128">Integration Tests</span></span>

<span data-ttu-id="283cf-129">データベースおよびファイル システムなど、インフラストラクチャと対話するコードをカプセル化することをお勧めはできますが、必要があります、コードの一部とことをテストする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="283cf-130">さらに、アプリケーションの依存関係が完全に解決されたときに期待どおりに、コードのレイヤーが対話することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="283cf-131">これは、統合テストの責任です。</span><span class="sxs-lookup"><span data-stu-id="283cf-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="283cf-132">統合テストでは、多くの場合、外部の依存関係とインフラストラクチャに依存している時間がかかりより、単体テストを設定することが困難である傾向があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="283cf-133">したがって、テストと単体テストの統合テストでの可能性があることをテストを避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-133">Thus, you should avoid testing things that could be tests with unit tests in integration tests.</span></span> <span data-ttu-id="283cf-134">単体テストを特定のシナリオをテストすることができる場合は、単体テストでテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="283cf-135">できない場合は、使用を検討して統合テストです。</span><span class="sxs-lookup"><span data-stu-id="283cf-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="283cf-136">複雑なセットアップと単体テストよりも teardown 手順、統合テストは必要多くの場合があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="283cf-137">たとえば、実際のデータベースに対する統合テストでは、各テストの実行前に、既知の状態にデータベースを戻す方法を必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="283cf-138">新しいテストが追加され、実稼働データベースのスキーマは進化、これらのテスト スクリプトがサイズと複雑さが増大する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="283cf-139">多くの大規模なシステムで、共有ソース管理への変更をチェックインする前に開発者のワークステーションで完全統合テスト スイートを実行する実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="283cf-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="283cf-140">このような場合は、ビルド サーバーで統合テストを実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="283cf-140">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="283cf-141">LocalFileImageService 実装クラスには、フェッチして、指定された id、特定のフォルダーからイメージ ファイルのバイト数を返すのためのロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="283cf-141">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

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

### <a name="functional-tests"></a><span data-ttu-id="283cf-142">機能テスト</span><span class="sxs-lookup"><span data-stu-id="283cf-142">Functional Tests</span></span>

<span data-ttu-id="283cf-143">統合テストは、システムの一部のコンポーネント正常に動作する同時ことを確認する、開発者の観点から書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="283cf-143">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="283cf-144">機能テストは、ユーザーの観点から書き込まれ、その要件に基づき、システムの正確性を確認します。</span><span class="sxs-lookup"><span data-stu-id="283cf-144">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="283cf-145">次の抜粋には、機能テスト、単体テストと比較してについて検討する方法についてわかりやすくが用意されています。</span><span class="sxs-lookup"><span data-stu-id="283cf-145">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="283cf-146">"システムの開発の回数は、家の構築にリンクします。</span><span class="sxs-lookup"><span data-stu-id="283cf-146">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="283cf-147">このとの類似性が非常に正しくないときに、単体テストと機能のテストの違いを理解するための目的で拡張おできます。</span><span class="sxs-lookup"><span data-stu-id="283cf-147">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="283cf-148">単体テストは、住宅の構築のサイトを訪問構築インスペクターに似ています。</span><span class="sxs-lookup"><span data-stu-id="283cf-148">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="283cf-149">彼は、家では、foundation、フレーム、電気を plumb およびなどのさまざまな内部システムで重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="283cf-149">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="283cf-150">彼はにより、家の部分が正常に動作し、安全に構築コードには、対応は (テスト)。</span><span class="sxs-lookup"><span data-stu-id="283cf-150">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="283cf-151">このシナリオでは機能テストは、この同じ構築サイトを訪問した住宅所有者に似ています。</span><span class="sxs-lookup"><span data-stu-id="283cf-151">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="283cf-152">彼は、内部システムが適切に動作する、建物インスペクターがこのタスクを実行するいると仮定します。</span><span class="sxs-lookup"><span data-stu-id="283cf-152">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="283cf-153">住宅所有者は、どのようなことがのようにこの家に重視されています。</span><span class="sxs-lookup"><span data-stu-id="283cf-153">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="283cf-154">快適なサイズを室、さまざまな、家がファミリのニーズに合わせて、windows の適切なスポット朝 sun をキャッチするには、彼は、家の外観に関係します。</span><span class="sxs-lookup"><span data-stu-id="283cf-154">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="283cf-155">家に対して、住宅機能テストの実行中はします。</span><span class="sxs-lookup"><span data-stu-id="283cf-155">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="283cf-156">ユーザーの観点を持ち、します。</span><span class="sxs-lookup"><span data-stu-id="283cf-156">He has the user's perspective.</span></span> <span data-ttu-id="283cf-157">ビルド インスペクターは、家で単体テストを実行しています。</span><span class="sxs-lookup"><span data-stu-id="283cf-157">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="283cf-158">彼は builder のパースペクティブです。"</span><span class="sxs-lookup"><span data-stu-id="283cf-158">He has the builder's perspective."</span></span>

<span data-ttu-id="283cf-159">ソース:[単体テストのテストと機能のテスト](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="283cf-159">Source: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="283cf-160">私は言うまでのフォント"2 つの方法で失敗する開発者は、: 正しくないことを構築するかが不適切な行為を構築する"。</span><span class="sxs-lookup"><span data-stu-id="283cf-160">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="283cf-161">単体テストでは、点右側を構築することを確認します。機能テストでは、正しいことを構築することを確認します。</span><span class="sxs-lookup"><span data-stu-id="283cf-161">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="283cf-162">機能テストは、システム レベルで動作するため、ある程度の UI オートメーションを必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-162">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="283cf-163">統合テストと同様に、機能は通常でテスト インフラストラクチャを同様のいくつかの種類。</span><span class="sxs-lookup"><span data-stu-id="283cf-163">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="283cf-164">これにより、低速と単位との統合のテストよりも不安定になります。</span><span class="sxs-lookup"><span data-stu-id="283cf-164">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="283cf-165">のみが必要に多くの機能テストようにユーザーが期待どおりに動作するシステムを保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-165">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="283cf-166">ピラミッドのテスト</span><span class="sxs-lookup"><span data-stu-id="283cf-166">Testing Pyramid</span></span>

<span data-ttu-id="283cf-167">Martin ファウラー書いています、テスト ピラミッド グラフ、図 9-1 にする例を示します。</span><span class="sxs-lookup"><span data-stu-id="283cf-167">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="283cf-168">図 9-1 ピラミッドのテスト</span><span class="sxs-lookup"><span data-stu-id="283cf-168">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="283cf-169">ピラミッド グラフ、およびそれらの相対的なサイズの異なるレイヤーでは、さまざまな種類のテストと数を記述してください、アプリケーションを表します。</span><span class="sxs-lookup"><span data-stu-id="283cf-169">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="283cf-170">ご覧のように、単体テストをさらに小さく、機能テストの層で、統合テストの小さい層でサポートされての大規模なベースにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="283cf-170">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="283cf-171">各レイヤー理想的のみがテストに下位層で適切に実行できることはできません。</span><span class="sxs-lookup"><span data-stu-id="283cf-171">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="283cf-172">特定のシナリオに必要なテストの種類を決定しようとしているときに、テスト、ピラミッドを注意してください。</span><span class="sxs-lookup"><span data-stu-id="283cf-172">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="283cf-173">テストの内容。</span><span class="sxs-lookup"><span data-stu-id="283cf-173">What to Test</span></span>

<span data-ttu-id="283cf-174">自動テストを作成した経験がある開発者にとっては一般的な問題は直近の見通しで何をテストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-174">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="283cf-175">適切な開始点では、条件ロジックをテストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-175">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="283cf-176">条件付きステートメントに基づいて、変更の動作を持つメソッドがある任意の場所 (if...else、スイッチなど) には、少なくともいくつかの特定の条件が正常に動作を確認するテストを考案することができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-176">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="283cf-177">場合は、コード エラー条件には、(エラーや例外的な結果) でアプリケーション エラーの発生した場合に想定どおりの動作を確認する (エラーなしで)、コードを「満足パス」を少なくとも 1 つのテストと"悲しい path"を少なくとも 1 つのテストを記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="283cf-177">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="283cf-178">最後に、コード カバレッジのようなメトリックに焦点を当てたするのではなく、テストが失敗する可能性のある点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="283cf-178">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="283cf-179">複数のコード カバレッジは通常より少ないです。</span><span class="sxs-lookup"><span data-stu-id="283cf-179">More code coverage is better than less, generally.</span></span> <span data-ttu-id="283cf-180">ただし、非常に複雑なビジネス クリティカルなメソッドには、さらに、いくつかのテストの記述は、通常時の自動テストのコード カバレッジ メトリックを向上させるためだけにプロパティのテストを記述するよりも効率的に使用します。</span><span class="sxs-lookup"><span data-stu-id="283cf-180">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="283cf-181">テスト プロジェクトの整理</span><span class="sxs-lookup"><span data-stu-id="283cf-181">Organizing Test Projects</span></span>

<span data-ttu-id="283cf-182">最適な動作が、テスト プロジェクトを編成できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-182">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="283cf-183">テスト (単体テスト、統合テスト) の型によって、(名前空間でのプロジェクト) をテストすることによってを分離することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="283cf-183">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="283cf-184">設計上の判断は、この分離は、1 つのテスト プロジェクトでは、または複数のテスト プロジェクト内のフォルダーで構成されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="283cf-184">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="283cf-185">1 つのプロジェクトは、最も簡単なが大きなプロジェクトの多くのテストやさまざまなテスト セットをより簡単に実行するために、複数の別のテスト プロジェクトをする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-185">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="283cf-186">多くのチームは、複数のプロジェクトを持つアプリケーションにまだを分解してこれらの各プロジェクトでのテストの種類に応じて場合に特にテスト プロジェクトの数が多いことができます発生するは、テスト プロジェクトに基づくテスト プロジェクトを編成します。</span><span class="sxs-lookup"><span data-stu-id="283cf-186">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="283cf-187">セキュリティ侵害の手法では、テスト対象プロジェクト (およびクラス) を示すためにテスト プロジェクト内にあるフォルダーで、アプリケーションあたりのテストの種類ごとの 1 つのプロジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="283cf-187">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="283cf-188">並列 'テスト' フォルダーの下の 'src' フォルダーの下のアプリケーション プロジェクトおよびアプリケーションのテストを整理する一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="283cf-188">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="283cf-189">この組織を便利にする場合は、Visual Studio で、一致するためのソリューション フォルダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-189">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="283cf-190">ソリューションのテスト組織を図 9-2</span><span class="sxs-lookup"><span data-stu-id="283cf-190">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="283cf-191">必要に応じていずれかのテスト フレームワークを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-191">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="283cf-192">XUnit framework でも、新機能で記述されたすべての ASP.NET Core と EF コア テストします。</span><span class="sxs-lookup"><span data-stu-id="283cf-192">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="283cf-193">図 9-3、または dotnet 新しい xunit を使用して、CLI からテンプレートを使用して Visual Studio では、xUnit テスト プロジェクトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-193">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="283cf-194">図 9-3 は、Visual Studio で、xUnit テスト プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="283cf-194">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="283cf-195">テストの名前を付ける</span><span class="sxs-lookup"><span data-stu-id="283cf-195">Test Naming</span></span>

<span data-ttu-id="283cf-196">各テストの実行内容を示す名前、一貫した方法で、テストの名前をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-196">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="283cf-197">優れた成功に必要だった 1 つは、名前テスト クラスに従ってクラスとメソッドをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="283cf-197">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="283cf-198">多くの小規模なテスト クラスでこの結果しますが、どのような各テストは、非常に明確になります。</span><span class="sxs-lookup"><span data-stu-id="283cf-198">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="283cf-199">クラスとメソッドをテストするを識別するように設定するテスト クラスの名前を持つテストされている動作を指定するテスト メソッドの名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-199">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="283cf-200">これには、想定される動作し、入力またはこの動作を生成する必要がある前提条件を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-200">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="283cf-201">一部の例のテスト名:</span><span class="sxs-lookup"><span data-stu-id="283cf-201">Some example test names:</span></span>

-   <span data-ttu-id="283cf-202">CatalogControllerGetImage.CallsImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="283cf-202">CatalogControllerGetImage.CallsImageServiceWithId</span></span>

-   <span data-ttu-id="283cf-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="283cf-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span></span>

-   <span data-ttu-id="283cf-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span><span class="sxs-lookup"><span data-stu-id="283cf-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span></span>

-   <span data-ttu-id="283cf-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="283cf-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span></span>

<span data-ttu-id="283cf-206">このアプローチのバリエーションは、各テスト クラス名「は」を終了し、時制を少し変更します。</span><span class="sxs-lookup"><span data-stu-id="283cf-206">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

-   <span data-ttu-id="283cf-207">CatalogControllerGetImage**必要があります**.**呼び出す**ImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="283cf-207">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span></span>

-   <span data-ttu-id="283cf-208">CatalogControllerGetImage**必要があります**.**ログ**WarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="283cf-208">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span></span>

<span data-ttu-id="283cf-209">一部のチームが明確になる 2 番目の名前付け方法を見つけるが少し詳細です。</span><span class="sxs-lookup"><span data-stu-id="283cf-209">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="283cf-210">いずれの場合は、どのようなケースが失敗した名前から明らかでは 1 つまたは複数のテストが失敗する場合、ようにテストの動作に関する洞察を提供する名前付け規則を使用する再試行してください。</span><span class="sxs-lookup"><span data-stu-id="283cf-210">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="283cf-211">これらを提供していない値テストの結果に表示される場合、名前付けするテスト漠然と、ControllerTests.Test1 などしないでください。</span><span class="sxs-lookup"><span data-stu-id="283cf-211">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="283cf-212">上に多数の小さなテスト クラスが生成するように 名前付け規則に従っている場合は、フォルダーおよび名前空間を使用して、テストをさらに整理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="283cf-212">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="283cf-213">図 9-4 は、いくつかのテスト プロジェクト内のフォルダーでテストを整理する 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="283cf-213">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="283cf-214">**図 9-4 です。**</span><span class="sxs-lookup"><span data-stu-id="283cf-214">**Figure 9-4.**</span></span> <span data-ttu-id="283cf-215">テスト対象のクラスに基づいてフォルダーで、テスト クラスを編成します。</span><span class="sxs-lookup"><span data-stu-id="283cf-215">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="283cf-216">もちろん、特定のアプリケーション クラスには多くのメソッドがテストされる (したがって多くのテスト クラス) 場合、ことは合理的でアプリケーションのクラスに対応するフォルダーを配置します。</span><span class="sxs-lookup"><span data-stu-id="283cf-216">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="283cf-217">この組織は、ファイルを別の場所のフォルダーに整理する方法と同じです。</span><span class="sxs-lookup"><span data-stu-id="283cf-217">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="283cf-218">3 つ以上ある場合、または 4 つの関連するその他の多くのファイルを含むフォルダーにファイル、お勧め多くの場合、独自のサブフォルダーに移動することです。</span><span class="sxs-lookup"><span data-stu-id="283cf-218">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="283cf-219">単体テストの ASP.NET Core アプリケーション</span><span class="sxs-lookup"><span data-stu-id="283cf-219">Unit Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="283cf-220">適切に設計された ASP.NET Core アプリケーションでは、ビジネス エンティティとのさまざまなサービスにほとんどの複雑さとビジネス ロジックをカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="283cf-220">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="283cf-221">ASP.NET Core MVC アプリ自体はコント ローラー、フィルター、viewmodels、ビュー、非常にいくつかの単体テストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-221">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="283cf-222">特定のアクションの機能の多くは、アクション メソッド自体の外側にします。</span><span class="sxs-lookup"><span data-stu-id="283cf-222">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="283cf-223">ルーティングが正常に動作をするかどうかをテストまたはグローバルのエラー処理は、単体テストを効果的に実行できません。</span><span class="sxs-lookup"><span data-stu-id="283cf-223">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="283cf-224">同様に、任意のフィルターを含むモデルの検証と認証および承認フィルターは、単体テストをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="283cf-224">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="283cf-225">これらの動作のソースでは、なしほとんどのアクション メソッドを小さな普通、それらを使用するコント ローラーの独立したテスト可能なサービスにその作業の大部分を委任することにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-225">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="283cf-226">場合によって、単体テストを順序で自分のコードをリファクターする必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-226">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="283cf-227">頻繁にこのエラーは、抽象化を識別して、抽象化をテストするには、コードにアクセスする依存関係の挿入を使用してコーディングよりインフラストラクチャに対して直接行われます。</span><span class="sxs-lookup"><span data-stu-id="283cf-227">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="283cf-228">たとえば、画像を表示するためには、この単純なアクション メソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="283cf-228">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="283cf-229">単体テストのこのメソッドは System.IO.File を使用して、ファイル システムからの読み取りをへの直接依存性によってが困難になります。</span><span class="sxs-lookup"><span data-stu-id="283cf-229">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="283cf-230">、期待どおりに動作が、統合テストは、実際のファイルでこれを確認するには、この動作をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-230">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="283cf-231">このメソッドのルートをテストすることはできません: については、これを行う機能テストとすぐに注意します。</span><span class="sxs-lookup"><span data-stu-id="283cf-231">It's worth noting you can't test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="283cf-232">単体テスト、ファイル システムの動作を直接できませんし、ルートをテストすることはできない場合がありますをテストするとは</span><span class="sxs-lookup"><span data-stu-id="283cf-232">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="283cf-233">単体テストを可能にするリファクタリング、した後は、いくつかのテスト_ケースおよびエラー処理など、不足している動作を検出可能性があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-233">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="283cf-234">メソッドは何のファイルが見つからないときにしますか。</span><span class="sxs-lookup"><span data-stu-id="283cf-234">What does the method do when a file isn't found?</span></span> <span data-ttu-id="283cf-235">何か。</span><span class="sxs-lookup"><span data-stu-id="283cf-235">What should it do?</span></span> <span data-ttu-id="283cf-236">この例では、リファクタリングされたメソッドは、これのようになります。</span><span class="sxs-lookup"><span data-stu-id="283cf-236">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="283cf-237">\_Logger と\_imageService は両方の依存関係として挿入します。</span><span class="sxs-lookup"><span data-stu-id="283cf-237">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="283cf-238">これで、アクション メソッドに渡されるのと同じ id が渡されるをテストすることができます、 \_imageService、および、FileResult の一部として返される結果のバイト。</span><span class="sxs-lookup"><span data-stu-id="283cf-238">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="283cf-239">テストすることも、想定どおりにエラーのログ記録が行われていることと、イメージが見つからない場合、NotFound 結果が返されることこれは重要なアプリケーションの動作 (いないだけ一時コードの問題の診断に追加する開発者は、) を想定します。</span><span class="sxs-lookup"><span data-stu-id="283cf-239">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="283cf-240">実際のファイル ロジックが別々 の実装のサービスに移動しが不足しているファイルの場合、アプリケーション固有の例外を返すが導入されました。</span><span class="sxs-lookup"><span data-stu-id="283cf-240">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="283cf-241">ことができますこの実装を個別にテスト、統合テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="283cf-241">You can test this implementation independently, using an integration test.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="283cf-242">テスト ASP.NET Core アプリケーションの統合</span><span class="sxs-lookup"><span data-stu-id="283cf-242">Integration Testing ASP.NET Core Apps</span></span>

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

<span data-ttu-id="283cf-243">このサービスは、コードが別のサービスにこれがリファクタリング前に、CatalogController と同様、IHostingEnvironment を使用します。</span><span class="sxs-lookup"><span data-stu-id="283cf-243">This service uses the IHostingEnvironment, just as the CatalogController code did before it was refactored into a separate service.</span></span> <span data-ttu-id="283cf-244">IHostingEnvironment を使用するコント ローラーのコードにのみ、このため、その依存関係が CatalogController のコンス トラクターから削除されました。</span><span class="sxs-lookup"><span data-stu-id="283cf-244">Since this was the only code in the controller that used IHostingEnvironment, that dependency was removed from CatalogController's constructor.</span></span>

<span data-ttu-id="283cf-245">このサービスが正常に動作するかをテストするには、既知のテストのイメージ ファイルを作成し、サービスが、特定の入力を指定することで返すことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-245">To test that this service works correctly, you need to create a known test image file and verify that the service returns it given a specific input.</span></span> <span data-ttu-id="283cf-246">モック オブジェクトを使用して、実際には (この場合、ファイル システムからの読み取り) をテストする動作にならない注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="283cf-246">You should take care not to use mock objects on the behavior you actually want to test (in this case, reading from the file system).</span></span> <span data-ttu-id="283cf-247">ただし、モック オブジェクトはまだ統合テストを設定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="283cf-247">However, mock objects may still be useful to set up integration tests.</span></span> <span data-ttu-id="283cf-248">この場合、その ContentRootPath が、テスト イメージに使用するフォルダーを指すように IHostingEnvironment を模擬表示できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-248">In this case, you can mock IHostingEnvironment so that its ContentRootPath points to the folder you're going to use for your test image.</span></span> <span data-ttu-id="283cf-249">完全な作業の統合テスト クラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="283cf-249">The complete working integration test class is shown here:</span></span>

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
> <span data-ttu-id="283cf-250">コードの大部分はテスト自体が非常に単純な – は、システムを構成し、テスト用インフラストラクチャ (この場合は、実際ファイルにディスクから読み取られる) を作成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="283cf-250">that the test itself is very simple – the bulk of the code is necessary to configure the system and create the testing infrastructure (in this case, an actual file to be read from disk).</span></span> <span data-ttu-id="283cf-251">これは、通常の統合テストは、通常、単体テストよりも複雑な設定作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="283cf-251">This is typical for integration tests, which often require more complex setup work than unit tests.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="283cf-252">機能のテスト ASP.NET Core アプリ</span><span class="sxs-lookup"><span data-stu-id="283cf-252">Functional Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="283cf-253">ASP.NET Core アプリケーションの場合、TestServer クラスは、機能テストの記述は比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="283cf-253">For ASP.NET Core applications, the TestServer class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="283cf-254">通常、アプリケーションを行う場合と同様、WebHostBuilder を使用して TestServer を構成します。</span><span class="sxs-lookup"><span data-stu-id="283cf-254">You configure a TestServer using a WebHostBuilder, just as you normally do for your application.</span></span> <span data-ttu-id="283cf-255">この WebHostBuilder は、アプリケーションの実際のホストと同じように構成する必要がありますが、テストしやすいようにすることの側面を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-255">This WebHostBuilder should be configured just like your application's real host, but you can modify any aspects of it that make testing easier.</span></span> <span data-ttu-id="283cf-256">ほとんどの場合を再利用する多くのテスト_ケースに対して同じ TestServer のため、再利用可能なメソッド (おそらく基底クラスの場合) 内にカプセル化することができます。</span><span class="sxs-lookup"><span data-stu-id="283cf-256">Most of the time, you'll reuse the same TestServer for many test cases, so you can encapsulate it in a reusable method (perhaps in a base class):</span></span>

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

<span data-ttu-id="283cf-257">GetProjectPath メソッドは、単に web プロジェクト (サンプル ソリューションのダウンロード) に物理パスを返します。</span><span class="sxs-lookup"><span data-stu-id="283cf-257">The GetProjectPath method simply returns the physical path to the web project (download sample solution).</span></span> <span data-ttu-id="283cf-258">WebHostBuilder ここでは単を指定、web アプリケーションのコンテンツのルートがここでは、実際の web アプリケーションを使用して同じスタートアップ クラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="283cf-258">The WebHostBuilder in this case simply specifies where the content root for the web application is, and references the same Startup class the real web application uses.</span></span> <span data-ttu-id="283cf-259">TestServer を操作するに要求を行うに System.Net.HttpClient の標準型を使用します。</span><span class="sxs-lookup"><span data-stu-id="283cf-259">To work with the TestServer, you use the standard System.Net.HttpClient type to make requests to it.</span></span> <span data-ttu-id="283cf-260">TestServer、TestServer で実行されているアプリケーションに要求する準備ができている構成済みクライアントを提供する、便利な CreateClient メソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="283cf-260">TestServer exposes a helpful CreateClient method that provides a pre-configured client that is ready to make requests to the application running on the TestServer.</span></span> <span data-ttu-id="283cf-261">このクライアントを使用する (保護された設定\_上記の基本のテストでのクライアント メンバー) ASP.NET Core アプリケーションの機能のテストを記述する場合。</span><span class="sxs-lookup"><span data-stu-id="283cf-261">You use this client (set to the protected \_client member on the base test above) when writing functional tests for your ASP.NET Core application:</span></span>

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

<span data-ttu-id="283cf-262">この機能のテストでは、すべてのミドルウェア、フィルター、バインダー、場所になることなどを含む完全な ASP.NET Core MVC アプリケーション スタックを実行します。</span><span class="sxs-lookup"><span data-stu-id="283cf-262">This functional test exercises the full ASP.NET Core MVC application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="283cf-263">あることを確認、特定のルート (「/カタログ/pic/1」) は、既知の場所にファイルの予期されたバイト配列を返します。</span><span class="sxs-lookup"><span data-stu-id="283cf-263">It verifies that a given route ("/catalog/pic/1") returns the expected byte array for a file in a known location.</span></span> <span data-ttu-id="283cf-264">実際の web サーバーをセットアップしなくても実行され、ため実際の web を使用してテストするためのサーバーが (たとえば、ファイアウォール設定の問題など) 発生する可能性がいる脆弱性の多くを回避できます。</span><span class="sxs-lookup"><span data-stu-id="283cf-264">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="283cf-265">TestServer に対して実行される機能のテスト通常統合と単体テストよりも遅くなりますが、テストの web サーバーにネットワーク経由で実行したテストよりもはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="283cf-265">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="283cf-266">[前](work-with-data-in-asp-net-core-apps.md) [次へ] (開発のプロセス-の-azure.md)</span><span class="sxs-lookup"><span data-stu-id="283cf-266">[Previous] (work-with-data-in-asp-net-core-apps.md) [Next] (development-process-for-azure.md)</span></span>
