---
title: 従来の Web アプリケーションかシングル ページ アプリケーションを選択する
description: ASP.NET Core および Microsoft Azure での最新の Web アプリケーションの設計
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb830ede1b644700a80f0e9fac2f3608deb88276
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="01bca-103">従来の Web アプリケーションかシングル ページ アプリケーション (SPA) を選択する</span><span class="sxs-lookup"><span data-stu-id="01bca-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="01bca-104">"Atwood の法則: JavaScript で記述できるすべてのアプリケーションは、最終的に JavaScript で記述される"</span><span class="sxs-lookup"><span data-stu-id="01bca-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="01bca-105">_\- Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="01bca-105">_\- Jeff Atwood_</span></span>

## <a name="summary"></a><span data-ttu-id="01bca-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="01bca-106">Summary</span></span>

<span data-ttu-id="01bca-107">現在、Web アプリケーションを構築するには、一般的に 2 つのアプローチがあります。サーバー上でアプリケーション ロジックの大部分を実行する従来の Web アプリケーションと、Web ブラウザーでユーザー インターフェイス ロジックのほとんどを実行し、主に Web API を使用して Web サーバーと通信するシングル ページ アプリケーション (SPA) です。</span><span class="sxs-lookup"><span data-stu-id="01bca-107">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="01bca-108">ハイブリッド アプローチも可能であり、最も単純なのは、高度な SPA のような 1 つ以上のサブアプリケーションを、より大規模な従来の Web アプリケーション内でホストする方法です。</span><span class="sxs-lookup"><span data-stu-id="01bca-108">A hybrid approach is also possible, the simplest being host one or more rich SPA-like sub-applications within a larger traditional web application.</span></span>

<span data-ttu-id="01bca-109">次の場合は、従来の Web アプリケーションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01bca-109">You should use traditional web applications when:</span></span>

-   <span data-ttu-id="01bca-110">アプリケーションのクライアント側の要件が単純か、読み取り専用である。</span><span class="sxs-lookup"><span data-stu-id="01bca-110">Your application's client-side requirements are simple or even read-only.</span></span>

-   <span data-ttu-id="01bca-111">JavaScript をサポートしていないブラウザーでアプリケーションが機能する必要がある。</span><span class="sxs-lookup"><span data-stu-id="01bca-111">Your application needs to function in browsers without JavaScript support.</span></span>

-   <span data-ttu-id="01bca-112">チームが JavaScript や TypeScript の開発手法に精通していない。</span><span class="sxs-lookup"><span data-stu-id="01bca-112">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="01bca-113">次の場合は、SPA を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01bca-113">You should use a SPA when:</span></span>

-   <span data-ttu-id="01bca-114">アプリケーションで、多くの機能を備えた高度なユーザー インターフェイスを公開する必要がある。</span><span class="sxs-lookup"><span data-stu-id="01bca-114">Your application must expose a rich user interface with many features.</span></span>

-   <span data-ttu-id="01bca-115">チームが JavaScript や TypeScript の開発に精通している。</span><span class="sxs-lookup"><span data-stu-id="01bca-115">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

-   <span data-ttu-id="01bca-116">他の (内部またはパブリック) クライアントに API を公開するという要件がアプリケーションに既にある。</span><span class="sxs-lookup"><span data-stu-id="01bca-116">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="01bca-117">さらに、SPA フレームワークには、より高度なアーキテクチャとセキュリティの専門知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="01bca-117">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="01bca-118">従来の Web アプリケーションよりも頻繁な更新と新しいフレームワークにより、チームは大きな変化を経験します。</span><span class="sxs-lookup"><span data-stu-id="01bca-118">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="01bca-119">SPA アプリケーションでは自動化されたビルドおよび展開プロセスを構成し、コンテナーのような展開オプションを利用するので、従来の Web アプリケーションよりも困難です。</span><span class="sxs-lookup"><span data-stu-id="01bca-119">Configuring automated build and deployment processes and utilizing deployment options like containers are more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="01bca-120">SPA モデルで可能になるユーザー エクスペリエンスの改善と、これらの考慮事項を比較して、優先順位を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bca-120">Improvements in user experience made possible by SPA model must be weighed against these considerations.</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="01bca-121">従来の Web アプリケーションを選択する場合</span><span class="sxs-lookup"><span data-stu-id="01bca-121">When to choose traditional web apps</span></span>

