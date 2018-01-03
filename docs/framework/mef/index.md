---
title: MEF (Managed Extensibility Framework)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 524fa0f2d654c812189ff6863f84db81144fb48f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="68713-102">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="68713-102">Managed Extensibility Framework (MEF)</span></span>
<span data-ttu-id="68713-103">ここでは、.NET Framework 4 で導入された Managed Extensibility Framework の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="68713-103">This topic provides an overview of the Managed Extensibility Framework introduced in the .NET Framework 4.</span></span>  
  
<a name="what_is_mef"></a>   
## <a name="what-is-mef"></a><span data-ttu-id="68713-104">MEF とは</span><span class="sxs-lookup"><span data-stu-id="68713-104">What is MEF?</span></span>  
 <span data-ttu-id="68713-105">Managed Extensibility Framework (MEF) は、軽量で拡張可能なアプリケーションを作成するためのライブラリです。</span><span class="sxs-lookup"><span data-stu-id="68713-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, extensible applications.</span></span> <span data-ttu-id="68713-106">これにより、アプリケーション開発者は、拡張機能を見つけたら、それをそのまま使用できます。構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="68713-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="68713-107">拡張機能の開発者は、コードを簡単にカプセル化できるため、ハードコーディングによる脆弱な依存関係を回避できます。</span><span class="sxs-lookup"><span data-stu-id="68713-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="68713-108">MEF により、アプリケーション内だけでなく、アプリケーション間でも拡張機能を再利用できます。</span><span class="sxs-lookup"><span data-stu-id="68713-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>  
  
<a name="the_problem_of_extensibility"></a>   
## <a name="the-problem-of-extensibility"></a><span data-ttu-id="68713-109">機能拡張の問題</span><span class="sxs-lookup"><span data-stu-id="68713-109">The Problem of Extensibility</span></span>  
 <span data-ttu-id="68713-110">機能拡張のサポートを提供する必要のある大規模アプリケーションの設計担当者である場合を想像してください。</span><span class="sxs-lookup"><span data-stu-id="68713-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="68713-111">アプリケーションには数多くの小規模コンポーネントを含める必要がある可能性があり、アプリケーションはこれらを作成して実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>  
  
 <span data-ttu-id="68713-112">このような問題を解決する最も簡単な方法は、アプリケーションにコンポーネントをソース コードとして組み込み、これらのコードをコードから直接呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="68713-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span>  <span data-ttu-id="68713-113">この方法には、数多くの明らかな欠点があります。</span><span class="sxs-lookup"><span data-stu-id="68713-113">This has a number of obvious drawbacks.</span></span>  <span data-ttu-id="68713-114">最も重要な点は、ソース コードを変更することなく新しいコンポーネントを追加できないという点です。これは、Web アプリケーションなどでは許容されますが、クライアント アプリケーションでは許容されません。</span><span class="sxs-lookup"><span data-stu-id="68713-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span>  <span data-ttu-id="68713-115">同様に重要な問題点として、開発元がサードパーティであるためにコンポーネントのソース コードにアクセスできないことがあります。また、同じ理由から、サードパーティ側からの (自分が開発したコンポーネントのソース コードへの) アクセスを許可することもできません。</span><span class="sxs-lookup"><span data-stu-id="68713-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>  
  
 <span data-ttu-id="68713-116">より高度な方法として、拡張ポイントまたはインターフェイスを提供して、アプリケーションとそのコンポーネントを切り離すことを許可する方法があります。</span><span class="sxs-lookup"><span data-stu-id="68713-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span>  <span data-ttu-id="68713-117">このモデルでは、必要に応じて、コンポーネントによって実装可能なインターフェイスと、そのインターフェイスがアプリケーションと対話するための API を提供できます。</span><span class="sxs-lookup"><span data-stu-id="68713-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span>  <span data-ttu-id="68713-118">これにより、ソース コードへのアクセスが必要になるという問題は解決されますが、この方法そのものにまだ問題があります。</span><span class="sxs-lookup"><span data-stu-id="68713-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>  
  
 <span data-ttu-id="68713-119">アプリケーションには独自にコンポーネントを検出する機能がないため、アプリケーションに対して使用可能なコンポーネントと読み込む必要のあるコンポーネントを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span>  <span data-ttu-id="68713-120">これは、通常、構成ファイルに使用可能なコンポーネントを明示的に登録することで指定します。</span><span class="sxs-lookup"><span data-stu-id="68713-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="68713-121">これは、登録されたコンポーネントが正しいことが想定されることにより、特に開発者ではなくエンド ユーザーが更新を行う場合は、保守の問題が生じることを意味します。</span><span class="sxs-lookup"><span data-stu-id="68713-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>  
  
 <span data-ttu-id="68713-122">さらに、アプリケーション自体の厳密に定義されたチャネルを介する場合を除き、コンポーネントは相互に通信することができません。</span><span class="sxs-lookup"><span data-stu-id="68713-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span>  <span data-ttu-id="68713-123">アプリケーションの設計担当者が特定の通信の必要性が生じる状況を想定しなかった場合、通常、通信は不可能です。</span><span class="sxs-lookup"><span data-stu-id="68713-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>  
  
 <span data-ttu-id="68713-124">最後に、コンポーネントの開発者は、どのアセンブリが実装するインターフェイスを含んでいるかに対するハードコーディングによる依存関係を許容する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span>  <span data-ttu-id="68713-125">これにより、1 つのコンポーネントを複数のアプリケーションで使用することが困難となり、コンポーネントのテスト フレームワークを作成するときに問題が生じる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="68713-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>  
  
