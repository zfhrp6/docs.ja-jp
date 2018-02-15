---
title: "従来の web アプリとアプリの 1 つのページの選択します。"
description: "ASP.NET Core と Microsoft Azure での最新の web アプリケーションを設計します。"
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a><span data-ttu-id="61c40-103">従来の Web アプリまたは単一ページ アプリケーション (SPAs) を選択します。</span><span class="sxs-lookup"><span data-stu-id="61c40-103">Choose Between Traditional Web Apps and Single Page Apps (SPAs)</span></span>

> <span data-ttu-id="61c40-104">"Atwood の法律: JavaScript では、書き込むことができる任意のアプリケーションは、JavaScript に最終的に記述されます"。</span><span class="sxs-lookup"><span data-stu-id="61c40-104">"Atwood's Law: Any application that can be written in JavaScript, will eventually be written in JavaScript."</span></span>  
> <span data-ttu-id="61c40-105">_\- Jeff Atwood_</span><span class="sxs-lookup"><span data-stu-id="61c40-105">_\- Jeff Atwood_</span></span>

## <a name="summary"></a><span data-ttu-id="61c40-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="61c40-106">Summary</span></span>

<span data-ttu-id="61c40-107">Web アプリケーションの構築を今すぐに 2 つの一般的なアプローチします従来の web アプリケーション サーバー、および web ブラウザーで、ほとんどのユーザー インターフェイス ロジックを実行する単一ページ アプリケーション (SPAs) 上のほとんどのアプリケーション ロジックを実行する。主に web Api を使用して web サーバーと通信します。</span><span class="sxs-lookup"><span data-stu-id="61c40-107">There are two general approaches to building web applications today: traditional web applications that perform most of the application logic on the server, and single page applications (SPAs) that perform most of the user interface logic in a web browser, communicating with the web server primarily using web APIs.</span></span> <span data-ttu-id="61c40-108">ハイブリッド アプローチも、最も簡単アプリケーションをホストする 1 つまたは複数リッチ SPA のようなサブ大規模な従来の web アプリケーション内でできます。</span><span class="sxs-lookup"><span data-stu-id="61c40-108">A hybrid approach is also possible, the simplest being host one or more rich SPA-like sub-applications within a larger traditional web application.</span></span>

<span data-ttu-id="61c40-109">従来の web アプリケーションを使用する必要があるとき。</span><span class="sxs-lookup"><span data-stu-id="61c40-109">You should use traditional web applications when:</span></span>

-   <span data-ttu-id="61c40-110">アプリケーションのクライアント側の要件は、単純型または読み取り専用でもです。</span><span class="sxs-lookup"><span data-stu-id="61c40-110">Your application's client-side requirements are simple or even read-only.</span></span>

-   <span data-ttu-id="61c40-111">アプリケーションは、JavaScript のサポートなしのブラウザーで機能する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-111">Your application needs to function in browsers without JavaScript support.</span></span>

-   <span data-ttu-id="61c40-112">チームでは、JavaScript または TypeScript 開発手法を理解します。</span><span class="sxs-lookup"><span data-stu-id="61c40-112">Your team is unfamiliar with JavaScript or TypeScript development techniques.</span></span>

<span data-ttu-id="61c40-113">SPA を使用する必要があるとき。</span><span class="sxs-lookup"><span data-stu-id="61c40-113">You should use a SPA when:</span></span>

-   <span data-ttu-id="61c40-114">アプリケーションでは、多くの機能の豊富なユーザー インターフェイスを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-114">Your application must expose a rich user interface with many features.</span></span>

-   <span data-ttu-id="61c40-115">チームが JavaScript または TypeScript の開発に慣れています。</span><span class="sxs-lookup"><span data-stu-id="61c40-115">Your team is familiar with JavaScript and/or TypeScript development.</span></span>

-   <span data-ttu-id="61c40-116">アプリケーションは、他の (内部またはパブリック) クライアント API を公開する必要があります既にです。</span><span class="sxs-lookup"><span data-stu-id="61c40-116">Your application must already expose an API for other (internal or public) clients.</span></span>

