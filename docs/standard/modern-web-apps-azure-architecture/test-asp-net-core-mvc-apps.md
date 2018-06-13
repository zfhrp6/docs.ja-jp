---
title: ASP.NET Core MVC アプリのテスト
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Core MVC アプリのテスト
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: 7b4bcb1c39ddbbc104820558532b03bc9341804e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592562"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="d0aaa-103">ASP.NET Core MVC アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="d0aaa-103">Test ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="d0aaa-104">_"あなたが製品の単体テストを好まないと、あなたの顧客もテストを望まないでしょう。"_</span><span class="sxs-lookup"><span data-stu-id="d0aaa-104">_"If you don't like unit testing your product, most likely your customers won't like to test it, either."_</span></span>
> <span data-ttu-id="d0aaa-105">_- 匿名-</span><span class="sxs-lookup"><span data-stu-id="d0aaa-105">_- Anonymous-</span></span>

## <a name="summary"></a><span data-ttu-id="d0aaa-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="d0aaa-106">Summary</span></span>

<span data-ttu-id="d0aaa-107">変更に対応するとき、複雑なソフトウェアには予想外のエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-107">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="d0aaa-108">そのため、ほとんどの些細な (少なくとも重要性が最も低い) アプリケーションを除くすべてのアプリケーションで変更後のテストが必須となります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-108">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="d0aaa-109">手動テストはソフトウェアのテスト方法として最も遅く、信頼性がなく、高額です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-109">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="d0aaa-110">残念ながら、アプリケーションにテスト機能が付いていない場合、手動テストが唯一の手段になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-110">Unfortunately, if applications are not designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="d0aaa-111">第 X 章に記載されているアーキテクチャ原則に基づいてアプリケーションが記述されている場合、単体テスト可能になるはずです。ASP.NET Core アプリケーションは、自動化統合と機能テストにも対応しています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-111">Applications written following the architectural principles laid out in chapter X should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="d0aaa-112">自動テストの種類</span><span class="sxs-lookup"><span data-stu-id="d0aaa-112">Kinds of Automated Tests</span></span>

<span data-ttu-id="d0aaa-113">ソフトウェア アプリケーションでは、さまざまな種類のテストが自動化されています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="d0aaa-114">最も単純でレベルの低いテストが単体テストです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="d0aaa-115">少し上のレベルに統合テストや機能テストがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-115">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="d0aaa-116">UI テスト、ロード テスト、ストレス テスト、スモーク テストなど、他の種類のテストについては本書では取り上げません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-116">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="d0aaa-117">単体テスト</span><span class="sxs-lookup"><span data-stu-id="d0aaa-117">Unit Tests</span></span>

<span data-ttu-id="d0aaa-118">単体テストでは、アプリケーションのロジックの 1 つの部分をテストします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="d0aaa-119">単体テストに含まれない内容を列挙するして単体テストをさらに説明できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="d0aaa-120">単体テストでは、依存関係やインフラストラクチャとのコードの連動をテストしません。それは統合テストの対象です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="d0aaa-121">単体テストでは、コード記述の基礎となるフレームワークをテストしません。フレームワークは動作すると想定してください。動作しないことが判明した場合、バグを提出するか、回避策となるコードを記述してください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="d0aaa-122">単体テストは、メモリとプロセスの中で完全に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="d0aaa-123">ファイル システム、ネットワーク、データベースとは通信しません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="d0aaa-124">単体テストはコードのみをテストします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="d0aaa-125">単体テストはコードの 1 単位のみをテストし、外部の依存関係が関与しないため、極めて短時間で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="d0aaa-126">そのため、何百という単体テストからなるテスト スイートを数秒で実行できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="d0aaa-127">単体テストは頻繁に実行してください。共有ソース管理リポジトリにプッシュするたびに実行するのが理想です。ビルド サーバーで自動化ビルドを実行したときには、もちろん毎回実行してください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="d0aaa-128">統合テスト</span><span class="sxs-lookup"><span data-stu-id="d0aaa-128">Integration Tests</span></span>