<a name="what_mef_provides"></a>   
## <a name="what-mef-provides"></a><span data-ttu-id="68713-126">MEF が提供する機能</span><span class="sxs-lookup"><span data-stu-id="68713-126">What MEF Provides</span></span>  
 <span data-ttu-id="68713-127">MEF が暗黙的に検出する方法を提供する使用可能なコンポーネントの明示的なこの登録ではなくを介して*コンポジション*です。</span><span class="sxs-lookup"><span data-stu-id="68713-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span>  <span data-ttu-id="68713-128">呼ばれる、MEF コンポーネント、*一部*宣言によって、両方の依存関係を指定します (と呼ばれる*インポート*) とどのような機能 (と呼ばれる*エクスポート*) 使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="68713-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="68713-129">パートが作成されると、MEF 合成エンジンは、他のパートから使用可能なパートでそのインポートを満たします。</span><span class="sxs-lookup"><span data-stu-id="68713-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>  
  
 <span data-ttu-id="68713-130">この方法により、前のセクションで説明した問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="68713-130">This approach solves the problems discussed in the previous section.</span></span>  <span data-ttu-id="68713-131">MEF パートは、その機能を宣言的に指定するため、実行時に検出できます。これは、アプリケーションがハードコーディングされた参照または脆弱な構成ファイルを使用せずにパートを使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="68713-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span>  <span data-ttu-id="68713-132">MEF を使用すると、アプリケーションは、メタデータを使用してパートを検出し、検証することができます。これらのパートをインスタンス化したり、そのアセンブリを読み込んだりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68713-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="68713-133">結果として、拡張機能がいつどのように読み込まれる必要があるかを慎重に指定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="68713-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>  
  
 <span data-ttu-id="68713-134">パートは、それが提供するエクスポートに加えて、他のパートで満たされるインポートを指定できます。</span><span class="sxs-lookup"><span data-stu-id="68713-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span>  <span data-ttu-id="68713-135">これにより、パート間の通信が可能になるだけでなく、簡単になり、コードのファクタリングが可能になります。</span><span class="sxs-lookup"><span data-stu-id="68713-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="68713-136">たとえば、多くのコンポーネントに共通のサービスを個々のパートにファクタリングして、簡単に変更したり置換したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="68713-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>  
  
 <span data-ttu-id="68713-137">MEF モデルでは、特定のアプリケーション アセンブリでハードコーディングによる依存関係を指定する必要がないため、アプリケーション間で拡張機能を再利用できます。</span><span class="sxs-lookup"><span data-stu-id="68713-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span>  <span data-ttu-id="68713-138">これによってテスト ハーネスの開発も容易になり、アプリケーションに依存せずに拡張コンポーネントをテストできます。</span><span class="sxs-lookup"><span data-stu-id="68713-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>  
  
 <span data-ttu-id="68713-139">MEF を使用して記述された拡張アプリケーションは、拡張コンポーネントで満たすことのできるインポートを宣言できます。また、拡張機能に対してアプリケーション サービスを公開するためにエクスポートを宣言できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="68713-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span>  <span data-ttu-id="68713-140">各拡張コンポーネントは、エクスポートを宣言するだけではなく、インポートを宣言することもあります。</span><span class="sxs-lookup"><span data-stu-id="68713-140">Each extension component declares an export, and may also declare imports.</span></span>  <span data-ttu-id="68713-141">こうすると、拡張コンポーネント自体が自動的に拡張可能になります。</span><span class="sxs-lookup"><span data-stu-id="68713-141">In this way, extension components themselves are automatically extensible.</span></span>  
  
<a name="where_is_mef_available"></a>   
## <a name="where-is-mef-available"></a><span data-ttu-id="68713-142">MEF を使用できる環境</span><span class="sxs-lookup"><span data-stu-id="68713-142">Where Is MEF Available?</span></span>  
 <span data-ttu-id="68713-143">MEF は、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] の不可欠な構成要素であり、.NET Framework が使用されている環境であればどのような環境でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="68713-143">MEF is an integral part of the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], and is available wherever the .NET Framework is used.</span></span>  <span data-ttu-id="68713-144">MEF は、Windows フォームや WPF などのテクノロジを使用するクライアント アプリケーション、または ASP.NET を使用するサーバー アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="68713-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>  
  
<a name="mef_and_maf"></a>   
## <a name="mef-and-maf"></a><span data-ttu-id="68713-145">MEF と MAF</span><span class="sxs-lookup"><span data-stu-id="68713-145">MEF and MAF</span></span>  
 <span data-ttu-id="68713-146">アプリケーションが拡張機能を特定および管理できるように設計された MAF (Managed Add-in Framework) は、以前のバージョンの .NET Framework で導入されました。</span><span class="sxs-lookup"><span data-stu-id="68713-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span>  <span data-ttu-id="68713-147">MAF では MEF と比較してやや高度なレベルに重点が置かれており、MEF では発見可能性、拡張性、および移植性に重点が置かれているのに対し、MAF では拡張機能の特定とアセンブリの読み込みおよびアンロードに重点が置かれています。</span><span class="sxs-lookup"><span data-stu-id="68713-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span>  <span data-ttu-id="68713-148">この 2 つのフレームワークは円滑に相互運用でき、1 つのアプリケーションで両方を活用することができます。</span><span class="sxs-lookup"><span data-stu-id="68713-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>  
  
