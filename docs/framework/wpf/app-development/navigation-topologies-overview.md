---
title: ナビゲーション トポロジの概要
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 8976ba7973e4f53022846b98c47d5613fd6ba158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="b84ea-102">ナビゲーション トポロジの概要</span><span class="sxs-lookup"><span data-stu-id="b84ea-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a> <span data-ttu-id="b84ea-103">この概要でナビゲーション トポロジの概要については、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-103">This overview provides an introduction to navigation topologies in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span> <span data-ttu-id="b84ea-104">3 つの一般的なナビゲーション トポロジをサンプルと共に説明します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b84ea-105">このトピックを読む前にする必要がありますでナビゲーションを構造化の概念を[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ページ関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-105">Before reading this topic, you should be familiar with the concept of structured navigation in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] using page functions.</span></span> <span data-ttu-id="b84ea-106">これらのトピックの両方の詳細については、次を参照してください。[構造化されたナビゲーションの概要](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-106">For more information on both of these topics, see [Structured Navigation Overview](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="b84ea-107">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-107">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="b84ea-108">ナビゲーション トポロジ</span><span class="sxs-lookup"><span data-stu-id="b84ea-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
-   [<span data-ttu-id="b84ea-109">構造化ナビゲーション トポロジ</span><span class="sxs-lookup"><span data-stu-id="b84ea-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
-   [<span data-ttu-id="b84ea-110">固定線形トポロジを介したナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [<span data-ttu-id="b84ea-111">固定階層トポロジを介した動的ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [<span data-ttu-id="b84ea-112">動的に生成されたトポロジを介したナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a><span data-ttu-id="b84ea-113">ナビゲーション トポロジ</span><span class="sxs-lookup"><span data-stu-id="b84ea-113">Navigation Topologies</span></span>  
 <span data-ttu-id="b84ea-114">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、ページのナビゲーションが通常で構成されます (<xref:System.Windows.Controls.Page>) のハイパーリンクの (<xref:System.Windows.Documents.Hyperlink>) クリックされたときに、他のページに移動します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-114">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="b84ea-115">移動するページがで識別される[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)](を参照してください[WPF のパック Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="b84ea-115">Pages that are navigated to are identified by [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="b84ea-116">ページ、ハイパーリンク、表示する次の単純な例を検討し、 [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="b84ea-116">Consider the following simple example that shows pages, hyperlinks, and [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="b84ea-117">これらのページが配列、*ナビゲーション トポロジ*構造は、ページ間を移動する方法によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b84ea-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="b84ea-118">このナビゲーション トポロジは、単純なシナリオに適していますが、ナビゲーションはより複雑なトポロジを必要とすることもあり、アプリケーションの実行中にしか定義できないものもあります。</span><span class="sxs-lookup"><span data-stu-id="b84ea-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="b84ea-119">このトピックの内容の 3 つの一般的なナビゲーション トポロジ:*固定線形*、*固定階層*、および*動的に生成された*です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="b84ea-120">各ナビゲーション トポロジを持つサンプルに示されている、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]などの次の図に示すいずれか。</span><span class="sxs-lookup"><span data-stu-id="b84ea-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 <span data-ttu-id="b84ea-121">![データ項目を含むタスク ページ](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span><span class="sxs-lookup"><span data-stu-id="b84ea-121">![Task pages with data items](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")</span></span>  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a><span data-ttu-id="b84ea-122">構造化ナビゲーション トポロジ</span><span class="sxs-lookup"><span data-stu-id="b84ea-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="b84ea-123">ナビゲーション トポロジには、大きく分けて次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="b84ea-123">There are two broad types of navigation topologies:</span></span>  
  
-   <span data-ttu-id="b84ea-124">**固定トポロジ**: コンパイル時に定義され、実行時に変化しません。</span><span class="sxs-lookup"><span data-stu-id="b84ea-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="b84ea-125">固定トポロジは、シーケンスが固定されたページを線形的または階層的にナビゲートする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
-   <span data-ttu-id="b84ea-126">**動的トポロジ**: ユーザー、アプリケーション、またはシステムから収集された入力に基づいて実行時に定義されます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="b84ea-127">動的トポロジは、ページがさまざまなシーケンスでナビゲートされる可能性があるときに便利です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="b84ea-128">ナビゲーション トポロジの作成にはページを使用することもできますが、これらのサンプルではページ関数を使用しています。その理由は、ページ関数に用意されている追加サポートによって、トポロジのページ間でデータをやり取りする機能のサポートを簡略化できるためです。</span><span class="sxs-lookup"><span data-stu-id="b84ea-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="b84ea-129">固定線形トポロジを介したナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="b84ea-130">固定線形トポロジは、シーケンスが固定されている 1 つ以上のウィザード ページの構造に似ています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="b84ea-131">次の図は、固定線形トポロジを持つウィザードの高レベルの構造とフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology.</span></span>  
  
 <span data-ttu-id="b84ea-132">![ナビゲーション トポロジのダイアグラム](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span><span class="sxs-lookup"><span data-stu-id="b84ea-132">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")</span></span>  
  
 <span data-ttu-id="b84ea-133">固定線形トポロジを使用するナビゲーションの一般的な動作は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b84ea-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
-   <span data-ttu-id="b84ea-134">呼び出し元ページから起動ページにナビゲートします。起動ページでは、ウィザードを初期化し、ウィザードの最初のページにナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="b84ea-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b84ea-135">起動ページ (、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小さい<xref:System.Windows.Navigation.PageFunction%601>) が必要でないため、呼び出し元のページでは、ウィザードの最初のページを直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b84ea-136">ただし、起動ページを使用すると、ウィザードの初期化プロセスを簡略化でき、特に初期化が複雑な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b84ea-137">ユーザーは、[戻る] ボタンと [進む] ボタン (またはハイパーリンク) を使用して、ページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b84ea-138">ユーザーは、履歴を使用してページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-138">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b84ea-139">ユーザーは、[キャンセル] ボタンを押すことによって、任意のウィザード ページからウィザードをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b84ea-140">ユーザーは、ウィザードの最後のページで [完了] ボタンを押すことによって、ウィザードを受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b84ea-141">ウィザードがキャンセルされると、ウィザードは適切な結果を返し、データは返しません。</span><span class="sxs-lookup"><span data-stu-id="b84ea-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b84ea-142">ユーザーがウィザードを受け入れた場合、ウィザードは適切な結果を返し、収集したデータを返します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b84ea-143">ウィザードが完了すると (受け入れられた場合も、キャンセルされた場合も)、ウィザードを構成するページは履歴から削除されます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b84ea-144">これにより、ウィザードの各インスタンスが分離され、異常なデータや状態の発生を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="b84ea-145">固定階層トポロジを介した動的ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="b84ea-146">一部のアプリケーションでは、次の図に示されているように、ページから複数のページにナビゲートできる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b84ea-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="b84ea-147">![複数のページにナビゲートできるページ](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span><span class="sxs-lookup"><span data-stu-id="b84ea-147">![A page that can navigate to multiple pages](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")</span></span>  
  
 <span data-ttu-id="b84ea-148">この構造は固定階層トポロジと呼ばれ、通常、階層内を移動するシーケンスは、アプリケーションまたはユーザーによって実行時に決定されます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="b84ea-149">実行時に、他の複数のページにナビゲートできる階層内の各ページは、移動先ページを決定するために必要なデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="b84ea-150">次の図は、前の図に基づくいくつかの可能なナビゲーション シーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-150">The following figure illustrates one of several possible navigation sequences based on the previous figure.</span></span>  
  
 <span data-ttu-id="b84ea-151">![ナビゲーション トポロジのダイアグラム](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span><span class="sxs-lookup"><span data-stu-id="b84ea-151">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")</span></span>  
  
 <span data-ttu-id="b84ea-152">固定階層構造内のページのシーケンスは実行時に決定されますが、ユーザー エクスペリエンスは固定線形トポロジの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="b84ea-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
-   <span data-ttu-id="b84ea-153">呼び出し元ページから起動ページにナビゲートします。起動ページでは、ウィザードを初期化し、ウィザードの最初のページにナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="b84ea-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b84ea-154">起動ページ (、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小さい<xref:System.Windows.Navigation.PageFunction%601>) が必要でないため、呼び出し元のページでは、ウィザードの最初のページを直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b84ea-155">ただし、起動ページを使用すると、ウィザードの初期化プロセスを簡略化でき、特に初期化が複雑な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b84ea-156">ユーザーは、[戻る] ボタンと [進む] ボタン (またはハイパーリンク) を使用して、ページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b84ea-157">ユーザーは、履歴を使用してページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-157">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b84ea-158">ユーザーは、履歴をたどって戻ることで、ナビゲーション シーケンスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
-   <span data-ttu-id="b84ea-159">ユーザーは、[キャンセル] ボタンを押すことによって、任意のウィザード ページからウィザードをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b84ea-160">ユーザーは、ウィザードの最後のページで [完了] ボタンを押すことによって、ウィザードを受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b84ea-161">ウィザードがキャンセルされると、ウィザードは適切な結果を返し、データは返しません。</span><span class="sxs-lookup"><span data-stu-id="b84ea-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b84ea-162">ユーザーがウィザードを受け入れた場合、ウィザードは適切な結果を返し、収集したデータを返します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b84ea-163">ウィザードが完了すると (受け入れられた場合も、キャンセルされた場合も)、ウィザードを構成するページは履歴から削除されます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b84ea-164">これにより、ウィザードの各インスタンスが分離され、異常なデータや状態の発生を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="b84ea-165">動的に生成されたトポロジを介したナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b84ea-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="b84ea-166">一部のアプリケーションでは、複数のページ間を移動するシーケンスの決定にユーザー、アプリケーション、または外部データが必要になり、実行時にしか決定できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b84ea-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="b84ea-167">次の図は、基本となるナビゲーション シーケンスを持つ一連のページを示しています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-167">The following figure illustrates a set of pages with an undetermined navigation sequence.</span></span>  
  
 <span data-ttu-id="b84ea-168">![ナビゲーション トポロジのダイアグラム](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span><span class="sxs-lookup"><span data-stu-id="b84ea-168">![Navigation topology diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")</span></span>  
  
 <span data-ttu-id="b84ea-169">次の図は、実行時にユーザーによって選択されたナビゲーション シーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="b84ea-169">The next figure illustrates a navigation sequence that was chosen by the user at run time.</span></span>  
  
 <span data-ttu-id="b84ea-170">![ナビゲーションのダイアグラム](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span><span class="sxs-lookup"><span data-stu-id="b84ea-170">![Navigation diagram](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")</span></span>  
  
 <span data-ttu-id="b84ea-171">このナビゲーション シーケンスは、動的生成トポロジと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="b84ea-172">ユーザーにとっては、他のナビゲーション トポロジと同様に、ユーザー エクスペリエンスは前述のトポロジと同じです。</span><span class="sxs-lookup"><span data-stu-id="b84ea-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
-   <span data-ttu-id="b84ea-173">呼び出し元ページから起動ページにナビゲートします。起動ページでは、ウィザードを初期化し、ウィザードの最初のページにナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="b84ea-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b84ea-174">起動ページ (、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-小さい<xref:System.Windows.Navigation.PageFunction%601>) が必要でないため、呼び出し元のページでは、ウィザードの最初のページを直接呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b84ea-175">ただし、起動ページを使用すると、ウィザードの初期化プロセスを簡略化でき、特に初期化が複雑な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b84ea-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
-   <span data-ttu-id="b84ea-176">ユーザーは、[戻る] ボタンと [進む] ボタン (またはハイパーリンク) を使用して、ページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
-   <span data-ttu-id="b84ea-177">ユーザーは、履歴を使用してページ間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-177">Users can navigate between pages using the journal.</span></span>  
  
-   <span data-ttu-id="b84ea-178">ユーザーは、[キャンセル] ボタンを押すことによって、任意のウィザード ページからウィザードをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
-   <span data-ttu-id="b84ea-179">ユーザーは、ウィザードの最後のページで [完了] ボタンを押すことによって、ウィザードを受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
-   <span data-ttu-id="b84ea-180">ウィザードがキャンセルされると、ウィザードは適切な結果を返し、データは返しません。</span><span class="sxs-lookup"><span data-stu-id="b84ea-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
-   <span data-ttu-id="b84ea-181">ユーザーがウィザードを受け入れた場合、ウィザードは適切な結果を返し、収集したデータを返します。</span><span class="sxs-lookup"><span data-stu-id="b84ea-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
-   <span data-ttu-id="b84ea-182">ウィザードが完了すると (受け入れられた場合も、キャンセルされた場合も)、ウィザードを構成するページは履歴から削除されます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b84ea-183">これにより、ウィザードの各インスタンスが分離され、異常なデータや状態の発生を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="b84ea-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84ea-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="b84ea-184">See Also</span></span>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [<span data-ttu-id="b84ea-185">構造化ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="b84ea-185">Structured Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