<span data-ttu-id="01bca-122">ここでは、前述した従来の Web アプリケーションを選択する理由について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="01bca-122">The following is a more detailed explanation of the previously-stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="01bca-123">**アプリケーションは単純で、場合によっては読み取り専用であり、クライアント側の必要条件がある**</span><span class="sxs-lookup"><span data-stu-id="01bca-123">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="01bca-124">多くの Web アプリケーションは、大多数のユーザーが主に読み取り専用で使用しています。</span><span class="sxs-lookup"><span data-stu-id="01bca-124">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="01bca-125">読み取り専用 (または読み取り主体) のアプリケーションは、大量の状態を維持および操作するアプリケーションよりもはるかに単純な傾向があります。</span><span class="sxs-lookup"><span data-stu-id="01bca-125">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="01bca-126">たとえば、検索エンジンは、テキストボックスを使用した 1 つのエントリ ポイントと、検索結果を表示するための 2 番目のページで構成されます。</span><span class="sxs-lookup"><span data-stu-id="01bca-126">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="01bca-127">匿名ユーザーは簡単に要求を実行することができます。クライアント側のロジックはほとんど必要ありません。</span><span class="sxs-lookup"><span data-stu-id="01bca-127">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="01bca-128">同様に、ブログやコンテンツ管理システムの公開アプリケーションは、通常、主にクライアント側の動作がほとんどないコンテンツから構成されています。</span><span class="sxs-lookup"><span data-stu-id="01bca-128">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="01bca-129">このようなアプリケーションは、Web サーバー上でロジックを実行し、HTML をブラウザーに表示する従来のサーバーベースの Web アプリケーションとして簡単に構築できます。</span><span class="sxs-lookup"><span data-stu-id="01bca-129">Such applications are easily built as traditional server-based web applications which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="01bca-130">サイトの個々のページには、ブックマークを追加し、検索エンジンでインデックスを付けることができる独自の URL があります (既定では、アプリケーションの個別の機能としてこの機能を追加する必要はありません)。このようなシナリオでは、この点は明らかな利点でもあります。</span><span class="sxs-lookup"><span data-stu-id="01bca-130">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="01bca-131">**JavaScript をサポートしていないブラウザーでアプリケーションが機能する必要がある**</span><span class="sxs-lookup"><span data-stu-id="01bca-131">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="01bca-132">JavaScript のサポートが限られている、またはサポートされていないブラウザーで機能する必要がある Web アプリケーションは、従来の Web アプリケーションのワークフローを使用して作成する必要があります (または、少なくともそのような動作にフォールバックできる必要があります)。</span><span class="sxs-lookup"><span data-stu-id="01bca-132">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="01bca-133">SPA が機能するには、クライアント側の JavaScript が必要です。JavaScript を利用できない場合は、SPA は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="01bca-133">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="01bca-134">**チームが JavaScript や TypeScript の開発手法に精通していない**</span><span class="sxs-lookup"><span data-stu-id="01bca-134">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="01bca-135">チームが JavaScript や TypeScript に精通しておらず、サーバー側の Web アプリケーション開発に精通している場合は、SPA よりも従来の Web アプリケーションの方が短時間で提供できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01bca-135">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="01bca-136">SPA のプログラミングを習得することが目標の場合や、SPA が提供するユーザー エクスペリエンスが必要な場合を除き、従来の Web アプリケーションは、その構築に既に精通しているチームにとってはより生産的な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="01bca-136">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="01bca-137">SPA を選択する場合</span><span class="sxs-lookup"><span data-stu-id="01bca-137">When to choose SPAs</span></span>