<a name="simplecalculator_an_example_application"></a>   
## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="68713-149">SimpleCalculator: サンプル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="68713-149">SimpleCalculator: An Example Application</span></span>  
 <span data-ttu-id="68713-150">MEF が実行できる処理を理解する最も簡単な方法は、単純な MEF アプリケーションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="68713-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="68713-151">この例では、SimpleCalculator という名前の単純な電卓を作成します。</span><span class="sxs-lookup"><span data-stu-id="68713-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="68713-152">SimpleCalculator の目的は、"5+3" や "6-2" などの形式で基本的な算術命令を受け取り、正しい答えを返すコンソール アプリケーションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="68713-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="68713-153">MEF を使用すると、アプリケーション コードを変更せずに、新しい演算子を追加できます。</span><span class="sxs-lookup"><span data-stu-id="68713-153">Using MEF, you will be able to add new operators without changing the application code.</span></span>  
  
 <span data-ttu-id="68713-154">この例の完全なコードをダウンロードするを参照してください。、 [SimpleCalculator のサンプル](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e)です。</span><span class="sxs-lookup"><span data-stu-id="68713-154">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68713-155">SimpleCalculator を作成する目的は、これを使用する実際のシナリオを必ずしも提供することではなく、MEF の概念と構文を示すことにあります。</span><span class="sxs-lookup"><span data-stu-id="68713-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="68713-156">MEF の機能を最大限に活用できるアプリケーションの多くは、SimpleCalculator よりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="68713-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="68713-157">広範な例については、次を参照してください。、 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) GitHub でします。</span><span class="sxs-lookup"><span data-stu-id="68713-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>
  
 <span data-ttu-id="68713-158">まず、 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)]、という名前の新しいコンソール アプリケーション プロジェクトを作成する`SimpleCalculator`です。</span><span class="sxs-lookup"><span data-stu-id="68713-158">To start, in [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], create a new Console Application project named `SimpleCalculator`.</span></span> <span data-ttu-id="68713-159">MEF が存在する System.ComponentModel.Composition アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-159">Add a reference to the System.ComponentModel.Composition assembly, where MEF resides.</span></span> <span data-ttu-id="68713-160">Module1.vb または Program.cs を開き、System.ComponentModel.Composition および System.ComponentModel.Composition.Hosting の `Imports` ステートメントまたは `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-160">Open Module1.vb or Program.cs and add `Imports` or `using` statements for System.ComponentModel.Composition and System.ComponentModel.Composition.Hosting.</span></span> <span data-ttu-id="68713-161">これらの 2 つの名前空間には、拡張可能なアプリケーションの開発に必要な MEF 型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="68713-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span> <span data-ttu-id="68713-162">Visual Basic では、`Public` モジュールを宣言する行に `Module1` キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-162">In Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>  
  
<a name="composition_container_and_catalogs"></a>   
## <a name="composition-container-and-catalogs"></a><span data-ttu-id="68713-163">合成コンテナーとカタログ</span><span class="sxs-lookup"><span data-stu-id="68713-163">Composition Container and Catalogs</span></span>  
 <span data-ttu-id="68713-164">MEF 合成モデルの中核を成すは、*合成コンテナー*、使用可能なすべてのパートが含まれ、合成を実行します。</span><span class="sxs-lookup"><span data-stu-id="68713-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span>  <span data-ttu-id="68713-165">(つまり、インポートとエクスポートの組み合わせ)。最も一般的な種類の合成コンテナーは <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> で、SimpleCalculator にはこれを使用します </span><span class="sxs-lookup"><span data-stu-id="68713-165">(That is, the matching up of imports to exports.)  The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you will use this for SimpleCalculator.</span></span>  
  
 <span data-ttu-id="68713-166">Visual Basic では、Module1.vb に `Program` という名前のパブリック クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-166">In Visual Basic, in Module1.vb, add a public class named `Program`.</span></span> <span data-ttu-id="68713-167">それから、Module1.vb ファイルまたは Program.cs ファイルの `Program` クラスに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-167">Then add the following line to the `Program` class in Module1.vb or Program.cs:</span></span>  
  
```vb  
Dim _container As CompositionContainer  
```  
  
```csharp  
private CompositionContainer _container;  
```  
  
 <span data-ttu-id="68713-168">合成コンテナーに使用可能なパートを検出するために使用する*カタログ*です。</span><span class="sxs-lookup"><span data-stu-id="68713-168">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="68713-169">カタログは、いくつかのソースから使用できるパートを検出するためのオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="68713-169">A catalog is an object that makes available parts discovered from some source.</span></span>  <span data-ttu-id="68713-170">MEF では、指定された型、アセンブリ、またはディレクトリからパートを検出するカタログを提供します。</span><span class="sxs-lookup"><span data-stu-id="68713-170">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="68713-171">アプリケーション開発者は、Web サービスなどの他のソースからパートを検出する新しいカタログを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="68713-171">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>  
  
 <span data-ttu-id="68713-172">`Program` クラスに次のコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-172">Add the following constructor to the `Program` class:</span></span>  
  