<span data-ttu-id="d0aaa-129">データベースやファイル システムなど、インフラストラクチャとやり取りするコードをカプセル化することは良い考えですが、それでもカプセル化されないコードが残るので、それをテストすることになります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="d0aaa-130">また、アプリケーションの依存関係が完全に解決されるとき、コードの層が予想どおりにやり取りすることを検証してください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="d0aaa-131">これは統合テストの責務です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="d0aaa-132">統合テストには、単体テストより時間がかかり、設定が難しくなる傾向があります。外部の依存関係やインフラストラクチャに依存することが多いためです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="d0aaa-133">そのため、統合テストでは、単体テストでテストできるようなことはテストしないでください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-133">Thus, you should avoid testing things that could be tests with unit tests in integration tests.</span></span> <span data-ttu-id="d0aaa-134">所与のシナリオを単体テストでテストできる場合、単体テストでテストしてください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="d0aaa-135">単体テストでテストできない場合、統合テストの利用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="d0aaa-136">統合テストは多くの場合、セットアップと破棄のプロシージャが単体テストより複雑です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="d0aaa-137">たとえば、実際のデータベースに対して統合テストを行うとき、データベースをテスト実行前の既知の状態に戻す方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="d0aaa-138">新しいテストが追加され、運用データベース スキーマが拡大するにつれ、テスト スクリプトのサイズが増加し、より複雑になります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="d0aaa-139">大規模なシステムの多くでは、共有ソース管理の変更を調べる前に、開発者ワークステーションで完全な統合テスト スイートを実行することは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="d0aaa-140">そのような場合、ビルド サーバーで統合テストを実行できることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-140">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="d0aaa-141">実装クラス LocalFileImageService は、ID が与えられるとき、特定のフォルダーから画像ファイル データを取得し、返すロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-141">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

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

### <a name="functional-tests"></a><span data-ttu-id="d0aaa-142">機能テスト</span><span class="sxs-lookup"><span data-stu-id="d0aaa-142">Functional Tests</span></span>

<span data-ttu-id="d0aaa-143">システムの一部のコンポーネントが正しく連動することを確認する目的で、統合テストは開発者の視点から記述されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-143">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="d0aaa-144">機能テストはユーザーの視点から記述され、その要件に基づき、システムの正確性を検証します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-144">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="d0aaa-145">機能テストとは何か、単体テストとの比較で考えるとき、次の抜粋が類推として役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-145">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="d0aaa-146">"多くの場合、システムの開発は家の建築に例えられます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-146">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="d0aaa-147">この類推はまったく正しいというわけではありませんが、単体テストと機能テストの違いを理解する目的で拡大解釈できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-147">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="d0aaa-148">単体テストは、建築調査官が家の建築現場を訪問する行為に似ています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-148">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="d0aaa-149">調査官は家のさまざまな内部システム、土台、骨組み、電気、配管を重点的に調べ、</span><span class="sxs-lookup"><span data-stu-id="d0aaa-149">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="d0aaa-150">家の各部分が正しく安全に機能すること、つまり、建築法規に準拠していることを確認 (テスト) します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-150">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="d0aaa-151">このシナリオにおける機能テストは、家主がこの同じ建築現場を訪問する行為に似ています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-151">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="d0aaa-152">家主は、内部システムが適切に動作し、建築調査官がその仕事を遂行しているものと想定し、</span><span class="sxs-lookup"><span data-stu-id="d0aaa-152">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="d0aaa-153">その家で生活することはどのような感じになるのかを重点的に確認します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-153">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="d0aaa-154">家はどのように見えるか、各部屋の大きさはちょうど良いか、家は家族の希望に合っているか、朝日を取り入れる場所に窓が取り付けられているかが重要となります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-154">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="d0aaa-155">家主は家に機能テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-155">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="d0aaa-156">家主の視点はユーザーの視点です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-156">He has the user's perspective.</span></span> <span data-ttu-id="d0aaa-157">建築調査官は家に単体テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-157">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="d0aaa-158">調査官の視点は開発者の視点です。"</span><span class="sxs-lookup"><span data-stu-id="d0aaa-158">He has the builder's perspective."</span></span>