<span data-ttu-id="61c40-117">さらに、SPA フレームワーク以上を必要とアーキテクチャとセキュリティに関する専門知識。</span><span class="sxs-lookup"><span data-stu-id="61c40-117">Additionally, SPA frameworks require greater architectural and security expertise.</span></span> <span data-ttu-id="61c40-118">従来の web アプリケーションよりも頻繁に更新および新しいフレームワークにより大きい変化が発生します。</span><span class="sxs-lookup"><span data-stu-id="61c40-118">They experience greater churn due to frequent updates and new frameworks than traditional web applications.</span></span> <span data-ttu-id="61c40-119">自動ビルドと配置プロセスを構成およびコンテナーのような展開オプションを利用するは、従来の web アプリよりも SPA アプリケーションとより困難です。</span><span class="sxs-lookup"><span data-stu-id="61c40-119">Configuring automated build and deployment processes and utilizing deployment options like containers are more difficult with SPA applications than traditional web apps.</span></span>

<span data-ttu-id="61c40-120">SPA モデルによって可能になりますユーザー エクスペリエンスの向上は、これらの注意点を比較検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-120">Improvements in user experience made possible by SPA model must be weighed against these considerations.</span></span>

## <a name="when-to-choose-traditional-web-apps"></a><span data-ttu-id="61c40-121">従来の web アプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="61c40-121">When to choose traditional web apps</span></span>

<span data-ttu-id="61c40-122">従来の web アプリケーションを選択する前に示した理由の詳細な説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61c40-122">The following is a more detailed explanation of the previously-stated reasons for picking traditional web applications.</span></span>

<span data-ttu-id="61c40-123">**アプリケーションがシンプルで読み取り専用可能性のある、クライアント側の要件**</span><span class="sxs-lookup"><span data-stu-id="61c40-123">**Your application has simple, possibly read-only, client-side requirements**</span></span>

<span data-ttu-id="61c40-124">多くの web アプリケーションは、ユーザーの大部分で読み取り専用で、主に消費されます。</span><span class="sxs-lookup"><span data-stu-id="61c40-124">Many web applications are primarily consumed in a read-only fashion by the vast majority of their users.</span></span> <span data-ttu-id="61c40-125">読み取り専用 (通常は読み取り専用) アプリケーションは、管理およびさまざまな状態を操作するよりもはるかに簡単にする傾向があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-125">Read-only (or read-mostly) applications tend to be much simpler than those that maintain and manipulate a great deal of state.</span></span> <span data-ttu-id="61c40-126">たとえば、検索エンジンをテキスト ボックスと検索結果を表示するための 2 番目のページの 1 つのエントリ ポイントの可能性がありますで構成されます。</span><span class="sxs-lookup"><span data-stu-id="61c40-126">For example, a search engine might consist of a single entry point with a textbox and a second page for displaying search results.</span></span> <span data-ttu-id="61c40-127">匿名ユーザーは、要求を簡単に作成でき、クライアント側のロジックの必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="61c40-127">Anonymous users can easily make requests, and there is little need for client-side logic.</span></span> <span data-ttu-id="61c40-128">同様に、ブログまたはコンテンツ管理システムの公開アプリケーションは、ほとんどのクライアント側の動作とコンテンツの内訳は通常は。</span><span class="sxs-lookup"><span data-stu-id="61c40-128">Likewise, a blog or content management system's public-facing application usually consists mainly of content with little client-side behavior.</span></span> <span data-ttu-id="61c40-129">このようなアプリケーションは、web サーバー上のロジックを実行し、ブラウザーに表示される HTML をレンダリングする従来のサーバー ベースの web アプリケーションとして簡単に構築されます。</span><span class="sxs-lookup"><span data-stu-id="61c40-129">Such applications are easily built as traditional server-based web applications which perform logic on the web server and render HTML to be displayed in the browser.</span></span> <span data-ttu-id="61c40-130">サイトの一意な各ページのブックマークが付けられたおよび検索エンジンで (既定では、このアプリケーションの個別の機能として追加することがなく) インデックスを作成できる、独自の URL であるという事実がこのようなシナリオで明らかな利点もあります。</span><span class="sxs-lookup"><span data-stu-id="61c40-130">The fact that each unique page of the site has its own URL that can be bookmarked and indexed by search engines (by default, without having to add this as a separate feature of the application) is also a clear benefit in such scenarios.</span></span>