```vb  
Public Sub New()  
    'An aggregate catalog that combines multiple catalogs  
     Dim catalog = New AggregateCatalog()  
  
    'Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))  
  
    'Create the CompositionContainer with the parts in the catalog  
    _container = New CompositionContainer(catalog)  
  
    'Fill the imports of this object  
    Try  
        _container.ComposeParts(Me)  
    Catch ex As Exception  
        Console.WriteLine(ex.ToString)  
    End Try  
End Sub  
```  
  
```csharp  
private Program()  
{  
    //An aggregate catalog that combines multiple catalogs  
    var catalog = new AggregateCatalog();  
    //Adds all the parts found in the same assembly as the Program class  
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));  
  
    //Create the CompositionContainer with the parts in the catalog  
    _container = new CompositionContainer(catalog);  
  
    //Fill the imports of this object  
    try  
    {  
        this._container.ComposeParts(this);  
    }  
    catch (CompositionException compositionException)  
    {  
        Console.WriteLine(compositionException.ToString());  
   }  
}  
```  
  
 <span data-ttu-id="68713-173"><xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> を呼び出すことで、合成コンテナーに対して特定のパート セット (この例では `Program` の現在のインスタンス) を合成するように指示します。</span><span class="sxs-lookup"><span data-stu-id="68713-173">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="68713-174">ただし、この時点では、`Program` に満たす必要のあるインポートがないため、何も実行されません。</span><span class="sxs-lookup"><span data-stu-id="68713-174">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>  
  
<a name="imports_and_exports_with_attributes"></a>   
## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="68713-175">属性を使用したインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="68713-175">Imports and Exports with Attributes</span></span>  
 <span data-ttu-id="68713-176">まず、`Program` で電卓をインポートします。</span><span class="sxs-lookup"><span data-stu-id="68713-176">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="68713-177">これにより、`Program` に渡されるコンソール入力やコンソール出力などのユーザー インターフェイスに関連する要素が電卓のロジックから切り離されます。</span><span class="sxs-lookup"><span data-stu-id="68713-177">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>  
  
 <span data-ttu-id="68713-178">`Program` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-178">Add the following code to the `Program` class:</span></span>  
  
```vb  
<Import(GetType(ICalculator))>  
Public Property calculator As ICalculator  
```  
  