<span data-ttu-id="d0aaa-159">出典: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (単体テストと機能テストの比較)</span><span class="sxs-lookup"><span data-stu-id="d0aaa-159">Source: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="d0aaa-160">"開発者は 2 通りの失敗をします。間違った方法で開発することと間違ったものを開発することです。" というのは私の好きな表現です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-160">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="d0aaa-161">単体テストでは、正しい方法で開発していることを確認します。機能テストでは、正しいものを開発していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-161">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="d0aaa-162">機能テストはシステム レベルで動作するため、ある程度の UI 自動化が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-162">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="d0aaa-163">統合テストと同様に、通常、ある種のテスト インフラストラクチャとも連動します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-163">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="d0aaa-164">そのため単体テストや統合テストより遅くなり、不安定になります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-164">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="d0aaa-165">機能テストは、システムがユーザーの期待どおりに動作すると確信できるために必要な数だけ行ってください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-165">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="d0aaa-166">テストのピラミッド</span><span class="sxs-lookup"><span data-stu-id="d0aaa-166">Testing Pyramid</span></span>

<span data-ttu-id="d0aaa-167">Martin Fowler がテストをピラミッド図にしました。図 9-1 がその例です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-167">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="d0aaa-168">図 9-1 テストのピラミッド</span><span class="sxs-lookup"><span data-stu-id="d0aaa-168">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="d0aaa-169">ピラミッドの各層はテストの種類を表し、その相対的な大きさはアプリケーションのために記述すべきテストの数を表します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-169">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="d0aaa-170">ご覧のように、単体テストの土台を大きくし、それより小さい統合テスト層が続き、さらに小さい機能テスト層が続くという構成が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-170">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="d0aaa-171">各層には、理想的には、それより下の層では適切に実行できないテストのみを含めます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-171">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="d0aaa-172">特定のシナリオで必要とするテストの種類を決定するとき、このピラミッドを念頭に置いてください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-172">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="d0aaa-173">テストの内容。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-173">What to Test</span></span>

<span data-ttu-id="d0aaa-174">自動化テストの記述経験がない開発者にとっては、何をテストするのかが共通の問題です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-174">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="d0aaa-175">理想的な出発点は条件ロジックをテストすることです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-175">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="d0aaa-176">条件文 (if-else、switch など) に基づいて変化する動作を持つメソッドが含まれる箇所で少なくとも 2、3 のテストが思い付くはずです。特定の条件に対して正しい動作を確認するテストです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-176">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="d0aaa-177">コードの条件に間違いがある場合、(エラーのない) コード経由で "Happy Path" のテストを少なくとも 1 つ記述し、(エラーがあるか、結果が不規則な) "Sad Path" のテストを少なくとも 1 つ記述し、エラーに直面したときにアプリケーションが予想どおりに動作することを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-177">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="d0aaa-178">最後に、コード カバレッジなどの指標ではなく、エラーが起こりうるものに対するテストに集中的に取り組みます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-178">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="d0aaa-179">一般的に、カバレッジは少ないよりも多い方が良いとされます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-179">More code coverage is better than less, generally.</span></span> <span data-ttu-id="d0aaa-180">しかしながら、非常に複雑でビジネスクリティカルなメソッドのテストを 2、3 多く記述することは、テストのコード カバレッジ指標を改善するためだけに自動プロパティのテストを記述することより、通常、時間の使い方として優れています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-180">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="d0aaa-181">テスト プロジェクトを整理する</span><span class="sxs-lookup"><span data-stu-id="d0aaa-181">Organizing Test Projects</span></span>