<span data-ttu-id="61c40-131">**アプリケーションは、JavaScript のサポートなしのブラウザーで機能する必要があります。**</span><span class="sxs-lookup"><span data-stu-id="61c40-131">**Your application needs to function in browsers without JavaScript support**</span></span>

<span data-ttu-id="61c40-132">限定的または JavaScript がサポートされていないブラウザーで機能する必要がある web アプリケーションは従来の web アプリのワークフローを使用して記述する必要があります (または、少なくともこのような動作に戻すことができる)。</span><span class="sxs-lookup"><span data-stu-id="61c40-132">Web applications that need to function in browsers with limited or no JavaScript support should be written using traditional web app workflows (or at least be able to fall back to such behavior).</span></span> <span data-ttu-id="61c40-133">SPAs がクライアント側の JavaScript を必要とすると、関数です。使用できない場合 SPAs はこの適切な選択ではありません。</span><span class="sxs-lookup"><span data-stu-id="61c40-133">SPAs require client-side JavaScript in order to function; if it's not available, SPAs are not a good choice.</span></span>

<span data-ttu-id="61c40-134">**チームが JavaScript または TypeScript の開発方法に慣れていなければ**</span><span class="sxs-lookup"><span data-stu-id="61c40-134">**Your team is unfamiliar with JavaScript or TypeScript development techniques**</span></span>

<span data-ttu-id="61c40-135">場合は、チームが JavaScript または TypeScript に慣れていなければがサーバー側の web アプリケーションの開発に慣れてがおそらくできる、SPA よりも速く、従来の web アプリを配信します。</span><span class="sxs-lookup"><span data-stu-id="61c40-135">If your team is unfamiliar with JavaScript or TypeScript, but is familiar with server-side web application development, then they will probably be able to deliver a traditional web app more quickly than a SPA.</span></span> <span data-ttu-id="61c40-136">場合を除き、プログラム SPAs を学習、目標、SPA で利用可能になるユーザー エクスペリエンスが必要、従来の web アプリは、既にそのビルドを使い慣れているチームの生産性を向上選択肢がします。</span><span class="sxs-lookup"><span data-stu-id="61c40-136">Unless learning to program SPAs is a goal, or the user experience afforded by a SPA is required, traditional web apps are a more productive choice for teams who are already familiar with building them.</span></span>

## <a name="when-to-choose-spas"></a><span data-ttu-id="61c40-137">SPAs を選択します。</span><span class="sxs-lookup"><span data-stu-id="61c40-137">When to choose SPAs</span></span>

<span data-ttu-id="61c40-138">Web アプリの開発の単一ページ アプリケーションのスタイルを選択するための詳細な説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="61c40-138">The following is a more detailed explanation of when to choose a Single Page Applications style of development for your web app.</span></span>

<span data-ttu-id="61c40-139">**アプリケーションは、多くの機能の豊富なユーザー インターフェイスを公開する必要があります。**</span><span class="sxs-lookup"><span data-stu-id="61c40-139">**Your application must expose a rich user interface with many features**</span></span>