```csharp  
[Import(typeof(ICalculator))]  
public ICalculator calculator;  
```  
  
 <span data-ttu-id="68713-179">`calculator` オブジェクトの宣言に特に変わった点はありませんが、<xref:System.ComponentModel.Composition.ImportAttribute> 属性で装飾されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68713-179">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span>  <span data-ttu-id="68713-180">この属性は、インポートとなるもの、つまり、オブジェクトが合成されると合成エンジンによって満たされるものを宣言します。</span><span class="sxs-lookup"><span data-stu-id="68713-180">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>  
  
 <span data-ttu-id="68713-181">すべてのインポートは、*コントラクト*、これにより、対応するエクスポートが決定されます。</span><span class="sxs-lookup"><span data-stu-id="68713-181">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="68713-182">コントラクトは、明示的に指定された文字列であったり、指定された型に基づいて MEF によって自動的に生成されたりします (この例では、`ICalculator` というインターフェイス)。</span><span class="sxs-lookup"><span data-stu-id="68713-182">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span>  <span data-ttu-id="68713-183">対応するコントラクトで宣言されたエクスポートが、このインポートを満たします。</span><span class="sxs-lookup"><span data-stu-id="68713-183">Any export declared with a matching contract will fulfill this import.</span></span>  <span data-ttu-id="68713-184">`calculator` オブジェクトの型は実際には `ICalculator` ですが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="68713-184">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="68713-185">コントラクトは、インポートするオブジェクトの型に依存しません。</span><span class="sxs-lookup"><span data-stu-id="68713-185">The contract is independent from the type of the importing object.</span></span>  <span data-ttu-id="68713-186">この例では、`typeof(ICalculator)` は省略できます。</span><span class="sxs-lookup"><span data-stu-id="68713-186">(In this case, you could leave out the `typeof(ICalculator)`.</span></span>  <span data-ttu-id="68713-187">MEF では、明示的に指定しない限り、インポートの型に基づいて自動的にコントラクトが想定されます。</span><span class="sxs-lookup"><span data-stu-id="68713-187">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>  
  
 <span data-ttu-id="68713-188">次のように、この単純なインターフェイスをモジュールまたは `SimpleCalculator` 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-188">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>  
  
```vb  
Public Interface ICalculator  
    Function Calculate(ByVal input As String) As String  
End Interface  
```  
  
```csharp  
public interface ICalculator  
{  
    String Calculate(String input);  
}  
```  
  
 <span data-ttu-id="68713-189">`ICalculator` を定義したので、これを実装するクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="68713-189">Now that you have defined `ICalculator`, you need a class that implements it.</span></span>  <span data-ttu-id="68713-190">モジュールまたは `SimpleCalculator` 名前空間に次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-190">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
```vb  
<Export(GetType(ICalculator))>  
Public Class MySimpleCalculator  
   Implements ICalculator  
  
End Class  
```  
  
```csharp  
[Export(typeof(ICalculator))]  
class MySimpleCalculator : ICalculator  
{  
  
}  
```  
  
 <span data-ttu-id="68713-191">これが、`Program` でインポートに対応するエクスポートになります。</span><span class="sxs-lookup"><span data-stu-id="68713-191">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="68713-192">エクスポートがインポートと一致するには、エクスポートで同じコントラクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-192">In order for the export to match the import, the export must have the same contract.</span></span>  <span data-ttu-id="68713-193">`typeof(MySimpleCalculator)` に基づいてコントラクトでエクスポートすると、不一致が発生し、インポートは満たされません。コントラクトは正確に対応している必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-193">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>  
  
 <span data-ttu-id="68713-194">合成コンテナーはこのアセンブリで使用可能なすべてのパートを使用して設定されるため、`MySimpleCalculator` パートが使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="68713-194">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span>  <span data-ttu-id="68713-195">`Program` のコンストラクターが `Program` オブジェクトで合成を実行するとき、そのインポートは、それを満たすために作成される `MySimpleCalculator` オブジェクトで満たされます。</span><span class="sxs-lookup"><span data-stu-id="68713-195">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>  
  
 <span data-ttu-id="68713-196">ユーザー インターフェイス レイヤー (`Program`) がそれ以外のことを認識する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68713-196">The user interface layer (`Program`) does not need to know anything else.</span></span>  <span data-ttu-id="68713-197">したがって、`Main` メソッド内の残りのユーザー インターフェイス ロジックを記述できます。</span><span class="sxs-lookup"><span data-stu-id="68713-197">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>  
  
 <span data-ttu-id="68713-198">`Main` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-198">Add the following code to the `Main` method:</span></span>  
  
```vb  
Sub Main()  
    Dim p As New Program()  
    Dim s As String  
    Console.WriteLine("Enter Command:")  
    While (True)  
        s = Console.ReadLine()  
        Console.WriteLine(p.calculator.Calculate(s))  
    End While  
End Sub  
```  
  
```csharp  
static void Main(string[] args)  
{  
    Program p = new Program(); //Composition is performed in the constructor  
    String s;  
    Console.WriteLine("Enter Command:");  
    while (true)  
    {  
        s = Console.ReadLine();  
        Console.WriteLine(p.calculator.Calculate(s));  
    }  
}  
```  
  
 <span data-ttu-id="68713-199">このコードは、単純に入力行を読み取り、結果に対して `Calculate` の `ICalculator` 関数を呼び出して、結果をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="68713-199">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="68713-200">これが、`Program` で必要なすべてのコードです。</span><span class="sxs-lookup"><span data-stu-id="68713-200">That is all the code you need in `Program`.</span></span>  <span data-ttu-id="68713-201">その他の処理は、パート内で行われます。</span><span class="sxs-lookup"><span data-stu-id="68713-201">All the rest of the work will happen in the parts.</span></span>  
  
<a name="further_imports_and_importmany"></a>   
## <a name="further-imports-and-importmany"></a><span data-ttu-id="68713-202">その他のインポートと ImportMany</span><span class="sxs-lookup"><span data-stu-id="68713-202">Further Imports and ImportMany</span></span>  
 <span data-ttu-id="68713-203">SimpleCalculator に拡張性を持たせるためには、演算の一覧をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-203">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="68713-204">通常の <xref:System.ComponentModel.Composition.ImportAttribute> 属性は、1 つの <xref:System.ComponentModel.Composition.ExportAttribute> だけで満たされます。</span><span class="sxs-lookup"><span data-stu-id="68713-204">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span>  <span data-ttu-id="68713-205">使用可能なエクスポートが複数あれば、合成エンジンでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="68713-205">If more than one is available, the composition engine produces an error.</span></span>  <span data-ttu-id="68713-206">任意の数のエクスポートで満たすことのできるインポートを作成するには、<xref:System.ComponentModel.Composition.ImportManyAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="68713-206">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>  
  
 <span data-ttu-id="68713-207">次の演算プロパティを追加、`MySimpleCalculator`クラス。</span><span class="sxs-lookup"><span data-stu-id="68713-207">Add the following operations property to the `MySimpleCalculator` class:</span></span>  
  
```vb  
<ImportMany()>  
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))  
```  
  
```csharp  
[ImportMany]  
IEnumerable<Lazy<IOperation, IOperationData>> operations;  
```  
  
 <span data-ttu-id="68713-208"><xref:System.Lazy%602> は、エクスポートの間接参照を格納するために MEF に用意されている型です。</span><span class="sxs-lookup"><span data-stu-id="68713-208"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span>  <span data-ttu-id="68713-209">ここで、エクスポートされたオブジェクト自体に加えて、取得することも*メタデータのエクスポート*、エクスポートされるオブジェクトについて説明する情報。</span><span class="sxs-lookup"><span data-stu-id="68713-209">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="68713-210">各 <xref:System.Lazy%602> には、実際の操作を表す `IOperation` オブジェクト、およびそのメタデータを表す `IOperationData` オブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68713-210">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>  
  
 <span data-ttu-id="68713-211">次の単純なインターフェイスをモジュールまたは `SimpleCalculator` 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-211">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>  
  
```vb  
Public Interface IOperation  
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer  
End Interface  
  
Public Interface IOperationData  
    ReadOnly Property Symbol As Char  
End Interface  
```  
  
```csharp  
public interface IOperation  
{  
     int Operate(int left, int right);  
}  
  
public interface IOperationData  
{  
    Char Symbol { get; }  
}  
```  
  
 <span data-ttu-id="68713-212">ここでは、各演算のメタデータは、演算を表す +、-、* などの記号です。</span><span class="sxs-lookup"><span data-stu-id="68713-212">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, *, and so on.</span></span> <span data-ttu-id="68713-213">加算の演算を使用可能にするには、次のクラスをモジュールまたは `SimpleCalculator` 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-213">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "+"c)>  
Public Class Add  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left + right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(IOperation))]  
[ExportMetadata("Symbol", '+')]  
class Add: IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left + right;  
    }  
}  
```  
  
 <span data-ttu-id="68713-214"><xref:System.ComponentModel.Composition.ExportAttribute> 属性は、以前と同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="68713-214">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span>  <span data-ttu-id="68713-215"><xref:System.ComponentModel.Composition.ExportMetadataAttribute> 属性は、そのエクスポートに対し、名前と値のペアの形式でメタデータをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="68713-215">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span>  <span data-ttu-id="68713-216">`Add` クラスは `IOperation` を実装していますが、`IOperationData` を実装するクラスは明示的に定義されていません。</span><span class="sxs-lookup"><span data-stu-id="68713-216">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="68713-217">代わりに、提供されるメタデータの名前に基づくプロパティを使用して、MEF によってクラスが暗黙的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="68713-217">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span>  <span data-ttu-id="68713-218">(MEF でメタデータにアクセスする方法にはいくつかありますが、これはその 1 つです)。</span><span class="sxs-lookup"><span data-stu-id="68713-218">(This is one of several ways to access metadata in MEF.)</span></span>  
  
 <span data-ttu-id="68713-219">MEF での合成は*再帰*です。</span><span class="sxs-lookup"><span data-stu-id="68713-219">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="68713-220">先ほど、`Program` オブジェクトを明示的に合成しました。これは `ICalculator` をインポートし、その型は `MySimpleCalculator` であることが判明しました。</span><span class="sxs-lookup"><span data-stu-id="68713-220">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span>  <span data-ttu-id="68713-221">この `MySimpleCalculator` は `IOperation` オブジェクトのコレクションをインポートし、このインポートは `MySimpleCalculator` が作成されるときに `Program` のインポートと同時に満たされます。</span><span class="sxs-lookup"><span data-stu-id="68713-221">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="68713-222">`Add` クラスがさらに別のインポートを宣言している場合は、そのインポートも満たされる必要があり、宣言されているインポートごとにそれが繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="68713-222">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="68713-223">満たされないインポートが残ると、合成エラーが発生します </span><span class="sxs-lookup"><span data-stu-id="68713-223">Any import left unfilled results in a composition error.</span></span>  <span data-ttu-id="68713-224">(省略可能なインポートを宣言する、またはそれらに既定値を割り当てることはできます)。</span><span class="sxs-lookup"><span data-stu-id="68713-224">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>  
  
<a name="calculator_logic"></a>   
## <a name="calculator-logic"></a><span data-ttu-id="68713-225">電卓のロジック</span><span class="sxs-lookup"><span data-stu-id="68713-225">Calculator Logic</span></span>  
 <span data-ttu-id="68713-226">3 つのパートを作成したので、残っている作業は電卓ロジックを作成することです。</span><span class="sxs-lookup"><span data-stu-id="68713-226">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="68713-227">`MySimpleCalculator` クラスに次のコードを追加して、`Calculate` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="68713-227">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>  
  
```vb  
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate  
    Dim left, right As Integer  
    Dim operation As Char  
    Dim fn = FindFirstNonDigit(input) 'Finds the operator  
    If fn < 0 Then  
        Return "Could not parse command."  
    End If  
    operation = input(fn)  
    Try  
        left = Integer.Parse(input.Substring(0, fn))  
        right = Integer.Parse(input.Substring(fn + 1))  
    Catch ex As Exception  
        Return "Could not parse command."  
    End Try  
    For Each i As Lazy(Of IOperation, IOperationData) In operations  
        If i.Metadata.symbol = operation Then  
            Return i.Value.Operate(left, right).ToString()  
        End If  
    Next  
    Return "Operation not found!"  