<span data-ttu-id="d0aaa-182">テスト プロジェクトは、自分にとって最適に機能するように整理できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-182">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="d0aaa-183">種類 (単体テストや統合テスト) やテスト内容 (プロジェクトや名前空間) に基づいてテストを分類することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-183">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="d0aaa-184">その分類が 1 つのテスト プロジェクト内のフォルダーで構成されるのか、複数のテスト プロジェクト内のフォルダーで構成されるのかは設計上の決定事項の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-184">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="d0aaa-185">プロジェクトが 1 つであれば最も単純に整理されますが、大型のプロジェクトでさまざまなテストが含まれる場合、あるいはさまざまなテスト セットをより簡単に実行するには、複数のテスト プロジェクトが必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-185">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="d0aaa-186">多くのチームは、自分たちがテストしているプロジェクトに基づいてプロジェクトを整理します。アプリケーションに相当な数のプロジェクトが含まれるとき、テスト プロジェクトが大量になります。各プロジェクトに含まれるテストの種類に基づいてさらに細分化される場合は特に大量になります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-186">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="d0aaa-187">妥協案としては、テストの種類あたり、アプリケーションあたりプロジェクトを 1 つとし、テスト プロジェクトの中にフォルダーを置き、テスト対象のプロジェクト (とクラス) を示します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-187">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="d0aaa-188">一般的な方法は、‘src' フォルダーの下でアプリケーション プロジェクトを整理し、並列する ‘tests' フォルダーの下でアプリケーションのテスト プロジェクトを整理することです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-188">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="d0aaa-189">この整理方法が有効な場合、Visual Studio でこれに合ったソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-189">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="d0aaa-190">図 9-2 ソリューションでテストを整理する</span><span class="sxs-lookup"><span data-stu-id="d0aaa-190">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="d0aaa-191">好きな方のテスト フレームワークを利用できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-191">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="d0aaa-192">xUnit フレームワークは良好に動作し、ASP.NET Core と EF Core テストはすべてこれで記述されています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-192">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="d0aaa-193">図 9-3 のテンプレートを利用して Visual Studio で xUnit テスト プロジェクトを追加できます。あるいは、dotnet new xunit を利用し、CLI から追加できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-193">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="d0aaa-194">図 9-3 Visual Studio で xUnit テスト プロジェクトを追加する</span><span class="sxs-lookup"><span data-stu-id="d0aaa-194">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="d0aaa-195">テストの命名規則</span><span class="sxs-lookup"><span data-stu-id="d0aaa-195">Test Naming</span></span>

<span data-ttu-id="d0aaa-196">テストには一貫性のある名前を付けてください。それぞれのテストの内容を示す名前にします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-196">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="d0aaa-197">テストするクラスやメソッドに基づいてテスト クラスに名前を付けるという方法でうまく行ったことがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-197">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="d0aaa-198">結果的に小さなテスト クラスがたくさん作られますが、それぞれのテストが担当する内容は極めて明白になります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-198">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="d0aaa-199">テストするクラスやメソッドを識別するためにテスト クラスの名前を設定したら、テスト メソッド名を利用し、テストする動作を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-199">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="d0aaa-200">それにより、求められる動作と、その動作を生むための入力や前提が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-200">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="d0aaa-201">テスト名の例:</span><span class="sxs-lookup"><span data-stu-id="d0aaa-201">Some example test names:</span></span>

-   <span data-ttu-id="d0aaa-202">CatalogControllerGetImage.CallsImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="d0aaa-202">CatalogControllerGetImage.CallsImageServiceWithId</span></span>

-   <span data-ttu-id="d0aaa-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="d0aaa-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span></span>

-   <span data-ttu-id="d0aaa-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span><span class="sxs-lookup"><span data-stu-id="d0aaa-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span></span>

-   <span data-ttu-id="d0aaa-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="d0aaa-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span></span>

<span data-ttu-id="d0aaa-206">この方法のバリエーションとしては、それぞれのテスト クラスの名前の末尾を "Should" にして時制を少し変えます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-206">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