<span data-ttu-id="01bca-138">ここでは、Web アプリケーションにシングル ページ アプリケーション スタイルの開発を選択する場合について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="01bca-138">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="01bca-139">**アプリケーションで、多くの機能を備えた高度なユーザー インターフェイスを公開する必要がある**</span><span class="sxs-lookup"><span data-stu-id="01bca-139">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="01bca-140">SPA は、ユーザーが操作を行ったり、アプリケーションの各領域間を移動したりするときに、ページの再読み込みが必要ない、高度なクライアント側の機能をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="01bca-140">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="01bca-141">SPA は読み込み時間が高速で、バックグラウンドでデータを取得します。ページ全体が再読み込みされることはまれなので、各ユーザー アクションの応答性が向上します。</span><span class="sxs-lookup"><span data-stu-id="01bca-141">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="01bca-142">SPA は増分更新をサポートできるので、ユーザーがボタンをクリックしてフォームを送信しなくても、部分的に完了したフォームまたはドキュメントを保存することができます。</span><span class="sxs-lookup"><span data-stu-id="01bca-142">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="01bca-143">SPA は、従来のアプリケーションよりもはるかに簡単に、ドラッグアンドドロップなどの高度なクライアント側の動作をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="01bca-143">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="01bca-144">SPA は、切断されたモードで動作するように設計し、接続が再確立したときに、最終的にサーバーに同期されるようにクライアント側モデルを更新できます。</span><span class="sxs-lookup"><span data-stu-id="01bca-144">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="01bca-145">一般的な HTML フォームが提供する機能を超える豊富な機能がアプリケーションの要件に含まれている場合は、SPA スタイルのアプリケーションを選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01bca-145">You should choose a SPA style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="01bca-146">従来の Web アプリケーションに組み込まれている機能の実装が SPA で必要になることはよくあります。たとえば、アドレス バーに現在の操作を反映したわかりやすい URL を表示する機能 (そしてユーザーが URL のブックマークやディープ リンクを作成して URL に戻ることができる機能) などです。</span><span class="sxs-lookup"><span data-stu-id="01bca-146">Note that frequently SPAs need to implement features that are built-in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="01bca-147">また、SPA では、ユーザーがブラウザーの [戻る] ボタンと [次に進む] ボタンを使用したときに驚くような結果にはなりません。</span><span class="sxs-lookup"><span data-stu-id="01bca-147">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="01bca-148">**チームが JavaScript や TypeScript の開発に精通している**</span><span class="sxs-lookup"><span data-stu-id="01bca-148">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="01bca-149">SPA を作成するには、JavaScript や TypeScript と、クライアント側のプログラミング手法とライブラリに精通している必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bca-149">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="01bca-150">チームには、Angular のような SPA フレームワークを使用して最新の JavaScript を記述できる能力が必要です。</span><span class="sxs-lookup"><span data-stu-id="01bca-150">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="01bca-151">参考資料 - SPA フレームワーク</span><span class="sxs-lookup"><span data-stu-id="01bca-151">References – SPA Frameworks</span></span>
> - <span data-ttu-id="01bca-152">**AngularJS**</span><span class="sxs-lookup"><span data-stu-id="01bca-152">**AngularJS**</span></span>  
> <span data-ttu-id="01bca-153"><https://angularjs.org/></span><span class="sxs-lookup"><span data-stu-id="01bca-153"><https://angularjs.org/></span></span>
> - <span data-ttu-id="01bca-154">**4 つの人気のある JavaScript フレームワークの比較**</span><span class="sxs-lookup"><span data-stu-id="01bca-154">**Comparison of 4 Popular JavaScript Frameworks**</span></span>  
> <span data-ttu-id="01bca-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span><span class="sxs-lookup"><span data-stu-id="01bca-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span></span>