End Function  
```  
  
```csharp  
public String Calculate(String input)  
{  
    int left;  
    int right;  
    Char operation;  
    int fn = FindFirstNonDigit(input); //finds the operator  
    if (fn < 0) return "Could not parse command.";  
  
    try  
    {  
        //separate out the operands  
        left = int.Parse(input.Substring(0, fn));  
        right = int.Parse(input.Substring(fn + 1));  
    }  
    catch   
    {  
        return "Could not parse command.";  
    }  
  
    operation = input[fn];  
  
    foreach (Lazy<IOperation, IOperationData> i in operations)  
    {  
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();  
    }  
    return "Operation Not Found!";  
}  
```  
  
 <span data-ttu-id="68713-228">1 つ目のステップでは、入力文字列が解析され、左オペランド、右オペランド、および演算子文字が特定されます。</span><span class="sxs-lookup"><span data-stu-id="68713-228">The initial steps parse the input string into left and right operands and an operator character.</span></span>  <span data-ttu-id="68713-229">`foreach` ループでは、`operations` コレクションのすべてのメンバーが検証されます。</span><span class="sxs-lookup"><span data-stu-id="68713-229">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="68713-230">これらのオブジェクトの型は <xref:System.Lazy%602> です。またそのメタデータ値とエクスポートされるオブジェクトにはそれぞれ <xref:System.Lazy%602.Metadata%2A> プロパティと <xref:System.Lazy%601.Value%2A> プロパティでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="68713-230">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="68713-231">この場合、`Symbol` オブジェクトの `IOperationData` プロパティが一致することが検出されると、電卓は `Operate` オブジェクトの `IOperation` メソッドを呼び出し、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="68713-231">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>  
  
 <span data-ttu-id="68713-232">電卓を完成させるには、文字列内で最初に出現する数字以外の文字の位置を返すヘルパー メソッドも必要です。</span><span class="sxs-lookup"><span data-stu-id="68713-232">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span>  <span data-ttu-id="68713-233">`MySimpleCalculator` クラスに次のヘルパー メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-233">Add the following helper method to the `MySimpleCalculator` class:</span></span>  
  
```vb  
Private Function FindFirstNonDigit(ByVal s As String) As Integer  
    For i = 0 To s.Length  
        If (Not (Char.IsDigit(s(i)))) Then Return i  
    Next  
    Return -1  