-   <span data-ttu-id="d0aaa-207">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="d0aaa-207">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span></span>

-   <span data-ttu-id="d0aaa-208">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="d0aaa-208">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span></span>

<span data-ttu-id="d0aaa-209">少しばかり冗長ですが、2 つ目の命名規則の方がわかりやすいと感じるチームもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-209">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="d0aaa-210">いずれにせよ、テストの動作がわかる命名規則を利用してください。テストが失敗したとき、何が失敗したのか名前から判断できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-210">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="d0aaa-211">ControllerTests.Test1 のような曖昧な名前をテストに付けないでください。テスト結果に表示されたとき、何の有用性もありません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-211">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="d0aaa-212">小さなテスト クラスをたくさん生成する上記のような命名規則に従う場合、フォルダーや名前空間を利用し、テストをさらに整理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-212">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="d0aaa-213">図 9-4 では、テスト プロジェクト内のフォルダー別にテストを整理している手法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-213">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="d0aaa-214">**図 9-4**</span><span class="sxs-lookup"><span data-stu-id="d0aaa-214">**Figure 9-4.**</span></span> <span data-ttu-id="d0aaa-215">テストされるクラスに基づき、テスト クラスをフォルダーで分けて整理します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-215">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="d0aaa-216">もちろん、特定のアプリケーション クラスにテスト対象メソッドがたくさんある (そのため、テスト クラスもたくさんある) 場合、アプリケーション クラスに対応するフォルダーにそれらを置く方が良いかもしれません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-216">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="d0aaa-217">その整理方法では、ファイルをどこか他の場所のフォルダーに入れて整理する場合と変わりません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-217">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="d0aaa-218">1 つのフォルダーの中に関連ファイルが 3 つもしくは 4 つ以上存在するとき、それぞれの下位フォルダーに移動させると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-218">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="d0aaa-219">ASP.NET Core アプリを単体テストする</span><span class="sxs-lookup"><span data-stu-id="d0aaa-219">Unit Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="d0aaa-220">うまく設計された ASP.NET Core アプリケーションでは、ビジネス エンティティやさまざまなサービスにほとんどの複雑性やビジネス ロジックがカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-220">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="d0aaa-221">ASP.NET Core MVC アプリ自体とそのコントローラー、ビューモデル、ビューには単体テストはほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-221">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="d0aaa-222">アクションの機能性の多くは、アクション メソッド自体の外にあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-222">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="d0aaa-223">ルーティングが正しく機能するかどうかのテストやグローバル エラーの処理は、単体テストで効果的に行うことができません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-223">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="d0aaa-224">同様に、モデル検証、認証、許可のフィルターなど、いかなるフィルターも単体テストできません。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-224">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="d0aaa-225">動作の源がなければ、ほとんどのアクション メソッドは取るに足りないほど小さくなります。動作の源を利用するコントローラーに関係なくテストできるサービスに作業の大部分が委任されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-225">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="d0aaa-226">場合によっては、単体テストする目的で、コードを改良する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-226">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="d0aaa-227">一般的には、インフラストラクチャに対して直接コード化せず、抽象化を特定し、依存関係挿入を利用し、テストするコードの抽象化にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-227">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="d0aaa-228">たとえば、次の例をご覧ください。これは画像を表示する単純なアクション メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-228">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="d0aaa-229">このメソッドの単体テストは System.IO.File に直接依存することで難しくなります。System.IO.File はファイル システムから読み込むために利用されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-229">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="d0aaa-230">この動作をテストし、予想どおり動くことを確認できますが、実際のファイルでそれをするのは統合テストです。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-230">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="d0aaa-231">このメソッドのルートをテストできない点に注目してください。この後すぐ、機能テストでこれを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-231">It's worth noting you can't test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="d0aaa-232">ファイル システムの動作の単体テストが直接実行できないために、ルートをテストできない場合、どのようなテストが残されているのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="d0aaa-232">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="d0aaa-233">改良して単体テストを可能にすると、テスト ケースや、エラー処理など、足りない動作が見つかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-233">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="d0aaa-234">ファイルが見つからないとき、メトリックは何を行うのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="d0aaa-234">What does the method do when a file isn't found?</span></span> <span data-ttu-id="d0aaa-235">何をすべきでしょうか?</span><span class="sxs-lookup"><span data-stu-id="d0aaa-235">What should it do?</span></span> <span data-ttu-id="d0aaa-236">この例では、改良後のメソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-236">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="d0aaa-237">\_logger と \_imageService はいずれも依存関係として挿入されています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-237">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="d0aaa-238">これで、アクション メソッドに渡される同じ ID が \_imageService に渡されることと、結果的に生成されるバイトが FileResult の一部として返されることをテストできます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-238">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="d0aaa-239">エラー ログが予想どおり行われることと、画像が足りない場合、NotFound 結果が返されることもテストできます。これが重要なアプリケーション動作である (つまり、問題を診断するために開発者が追加した一時的なコードではない) ことを前提とします。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-239">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="d0aaa-240">実際のファイル ロジックは別個の実装サービスに移動しており、ファイルが足りない場合にアプリケーション固有の例外を返すように拡大されています。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-240">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="d0aaa-241">統合テストを利用して、この実装を非依存でテストできます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-241">You can test this implementation independently, using an integration test.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="d0aaa-242">ASP.NET Core Apps を統合テストする</span><span class="sxs-lookup"><span data-stu-id="d0aaa-242">Integration Testing ASP.NET Core Apps</span></span>

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