<span data-ttu-id="01bca-156">**他の (内部またはパブリック) クライアントに API を公開するという要件がアプリケーションに既にある**</span><span class="sxs-lookup"><span data-stu-id="01bca-156">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="01bca-157">他のクライアントが使用する Web API をサポートしている場合は、サーバー側のフォームでロジックを再現するのではなく、このような API を利用する SPA 実装を作成する方が簡単な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01bca-157">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="01bca-158">ユーザーがアプリケーションを操作すると、SPA は多数の Web API を使用してデータのクエリと更新を行います。</span><span class="sxs-lookup"><span data-stu-id="01bca-158">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="decision-table--traditional-web-or-spa"></a><span data-ttu-id="01bca-159">意思決定テーブル - 従来の Web または SPA</span><span class="sxs-lookup"><span data-stu-id="01bca-159">Decision table – Traditional Web or SPA</span></span>

<span data-ttu-id="01bca-160">以下の意思決定テーブルは、従来の Web アプリケーションまたは SPA を選択する際に考慮する基本的な要素の一部をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="01bca-160">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application and a SPA.</span></span>

  | <span data-ttu-id="01bca-161">**要素**</span><span class="sxs-lookup"><span data-stu-id="01bca-161">**Factor**</span></span> | <span data-ttu-id="01bca-162">**従来の Web アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="01bca-162">**Traditional Web App**</span></span> | <span data-ttu-id="01bca-163">**シングル ページ アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="01bca-163">**Single Page Application**</span></span> |
  |---|---|---|
  | <span data-ttu-id="01bca-164">チームに必要な JavaScript/TypeScript の精通度</span><span class="sxs-lookup"><span data-stu-id="01bca-164">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="01bca-165">**最小限**</span><span class="sxs-lookup"><span data-stu-id="01bca-165">**Minimal**</span></span> | <span data-ttu-id="01bca-166">**必須**</span><span class="sxs-lookup"><span data-stu-id="01bca-166">**Required**</span></span> |
  | <span data-ttu-id="01bca-167">スクリプトを作成せずにブラウザーをサポート</span><span class="sxs-lookup"><span data-stu-id="01bca-167">Support Browsers without Scripting</span></span> | <span data-ttu-id="01bca-168">**サポート**</span><span class="sxs-lookup"><span data-stu-id="01bca-168">**Supported**</span></span> | <span data-ttu-id="01bca-169">**サポートされない**</span><span class="sxs-lookup"><span data-stu-id="01bca-169">**Not Supported**</span></span> |
  | <span data-ttu-id="01bca-170">最小限のクライアント側アプリケーションの動作</span><span class="sxs-lookup"><span data-stu-id="01bca-170">Minimal Client-Side Application Behavior</span></span> | <span data-ttu-id="01bca-171">**適している**</span><span class="sxs-lookup"><span data-stu-id="01bca-171">**Well-Suited**</span></span> | <span data-ttu-id="01bca-172">**過剰**</span><span class="sxs-lookup"><span data-stu-id="01bca-172">**Overkill**</span></span> |
  | <span data-ttu-id="01bca-173">高度で複雑なユーザー インターフェイス要件</span><span class="sxs-lookup"><span data-stu-id="01bca-173">Rich, Complex User Interface Requirements</span></span> | <span data-ttu-id="01bca-174">**制限がある**</span><span class="sxs-lookup"><span data-stu-id="01bca-174">**Limited**</span></span> | <span data-ttu-id="01bca-175">**適している**</span><span class="sxs-lookup"><span data-stu-id="01bca-175">**Well-Suited**</span></span> |

>[!div class="step-by-step"]
<span data-ttu-id="01bca-176">[前へ] (modern-web-applications-characteristics.md) [次へ](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="01bca-176">[Previous] (modern-web-applications-characteristics.md) [Next](architectural-principles.md)</span></span>