End Function  
```  
  
```csharp  
private int FindFirstNonDigit(String s)  
{  
    for (int i = 0; i < s.Length; i++)  
    {  
        if (!(Char.IsDigit(s[i]))) return i;  
    }  
    return -1;  
}  
```  
  
 <span data-ttu-id="68713-234">これで、プロジェクトをコンパイルして実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="68713-234">You should now be able to compile and run the project.</span></span> <span data-ttu-id="68713-235">Visual Basic の場合、`Public` に `Module1` キーワードを追加していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="68713-235">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="68713-236">コンソール ウィンドウで "5+3" などの加算演算を入力すると、電卓が結果を返します。</span><span class="sxs-lookup"><span data-stu-id="68713-236">In the console window, type an addition operation, such as "5+3", and the calculator will return the results.</span></span>  <span data-ttu-id="68713-237">その他の演算子は、"Operation Not Found!"になります</span><span class="sxs-lookup"><span data-stu-id="68713-237">Any other operator will result in the "Operation Not Found!"</span></span> <span data-ttu-id="68713-238">メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="68713-238">message.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_class"></a>   
## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="68713-239">新しいクラスを使用した SimpleCalculator の拡張</span><span class="sxs-lookup"><span data-stu-id="68713-239">Extending SimpleCalculator Using A New Class</span></span>  
 <span data-ttu-id="68713-240">これで、電卓が機能するようになりました。新しい演算の追加は簡単です。</span><span class="sxs-lookup"><span data-stu-id="68713-240">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="68713-241">モジュールまたは `SimpleCalculator` 名前空間に次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-241">Add the following class to the module or `SimpleCalculator` namespace:</span></span>  
  
```vb  
<Export(GetType(IOperation))>  
<ExportMetadata("Symbol", "-"c)>  
Public Class Subtract  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left - right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(IOperation))]  
[ExportMetadata("Symbol", '-')]  
class Subtract : IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left - right;  
    }  
}  
```  
  
 <span data-ttu-id="68713-242">プロジェクトをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="68713-242">Compile and run the project.</span></span> <span data-ttu-id="68713-243">"5-3" などの減算演算を入力します。</span><span class="sxs-lookup"><span data-stu-id="68713-243">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="68713-244">電卓は、加算だけでなく減算もサポートするようになりました。</span><span class="sxs-lookup"><span data-stu-id="68713-244">The calculator now supports subtraction as well as addition.</span></span>  
  
<a name="extending_simplecalculator_using_a_new_assembly"></a>   
## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="68713-245">新しいアセンブリを使用した SimpleCalculator の拡張</span><span class="sxs-lookup"><span data-stu-id="68713-245">Extending SimpleCalculator Using A New Assembly</span></span>  
 <span data-ttu-id="68713-246">ソース コードにクラスを追加するのは簡単ですが、MEF には、アプリケーション独自のソースの外部でパートを検索する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="68713-246">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="68713-247">この例を示すためには、<xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> を追加することで、独自のアセンブリだけではなくディレクトリでもパートを検索するように SimpleCalculator を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-247">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>  
  
 <span data-ttu-id="68713-248">という名前の新しいディレクトリを追加`Extensions`SimpleCalculator プロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="68713-248">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span>  <span data-ttu-id="68713-249">これは、アプリケーション レベルではなく、プロジェクト レベルで追加してください。</span><span class="sxs-lookup"><span data-stu-id="68713-249">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="68713-250">という名前のソリューションに新しいクラス ライブラリ プロジェクトを追加`ExtendedOperations`です。</span><span class="sxs-lookup"><span data-stu-id="68713-250">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="68713-251">新しいプロジェクトをコンパイルし、個別のアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="68713-251">The new project will compile into a separate assembly.</span></span>  
  
 <span data-ttu-id="68713-252">ExtendedOperations プロジェクトのプロジェクト プロパティ デザイナーを開き、をクリックして、**コンパイル**または**ビルド**タブです。変更、**ビルド出力パス**または**出力パス**SimpleCalculator プロジェクト ディレクトリの Extensions ディレクトリを指す (..\SimpleCalculator\Extensions\\)。</span><span class="sxs-lookup"><span data-stu-id="68713-252">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (..\SimpleCalculator\Extensions\\).</span></span>  
  
 <span data-ttu-id="68713-253">Module1.vb または Program.cs で、`Program` コンストラクターに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-253">In Module1.vb or Program.cs, add the following line to the `Program` constructor:</span></span>  
  
```vb  
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))  
```  
  
```csharp  
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));  
```  
  
 <span data-ttu-id="68713-254">例に示されているパスを、Extensions ディレクトリのパスに置き換えます </span><span class="sxs-lookup"><span data-stu-id="68713-254">Replace the example path with the path to your Extensions directory.</span></span>  <span data-ttu-id="68713-255">(この絶対パスはデバッグにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="68713-255">(This absolute path is for debugging purposes only.</span></span>  <span data-ttu-id="68713-256">実稼働アプリケーションでは、相対パスを使用します)。これで、<xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> により、Extensions ディレクトリ内のアセンブリで見つかったすべてのパートが合成コンテナーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="68713-256">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>  
  
 <span data-ttu-id="68713-257">ExtendedOperations プロジェクトで、SimpleCalculator と System.ComponentModel.Composition への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-257">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="68713-258">ExtendedOperations クラス ファイルで、System.ComponentModel.Composition の `Imports` ステートメントまたは `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-258">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="68713-259">Visual Basic では、SimpleCalculator の `Imports` ステートメントも追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-259">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="68713-260">次に、ExtendedOperations クラス ファイルに次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="68713-260">Then add the following class to the ExtendedOperations class file:</span></span>  
  