<span data-ttu-id="d0aaa-243">このサービスでは、別個のサービスに改良される前の CatalogController コードと同様に、IHostingEnvironment が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-243">This service uses the IHostingEnvironment, just as the CatalogController code did before it was refactored into a separate service.</span></span> <span data-ttu-id="d0aaa-244">これがコントローラーで IHostingEnvironment を使用した唯一のコードであったため、その依存関係は CatalogController のコンストラクターから削除されました。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-244">Since this was the only code in the controller that used IHostingEnvironment, that dependency was removed from CatalogController's constructor.</span></span>

<span data-ttu-id="d0aaa-245">このサービスが正しく機能することをテストするには、既知のテスト画像ファイルを作成し、特定の入力後、サービスがそのファイルを正しく返すことを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-245">To test that this service works correctly, you need to create a known test image file and verify that the service returns it given a specific input.</span></span> <span data-ttu-id="d0aaa-246">実際にテストする動作 (この場合、ファイル システムから読み込むこと) にはモック オブジェクトを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-246">You should take care not to use mock objects on the behavior you actually want to test (in this case, reading from the file system).</span></span> <span data-ttu-id="d0aaa-247">ただし、統合テストの設定でもモック オブジェクトは役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-247">However, mock objects may still be useful to set up integration tests.</span></span> <span data-ttu-id="d0aaa-248">この事例では、その ContentRootPath がテスト画像に使用するフォルダーを指すように IHostingEnvironment をモックできます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-248">In this case, you can mock IHostingEnvironment so that its ContentRootPath points to the folder you're going to use for your test image.</span></span> <span data-ttu-id="d0aaa-249">完璧に動作する統合テスト クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-249">The complete working integration test class is shown here:</span></span>

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
> <span data-ttu-id="d0aaa-250">テスト自体は非常に単純です。コードの大部分はシステムを構成し、テスト インフラストラクチャを作成するために必要です (この場合、ディスクから読み取る実際のファイル)。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-250">that the test itself is very simple – the bulk of the code is necessary to configure the system and create the testing infrastructure (in this case, an actual file to be read from disk).</span></span> <span data-ttu-id="d0aaa-251">これは、通常は単体テストより複雑な設定作業を必要とする統合テストの特徴です。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-251">This is typical for integration tests, which often require more complex setup work than unit tests.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="d0aaa-252">ASP.NET Core アプリを機能テストする</span><span class="sxs-lookup"><span data-stu-id="d0aaa-252">Functional Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="d0aaa-253">ASP.NET Core アプリケーションの場合、TestServer クラスを利用すると、機能テストをとても簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-253">For ASP.NET Core applications, the TestServer class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="d0aaa-254">アプリケーションに普通に行うように、WebHostBuilder を利用して TestServer を構成します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-254">You configure a TestServer using a WebHostBuilder, just as you normally do for your application.</span></span> <span data-ttu-id="d0aaa-255">この WebHostBuilder はアプリケーションの実際のホストと同じように構成すべきですが、テストが楽にするあらゆる側面を改良できます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-255">This WebHostBuilder should be configured just like your application's real host, but you can modify any aspects of it that make testing easier.</span></span> <span data-ttu-id="d0aaa-256">ほとんどの場合、さまざまなテスト ケースで同じ TestServer を再利用します。再利用可能メソッドでカプセル化できます (おそらく基底クラスで)。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-256">Most of the time, you'll reuse the same TestServer for many test cases, so you can encapsulate it in a reusable method (perhaps in a base class):</span></span>

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