<span data-ttu-id="61c40-140">SPAs には、ユーザーがアクションを実行またはアプリケーションの領域間を移動するページの再読み込みを必要としない豊富なクライアント側機能をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="61c40-140">SPAs can support rich client-side functionality that doesn't require reloading the page as users take actions or navigate between areas of the app.</span></span> <span data-ttu-id="61c40-141">SPAs はバック グラウンドでデータのフェッチより迅速に読み込むことができ、ページ全体の再読み込みがほとんどないために、個々 のユーザー操作は応答性が向上します。</span><span class="sxs-lookup"><span data-stu-id="61c40-141">SPAs can load more quickly, fetching data in the background, and individual user actions are more responsive since full page reloads are rare.</span></span> <span data-ttu-id="61c40-142">SPAs には、フォームを送信するユーザーがボタンをクリックすることも、部分的に完了したフォームまたはドキュメントを保存、増分更新をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="61c40-142">SPAs can support incremental updates, saving partially completed forms or documents without the user having to click a button to submit a form.</span></span> <span data-ttu-id="61c40-143">SPAs では、従来のアプリケーションよりもはるかに簡単にドラッグ アンド ドロップなどの豊富なクライアント側の動作をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="61c40-143">SPAs can support rich client-side behaviors, such as drag-and-drop, much more readily than traditional applications.</span></span> <span data-ttu-id="61c40-144">SPAs は、接続が再確立された後に最終的に、サーバーに再度同期されるクライアント側のモデルに対して更新を行う、切断されているモードで実行するように設計できます。</span><span class="sxs-lookup"><span data-stu-id="61c40-144">SPAs can be designed to run in a disconnected mode, making updates to a client-side model that are eventually synchronized back to the server once a connection is re-established.</span></span> <span data-ttu-id="61c40-145">アプリの要件は、一般的な HTML フォームの提供を超える豊富な機能を含める場合は、SPA スタイルのアプリケーションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="61c40-145">You should choose a SPA style application if your app's requirements include rich functionality that goes beyond what typical HTML forms offer.</span></span>

<span data-ttu-id="61c40-146">SPAs が頻繁に意味のある URL が表示され、アドレス バーで、現在の操作の反映 (に戻り、ブックマークにユーザーまたはこの URL へのディープ リンクを許可する) などの従来の web アプリに組み込まれている機能を実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="61c40-146">Note that frequently SPAs need to implement features that are built-in to traditional web apps, such as displaying a meaningful URL in the address bar reflecting the current operation (and allowing users to bookmark or deep link to this URL to return to it).</span></span> <span data-ttu-id="61c40-147">SPAs もする必要があります、ユーザーに驚くされない結果を含む、ブラウザーの戻るボタンと進むボタンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="61c40-147">SPAs also should allow users to use the browser's back and forward buttons with results that won't surprise them.</span></span>

<span data-ttu-id="61c40-148">**チームが JavaScript または TypeScript の開発に慣れて**</span><span class="sxs-lookup"><span data-stu-id="61c40-148">**Your team is familiar with JavaScript and/or TypeScript development**</span></span>

<span data-ttu-id="61c40-149">SPAs を書き込むには、JavaScript または TypeScript およびクライアント側のプログラミング手法とライブラリに関する知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="61c40-149">Writing SPAs requires familiarity with JavaScript and/or TypeScript and client-side programming techniques and libraries.</span></span> <span data-ttu-id="61c40-150">チームは、角のような SPA フレームワークを使用して JavaScript を最新の書き込みで高いする必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-150">Your team should be competent in writing modern JavaScript using a SPA framework like Angular.</span></span>

> ### <a name="references--spa-frameworks"></a><span data-ttu-id="61c40-151">参照: SPA フレームワーク</span><span class="sxs-lookup"><span data-stu-id="61c40-151">References – SPA Frameworks</span></span>
> - <span data-ttu-id="61c40-152">**AngularJS**</span><span class="sxs-lookup"><span data-stu-id="61c40-152">**AngularJS**</span></span>  
> <span data-ttu-id="61c40-153"><https://angularjs.org/></span><span class="sxs-lookup"><span data-stu-id="61c40-153"><https://angularjs.org/></span></span>
> - <span data-ttu-id="61c40-154">**4 つの一般的な JavaScript フレームワークの比較**</span><span class="sxs-lookup"><span data-stu-id="61c40-154">**Comparison of 4 Popular JavaScript Frameworks**</span></span>  
> <span data-ttu-id="61c40-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span><span class="sxs-lookup"><span data-stu-id="61c40-155"><https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks></span></span>

<span data-ttu-id="61c40-156">**アプリケーションは、他の (内部またはパブリック) クライアント API を公開既に必要があります。**</span><span class="sxs-lookup"><span data-stu-id="61c40-156">**Your application must already expose an API for other (internal or public) clients**</span></span>