```vb  
<Export(GetType(SimpleCalculator.IOperation))>  
<ExportMetadata("Symbol", "%"c)>  
Public Class Modulo  
    Implements IOperation  
  
    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate  
        Return left Mod right  
    End Function  
End Class  
```  
  
```csharp  
[Export(typeof(SimpleCalculator.IOperation))]  
[ExportMetadata("Symbol", '%')]  
public class Mod : SimpleCalculator.IOperation  
{  
    public int Operate(int left, int right)  
    {  
        return left % right;  
    }  
}  
```  
  
 <span data-ttu-id="68713-261">コントラクトを対応させるには、<xref:System.ComponentModel.Composition.ExportAttribute> 属性が <xref:System.ComponentModel.Composition.ImportAttribute> と同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="68713-261">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>  
  
 <span data-ttu-id="68713-262">プロジェクトをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="68713-262">Compile and run the project.</span></span> <span data-ttu-id="68713-263">新しい Mod (%) 演算子をテストします。</span><span class="sxs-lookup"><span data-stu-id="68713-263">Test the new Mod (%) operator.</span></span>  
  
<a name="conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="68713-264">まとめ</span><span class="sxs-lookup"><span data-stu-id="68713-264">Conclusion</span></span>  
 <span data-ttu-id="68713-265">ここでは、MEF の基本的な概念について説明しました。</span><span class="sxs-lookup"><span data-stu-id="68713-265">This topic covered the basic concepts of MEF.</span></span>  
  
-   <span data-ttu-id="68713-266">パート、カタログ、および合成コンテナー</span><span class="sxs-lookup"><span data-stu-id="68713-266">Parts, catalogs, and the composition container</span></span>  
  
     <span data-ttu-id="68713-267">パートと合成コンテナーは、MEF アプリケーションの基本のビルド ブロックです。</span><span class="sxs-lookup"><span data-stu-id="68713-267">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="68713-268">パートは、それ自体までの (自身を含む) 値をインポートまたはエクスポートするオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="68713-268">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="68713-269">カタログは、特定のソースからのパートのコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="68713-269">A catalog provides a collection of parts from a particular source.</span></span>  <span data-ttu-id="68713-270">合成コンテナーは、カタログによって提供されるパートを使用して合成 (インポートのエクスポートへの結合) を実行します。</span><span class="sxs-lookup"><span data-stu-id="68713-270">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>  
  
-   <span data-ttu-id="68713-271">インポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="68713-271">Imports and exports</span></span>  
  
     <span data-ttu-id="68713-272">インポートとエクスポートは、コンポーネントが通信を行う手段です。</span><span class="sxs-lookup"><span data-stu-id="68713-272">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="68713-273">インポートを使用して、コンポーネントは特定の値またはオブジェクトが必要であることを指定します。エクスポートを使用して、コンポーネントは値が使用可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="68713-273">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="68713-274">各インポートは、コントラクトを通じて、エクスポートの一覧と対応付けされます。</span><span class="sxs-lookup"><span data-stu-id="68713-274">Each import is matched with a list of exports by way of its contract.</span></span>  
  
<a name="where_do_i_go_now"></a>   
## <a name="where-do-i-go-now"></a><span data-ttu-id="68713-275">次のステップ</span><span class="sxs-lookup"><span data-stu-id="68713-275">Where Do I Go Now?</span></span>  
 <span data-ttu-id="68713-276">この例の完全なコードをダウンロードするを参照してください。、 [SimpleCalculator のサンプル](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e)です。</span><span class="sxs-lookup"><span data-stu-id="68713-276">To download the complete code for this example, see the [SimpleCalculator sample](http://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e).</span></span>  
  
 <span data-ttu-id="68713-277">詳細とコード例については、次を参照してください。 [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282)です。</span><span class="sxs-lookup"><span data-stu-id="68713-277">For more information and code examples, see [Managed Extensibility Framework](http://go.microsoft.com/fwlink/?LinkId=144282).</span></span> <span data-ttu-id="68713-278">MEF 型の一覧については、<xref:System.ComponentModel.Composition?displayProperty=nameWithType> 名前空間を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68713-278">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