<span data-ttu-id="d0aaa-257">GetProjectPath メソッドは、Web プロジェクトの物理パスを返します (サンプル ソリューションをダウンロードする)。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-257">The GetProjectPath method simply returns the physical path to the web project (download sample solution).</span></span> <span data-ttu-id="d0aaa-258">この場合の WebHostBuilder は Web アプリケーションのコンテンツ ルートがある場所を指定し、実際の Web アプリケーションが使用する同じ Startup クラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-258">The WebHostBuilder in this case simply specifies where the content root for the web application is, and references the same Startup class the real web application uses.</span></span> <span data-ttu-id="d0aaa-259">TestServer と連動させるには、標準の System.Net.HttpClient 型を利用し、TestServer に要求します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-259">To work with the TestServer, you use the standard System.Net.HttpClient type to make requests to it.</span></span> <span data-ttu-id="d0aaa-260">TestServer は便利な CreateClient メソッドを公開します。このメソッドが提供する事前構成済みのクライアントは、TestServer で実行されているアプリケーションにいつでも要求を出せます。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-260">TestServer exposes a helpful CreateClient method that provides a pre-configured client that is ready to make requests to the application running on the TestServer.</span></span> <span data-ttu-id="d0aaa-261">ASP.NET Core アプリケーションのために機能テストを記述するとき、このクライアントを使用します (上記の基本テストで保護 \_client メンバーに設定されています)。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-261">You use this client (set to the protected \_client member on the base test above) when writing functional tests for your ASP.NET Core application:</span></span>

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

<span data-ttu-id="d0aaa-262">この機能テストは、配置されているあらゆるミドルウェア、フィルター、バインダーなど、完全な ASP.NET Core MVC アプリケーション スタックを行使します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-262">This functional test exercises the full ASP.NET Core MVC application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="d0aaa-263">既知の場所にあるファイルに対して予想されるバイト配列を所与のルート ("/catalog/pic/1") が返すことを検証します。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-263">It verifies that a given route ("/catalog/pic/1") returns the expected byte array for a file in a known location.</span></span> <span data-ttu-id="d0aaa-264">これは実際の Web サーバーを設定せずに行い、実際の Web サーバーを利用して不安定になることを回避します (ファイアウォール設定の問題など)。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-264">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="d0aaa-265">TestServer に対して実行される機能テストは通常、統合テストや単体テストより遅くなりますが、テスト Web サーバーのネットワークで実行されるテストよりはるかに速くなります。</span><span class="sxs-lookup"><span data-stu-id="d0aaa-265">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="d0aaa-266">[前] (work-with-data-in-asp-net-core-apps.md) [次] (development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="d0aaa-266">[Previous] (work-with-data-in-asp-net-core-apps.md) [Next] (development-process-for-azure.md)</span></span>
