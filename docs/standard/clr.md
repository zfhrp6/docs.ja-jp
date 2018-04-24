---
title: 共通言語ランタイム (CLR)
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2993fbcdc1caf73147c252a0d501e65478a3d08d
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="common-language-runtime-clr"></a><span data-ttu-id="10b5a-102">共通言語ランタイム (CLR)</span><span class="sxs-lookup"><span data-stu-id="10b5a-102">Common Language Runtime (CLR)</span></span>
<span data-ttu-id="10b5a-103">.NET Framework には、共通言語ランタイムと呼ばれるランタイム環境が用意されています。共通言語ランタイムは、コードを実行し、開発プロセスを支援するサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-103">The .NET Framework provides a run-time environment called the common language runtime, which runs the code and provides services that make the development process easier.</span></span>  
  
 <span data-ttu-id="10b5a-104">コンパイラとツールにより、共通言語ランタイムの機能が公開されることによって、このマネージ実行環境の利点を活用するコードを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-104">Compilers and tools expose the common language runtime's functionality and enable you to write code that benefits from this managed execution environment.</span></span> <span data-ttu-id="10b5a-105">このような共通言語ランタイムに対応した言語コンパイラを使用して作成したコードはマネージ コードと呼ばれます。マネージ コードは、言語間の統合、言語間の例外処理、強化されたセキュリティ、バージョン管理と配置のサポート、コンポーネント間の対話の簡易モデル、デバッグ サービスとプロファイル サービスなど、さまざまな機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-105">Code that you develop with a language compiler that targets the runtime is called managed code; it benefits from features such as cross-language integration, cross-language exception handling, enhanced security, versioning and deployment support, a simplified model for component interaction, and debugging and profiling services.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10b5a-106">型システム、メタデータの書式、およびランタイム環境 (仮想実行システム) はすべて公的な標準規格の ECMA 共通言語基盤仕様により定義されているため、コンパイラおよびツールは共通言語ランタイムが使用できる出力を生成できます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-106">Compilers and tools are able to produce output that the common language runtime can consume because the type system, the format of metadata, and the runtime environment (the virtual execution system) are all defined by a public standard, the ECMA Common Language Infrastructure specification.</span></span> <span data-ttu-id="10b5a-107">詳細については、「[ECMA C# and Common Language Infrastructure Specifications (ECMA C# および共通言語基盤の仕様)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10b5a-107">For more information, see [ECMA C# and Common Language Infrastructure Specifications](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/).</span></span>  
  
 <span data-ttu-id="10b5a-108">マネージ コードが共通言語ランタイムからサービスを受けられるようにするために、言語コンパイラは、そのコード内の型、メンバー、および参照を記述したメタデータを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-108">To enable the runtime to provide services to managed code, language compilers must emit metadata that describes the types, members, and references in your code.</span></span> <span data-ttu-id="10b5a-109">メタデータはコード内に格納されます。つまり、共通言語ランタイムの読み込み可能なすべてのポータブル実行可能 (PE) ファイルには、メタデータが含まれていることになります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-109">Metadata is stored with the code; every loadable common language runtime portable executable (PE) file contains metadata.</span></span> <span data-ttu-id="10b5a-110">共通言語ランタイムは、クラスの検索と読み込み、メモリ内でのインスタンスのレイアウト、メソッドの呼び出しの解決、ネイティブ コードの生成、セキュリティの強化、およびランタイムのコンテキスト境界の設定にメタデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-110">The runtime uses metadata to locate and load classes, lay out instances in memory, resolve method invocations, generate native code, enforce security, and set run-time context boundaries.</span></span>  
  
 <span data-ttu-id="10b5a-111">共通言語ランタイムはオブジェクトのレイアウトを自動的に処理し、それらのオブジェクトへの参照を管理し、不要になったオブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-111">The runtime automatically handles object layout and manages references to objects, releasing them when they are no longer being used.</span></span> <span data-ttu-id="10b5a-112">このような方法で有効期間を管理されるオブジェクトをマネージ データと呼びます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-112">Objects whose lifetimes are managed in this way are called managed data.</span></span> <span data-ttu-id="10b5a-113">ガベージ コレクションによって、一般的なプログラミング エラーだけでなくメモリ リークもなくなります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-113">Garbage collection eliminates memory leaks as well as some other common programming errors.</span></span> <span data-ttu-id="10b5a-114">コードがマネージ コードの場合、作成する .NET Framework アプリケーションではマネージ データ、アンマネージ データ、またはマネージ データとアンマネージ データの両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-114">If your code is managed, you can use managed data, unmanaged data, or both managed and unmanaged data in your .NET Framework application.</span></span> <span data-ttu-id="10b5a-115">プリミティブ型などのデータ型は言語コンパイラが独自に提供しているため、データがマネージ データかどうかが不明な (または把握する必要がない) 場合もあります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-115">Because language compilers supply their own types, such as primitive types, you might not always know (or need to know) whether your data is being managed.</span></span>  
  
 <span data-ttu-id="10b5a-116">共通言語ランタイムでは、複数の言語間で対話できるオブジェクトを含むコンポーネントやアプリケーションを簡単にデザインできます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-116">The common language runtime makes it easy to design components and applications whose objects interact across languages.</span></span> <span data-ttu-id="10b5a-117">異なる言語で記述されたオブジェクトが相互に対話でき、それらのオブジェクトの動作が緊密に統合されます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-117">Objects written in different languages can communicate with each other, and their behaviors can be tightly integrated.</span></span> <span data-ttu-id="10b5a-118">たとえば、あるクラスを定義してから、そのクラスの派生クラスを別の言語で作成したり、そのクラスに対して別の言語で記述したメソッドを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-118">For example, you can define a class and then use a different language to derive a class from your original class or call a method on the original class.</span></span> <span data-ttu-id="10b5a-119">また、あるクラスのインスタンスを別の言語で記述されたクラスのメソッドに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="10b5a-119">You can also pass an instance of a class to a method of a class written in a different language.</span></span> <span data-ttu-id="10b5a-120">このような言語間の統合を実現できるのは、共通言語ランタイムに対応した言語コンパイラとツールが、共通言語ランタイムによって定義されている共通型システムを採用し、型の作成、使用、永続化、型へのバインディング、および新しい型の定義に関する共通言語ランタイムの規則に従っているためです。</span><span class="sxs-lookup"><span data-stu-id="10b5a-120">This cross-language integration is possible because language compilers and tools that target the runtime use a common type system defined by the runtime, and they follow the runtime's rules for defining new types, as well as for creating, using, persisting, and binding to types.</span></span>  
  
 <span data-ttu-id="10b5a-121">すべてのマネージ コンポーネントは、関連するコンポーネントとリソースについての情報をメタデータの一部として保持しています。</span><span class="sxs-lookup"><span data-stu-id="10b5a-121">As part of their metadata, all managed components carry information about the components and resources they were built against.</span></span> <span data-ttu-id="10b5a-122">共通言語ランタイムはこの情報を使用して、作成したコンポーネントまたはアプリケーションが必要とする特定バージョンのコンポーネントやリソースがあることを確認します。これにより、不明な依存関係によってコードが中断される確率が低くなります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-122">The runtime uses this information to ensure that your component or application has the specified versions of everything it needs, which makes your code less likely to break because of some unmet dependency.</span></span> <span data-ttu-id="10b5a-123">登録情報や状態データはレジストリ内では設定や保守が難しくなるため、レジストリには格納されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="10b5a-123">Registration information and state data are no longer stored in the registry where they can be difficult to establish and maintain.</span></span> <span data-ttu-id="10b5a-124">代わりに、定義した型 (およびその依存関係) に関する情報はコードと共にメタデータとして保存されます。これによって、コンポーネントのレプリケーションと削除がより簡単に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-124">Instead, information about the types you define (and their dependencies) is stored with the code as metadata, making the tasks of component replication and removal much less complicated.</span></span>  
  
 <span data-ttu-id="10b5a-125">言語コンパイラおよびツールは、開発者にとってわかりやすく役に立つ方法で共通言語ランタイムの機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-125">Language compilers and tools expose the runtime's functionality in ways that are intended to be useful and intuitive to developers.</span></span> <span data-ttu-id="10b5a-126">つまり、ある環境では重視されている共通言語ランタイムの機能が、別の環境ではそれほど重視されていないという場合もあります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-126">This means that some features of the runtime might be more noticeable in one environment than in another.</span></span> <span data-ttu-id="10b5a-127">共通言語ランタイムがどのような利点をもたらすかは、使用するコンパイラやツールによって異なります。</span><span class="sxs-lookup"><span data-stu-id="10b5a-127">How you experience the runtime depends on which language compilers or tools you use.</span></span> <span data-ttu-id="10b5a-128">たとえば、Visual Basic の開発者が共通言語ランタイムを使用した場合は、Visual Basic 言語のオブジェクト指向機能が強化されたと感じるでしょう。</span><span class="sxs-lookup"><span data-stu-id="10b5a-128">For example, if you are a Visual Basic developer, you might notice that with the common language runtime, the Visual Basic language has more object-oriented features than before.</span></span> <span data-ttu-id="10b5a-129">ランタイムの利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="10b5a-129">The runtime provides the following benefits:</span></span>  
  
-   <span data-ttu-id="10b5a-130">パフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="10b5a-130">Performance improvements.</span></span>  
  
-   <span data-ttu-id="10b5a-131">異なる言語で開発されたコンポーネントを簡単に利用可能。</span><span class="sxs-lookup"><span data-stu-id="10b5a-131">The ability to easily use components developed in other languages.</span></span>  
  
-   <span data-ttu-id="10b5a-132">クラス ライブラリによって提供される拡張性のある型。</span><span class="sxs-lookup"><span data-stu-id="10b5a-132">Extensible types provided by a class library.</span></span>  
  
-   <span data-ttu-id="10b5a-133">継承、インターフェイス、オーバーロードなどのオブジェクト指向プログラミングの言語機能。</span><span class="sxs-lookup"><span data-stu-id="10b5a-133">Language features such as inheritance, interfaces, and overloading for object-oriented programming.</span></span>  
  
-   <span data-ttu-id="10b5a-134">マルチスレッドでスケーラブルなアプリケーションの作成を可能にする明示的なフリー スレッドのサポート。</span><span class="sxs-lookup"><span data-stu-id="10b5a-134">Support for explicit free threading that allows creation of multithreaded, scalable applications.</span></span>  
  
-   <span data-ttu-id="10b5a-135">構造化例外処理のサポート。</span><span class="sxs-lookup"><span data-stu-id="10b5a-135">Support for structured exception handling.</span></span>  
  
-   <span data-ttu-id="10b5a-136">カスタム属性のサポート。</span><span class="sxs-lookup"><span data-stu-id="10b5a-136">Support for custom attributes.</span></span>  
  
-   <span data-ttu-id="10b5a-137">ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="10b5a-137">Garbage collection.</span></span>  
  
-   <span data-ttu-id="10b5a-138">タイプ セーフとセキュリティを強化するために関数ポインターではなくデリゲートを使用。</span><span class="sxs-lookup"><span data-stu-id="10b5a-138">Use of delegates instead of function pointers for increased type safety and security.</span></span> <span data-ttu-id="10b5a-139">デリゲートの詳細については、「[共通型システム](../../docs/standard/base-types/common-type-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10b5a-139">For more information about delegates, see [Common Type System](../../docs/standard/base-types/common-type-system.md).</span></span>  
  
## <a name="versions-of-the-common-language-runtime"></a><span data-ttu-id="10b5a-140">共通言語ランタイムのバージョン</span><span class="sxs-lookup"><span data-stu-id="10b5a-140">Versions of the Common Language Runtime</span></span>  
 <span data-ttu-id="10b5a-141">.NET Framework のバージョン番号はそれに含まれている CLR のバージョン番号には必ずしも対応しません。</span><span class="sxs-lookup"><span data-stu-id="10b5a-141">The version number of the .NET Framework doesn't necessarily correspond to the version number of the CLR it includes.</span></span> <span data-ttu-id="10b5a-142">2 つのバージョン番号がどのように対応しているかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-142">The following table shows how the two version numbers correlate.</span></span>  
  
|<span data-ttu-id="10b5a-143">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="10b5a-143">.NET Framework version</span></span>|<span data-ttu-id="10b5a-144">含まれている CLR のバージョン</span><span class="sxs-lookup"><span data-stu-id="10b5a-144">Includes CLR version</span></span>|  
|----------------------------|--------------------------|  
|<span data-ttu-id="10b5a-145">1</span><span class="sxs-lookup"><span data-stu-id="10b5a-145">1.0</span></span>|<span data-ttu-id="10b5a-146">1</span><span class="sxs-lookup"><span data-stu-id="10b5a-146">1.0</span></span>|  
|<span data-ttu-id="10b5a-147">1.1</span><span class="sxs-lookup"><span data-stu-id="10b5a-147">1.1</span></span>|<span data-ttu-id="10b5a-148">1.1</span><span class="sxs-lookup"><span data-stu-id="10b5a-148">1.1</span></span>|  
|<span data-ttu-id="10b5a-149">2.0</span><span class="sxs-lookup"><span data-stu-id="10b5a-149">2.0</span></span>|<span data-ttu-id="10b5a-150">2.0</span><span class="sxs-lookup"><span data-stu-id="10b5a-150">2.0</span></span>|  
|<span data-ttu-id="10b5a-151">3.0</span><span class="sxs-lookup"><span data-stu-id="10b5a-151">3.0</span></span>|<span data-ttu-id="10b5a-152">2.0</span><span class="sxs-lookup"><span data-stu-id="10b5a-152">2.0</span></span>|  
|<span data-ttu-id="10b5a-153">3.5</span><span class="sxs-lookup"><span data-stu-id="10b5a-153">3.5</span></span>|<span data-ttu-id="10b5a-154">2.0</span><span class="sxs-lookup"><span data-stu-id="10b5a-154">2.0</span></span>|  
|<span data-ttu-id="10b5a-155">4</span><span class="sxs-lookup"><span data-stu-id="10b5a-155">4</span></span>|<span data-ttu-id="10b5a-156">4</span><span class="sxs-lookup"><span data-stu-id="10b5a-156">4</span></span>|  
|<span data-ttu-id="10b5a-157">4.5 (4.5.1 および 4.5.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="10b5a-157">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="10b5a-158">4</span><span class="sxs-lookup"><span data-stu-id="10b5a-158">4</span></span>|  
|<span data-ttu-id="10b5a-159">4.6 (4.6.1 と 4.6.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="10b5a-159">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="10b5a-160">4</span><span class="sxs-lookup"><span data-stu-id="10b5a-160">4</span></span>|
|<span data-ttu-id="10b5a-161">4.7 (4.7.1 を含む)</span><span class="sxs-lookup"><span data-stu-id="10b5a-161">4.7 (including 4.7.1)</span></span>|<span data-ttu-id="10b5a-162">4</span><span class="sxs-lookup"><span data-stu-id="10b5a-162">4</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="10b5a-163">関連トピック</span><span class="sxs-lookup"><span data-stu-id="10b5a-163">Related Topics</span></span>  
  
|<span data-ttu-id="10b5a-164">Title</span><span class="sxs-lookup"><span data-stu-id="10b5a-164">Title</span></span>|<span data-ttu-id="10b5a-165">説明</span><span class="sxs-lookup"><span data-stu-id="10b5a-165">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="10b5a-166">マネージ実行プロセス</span><span class="sxs-lookup"><span data-stu-id="10b5a-166">Managed Execution Process</span></span>](../../docs/standard/managed-execution-process.md)|<span data-ttu-id="10b5a-167">共通言語ランタイム利用するために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-167">Describes the steps required to take advantage of the common language runtime.</span></span>|  
|[<span data-ttu-id="10b5a-168">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="10b5a-168">Automatic Memory Management</span></span>](../../docs/standard/automatic-memory-management.md)|<span data-ttu-id="10b5a-169">ガベージ コレクターによるメモリの割り当て方法および解放方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-169">Describes how the garbage collector allocates and releases memory.</span></span>|  
|[<span data-ttu-id="10b5a-170">.NET Framework の概要</span><span class="sxs-lookup"><span data-stu-id="10b5a-170">NIB: Overview of the .NET Framework</span></span>](https://msdn.microsoft.com/library/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|<span data-ttu-id="10b5a-171">共通型システム、言語間での相互運用性、マネージ実行、アプリケーション ドメイン、アセンブリなどの .NET Framework の主要な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-171">Describes key .NET Framework concepts such as the common type system, cross-language interoperability, managed execution, application domains, and assemblies.</span></span>|  
|[<span data-ttu-id="10b5a-172">共通型システム</span><span class="sxs-lookup"><span data-stu-id="10b5a-172">Common Type System</span></span>](../../docs/standard/base-types/common-type-system.md)|<span data-ttu-id="10b5a-173">言語間の統合をサポートするために共通言語ランタイムで型を宣言、使用、および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="10b5a-173">Describes how types are declared, used, and managed in the runtime in support of cross-language integration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10b5a-174">参照</span><span class="sxs-lookup"><span data-stu-id="10b5a-174">See Also</span></span>  
 [<span data-ttu-id="10b5a-175">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="10b5a-175">Versions and Dependencies</span></span>](../../docs/framework/migration-guide/versions-and-dependencies.md)