<span data-ttu-id="61c40-157">既に他のクライアントで使用する web API をサポートしている、サーバー側フォーム内のロジックを再現するのではなく、これらの Api を活用する SPA 実装を作成するには、少ない労力が必要があります。</span><span class="sxs-lookup"><span data-stu-id="61c40-157">If you're already supporting a web API for use by other clients, it may require less effort to create a SPA implementation that leverages these APIs rather than reproducing the logic in server-side form.</span></span> <span data-ttu-id="61c40-158">SPAs 広く利用されて web Api のデータのクエリと更新プログラムをユーザーがアプリケーションを操作するとします。</span><span class="sxs-lookup"><span data-stu-id="61c40-158">SPAs make extensive use of web APIs to query and update data as users interact with the application.</span></span>

## <a name="decision-table--traditional-web-or-spa"></a><span data-ttu-id="61c40-159">従来の Web または SPA – 意思決定テーブル</span><span class="sxs-lookup"><span data-stu-id="61c40-159">Decision table – Traditional Web or SPA</span></span>

<span data-ttu-id="61c40-160">次の意思決定テーブルでは、従来の web アプリケーションと、SPA を選択するときに考慮する基本的な事項のいくつかまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="61c40-160">The following decision table summarizes some of the basic factors to consider when choosing between a traditional web application and a SPA.</span></span>

  | <span data-ttu-id="61c40-161">**Factor**</span><span class="sxs-lookup"><span data-stu-id="61c40-161">**Factor**</span></span> | <span data-ttu-id="61c40-162">**従来の Web アプリ**</span><span class="sxs-lookup"><span data-stu-id="61c40-162">**Traditional Web App**</span></span> | <span data-ttu-id="61c40-163">**シングル ページ アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="61c40-163">**Single Page Application**</span></span> |
  |---|---|---|
  | <span data-ttu-id="61c40-164">JavaScript または TypeScript の必要なチームに関する知識</span><span class="sxs-lookup"><span data-stu-id="61c40-164">Required Team Familiarity with JavaScript/TypeScript</span></span> | <span data-ttu-id="61c40-165">最小</span><span class="sxs-lookup"><span data-stu-id="61c40-165">**Minimal**</span></span> | <span data-ttu-id="61c40-166">**必須**</span><span class="sxs-lookup"><span data-stu-id="61c40-166">**Required**</span></span> |
  | <span data-ttu-id="61c40-167">スクリプト作成せずにブラウザーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="61c40-167">Support Browsers without Scripting</span></span> | <span data-ttu-id="61c40-168">**サポート状況**</span><span class="sxs-lookup"><span data-stu-id="61c40-168">**Supported**</span></span> | <span data-ttu-id="61c40-169">サポートされていません</span><span class="sxs-lookup"><span data-stu-id="61c40-169">**Not Supported**</span></span> |
  | <span data-ttu-id="61c40-170">最低限のクライアント側アプリケーションの動作</span><span class="sxs-lookup"><span data-stu-id="61c40-170">Minimal Client-Side Application Behavior</span></span> | <span data-ttu-id="61c40-171">**Well-Suited**</span><span class="sxs-lookup"><span data-stu-id="61c40-171">**Well-Suited**</span></span> | <span data-ttu-id="61c40-172">**過剰**</span><span class="sxs-lookup"><span data-stu-id="61c40-172">**Overkill**</span></span> |
  | <span data-ttu-id="61c40-173">豊富な複雑なユーザー インターフェイスの要件</span><span class="sxs-lookup"><span data-stu-id="61c40-173">Rich, Complex User Interface Requirements</span></span> | <span data-ttu-id="61c40-174">**制限**</span><span class="sxs-lookup"><span data-stu-id="61c40-174">**Limited**</span></span> | <span data-ttu-id="61c40-175">**Well-Suited**</span><span class="sxs-lookup"><span data-stu-id="61c40-175">**Well-Suited**</span></span> |

>[!div class="step-by-step"]
<span data-ttu-id="61c40-176">[前](モダン-web-アプリケーション-characteristics.md) [[次へ]](architectural-principles.md)</span><span class="sxs-lookup"><span data-stu-id="61c40-176">[Previous] (modern-web-applications-characteristics.md) [Next](architectural-principles.md)</span></span>
