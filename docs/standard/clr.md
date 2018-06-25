---
title: 共通言語ランタイム (CLR)
ms.custom: updateeachrelease
ms.date: 04/16/2018
ms.technology: dotnet-standard
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
ms.openlocfilehash: 89989b4b7730f4e252dc846377b385cb359dbee1
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315122"
---
# <a name="common-language-runtime-clr-overview"></a><span data-ttu-id="53493-102">共通言語ランタイム (CLR) の概要</span><span class="sxs-lookup"><span data-stu-id="53493-102">Common Language Runtime (CLR) overview</span></span>

<span data-ttu-id="53493-103">.NET Framework には、共通言語ランタイムと呼ばれるランタイム環境が用意されています。共通言語ランタイムは、コードを実行し、開発プロセスを支援するサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="53493-103">The .NET Framework provides a run-time environment called the common language runtime, which runs the code and provides services that make the development process easier.</span></span>

<span data-ttu-id="53493-104">コンパイラとツールにより、共通言語ランタイムの機能が公開されることによって、このマネージ実行環境の利点を活用するコードを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="53493-104">Compilers and tools expose the common language runtime's functionality and enable you to write code that benefits from this managed execution environment.</span></span> <span data-ttu-id="53493-105">このような共通言語ランタイムに対応した言語コンパイラを使用して作成したコードはマネージ コードと呼ばれます。マネージ コードは、言語間の統合、言語間の例外処理、強化されたセキュリティ、バージョン管理と配置のサポート、コンポーネント間の対話の簡易モデル、デバッグ サービスとプロファイル サービスなど、さまざまな機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="53493-105">Code that you develop with a language compiler that targets the runtime is called managed code; it benefits from features such as cross-language integration, cross-language exception handling, enhanced security, versioning and deployment support, a simplified model for component interaction, and debugging and profiling services.</span></span>

> [!NOTE]
> <span data-ttu-id="53493-106">型システム、メタデータの書式、およびランタイム環境 (仮想実行システム) はすべて公的な標準規格の ECMA 共通言語基盤仕様により定義されているため、コンパイラおよびツールは共通言語ランタイムが使用できる出力を生成できます。</span><span class="sxs-lookup"><span data-stu-id="53493-106">Compilers and tools are able to produce output that the common language runtime can consume because the type system, the format of metadata, and the runtime environment (the virtual execution system) are all defined by a public standard, the ECMA Common Language Infrastructure specification.</span></span> <span data-ttu-id="53493-107">詳細については、「[ECMA C# and Common Language Infrastructure Specifications (ECMA C# および共通言語基盤の仕様)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53493-107">For more information, see [ECMA C# and Common Language Infrastructure Specifications](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).</span></span>

<span data-ttu-id="53493-108">マネージ コードが共通言語ランタイムからサービスを受けられるようにするために、言語コンパイラは、そのコード内の型、メンバー、および参照を記述したメタデータを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53493-108">To enable the runtime to provide services to managed code, language compilers must emit metadata that describes the types, members, and references in your code.</span></span> <span data-ttu-id="53493-109">メタデータはコード内に格納されます。つまり、共通言語ランタイムの読み込み可能なすべてのポータブル実行可能 (PE) ファイルには、メタデータが含まれていることになります。</span><span class="sxs-lookup"><span data-stu-id="53493-109">Metadata is stored with the code; every loadable common language runtime portable executable (PE) file contains metadata.</span></span> <span data-ttu-id="53493-110">共通言語ランタイムは、クラスの検索と読み込み、メモリ内でのインスタンスのレイアウト、メソッドの呼び出しの解決、ネイティブ コードの生成、セキュリティの強化、およびランタイムのコンテキスト境界の設定にメタデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="53493-110">The runtime uses metadata to locate and load classes, lay out instances in memory, resolve method invocations, generate native code, enforce security, and set run-time context boundaries.</span></span>

<span data-ttu-id="53493-111">共通言語ランタイムはオブジェクトのレイアウトを自動的に処理し、それらのオブジェクトへの参照を管理し、不要になったオブジェクトを解放します。</span><span class="sxs-lookup"><span data-stu-id="53493-111">The runtime automatically handles object layout and manages references to objects, releasing them when they are no longer being used.</span></span> <span data-ttu-id="53493-112">このような方法で有効期間を管理されるオブジェクトをマネージ データと呼びます。</span><span class="sxs-lookup"><span data-stu-id="53493-112">Objects whose lifetimes are managed in this way are called managed data.</span></span> <span data-ttu-id="53493-113">ガベージ コレクションによって、一般的なプログラミング エラーだけでなくメモリ リークもなくなります。</span><span class="sxs-lookup"><span data-stu-id="53493-113">Garbage collection eliminates memory leaks as well as some other common programming errors.</span></span> <span data-ttu-id="53493-114">コードがマネージ コードの場合、作成する .NET Framework アプリケーションではマネージ データ、アンマネージ データ、またはマネージ データとアンマネージ データの両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="53493-114">If your code is managed, you can use managed data, unmanaged data, or both managed and unmanaged data in your .NET Framework application.</span></span> <span data-ttu-id="53493-115">プリミティブ型などのデータ型は言語コンパイラが独自に提供しているため、データがマネージ データかどうかが不明な (または把握する必要がない) 場合もあります。</span><span class="sxs-lookup"><span data-stu-id="53493-115">Because language compilers supply their own types, such as primitive types, you might not always know (or need to know) whether your data is being managed.</span></span>

<span data-ttu-id="53493-116">共通言語ランタイムでは、複数の言語間で対話できるオブジェクトを含むコンポーネントやアプリケーションを簡単にデザインできます。</span><span class="sxs-lookup"><span data-stu-id="53493-116">The common language runtime makes it easy to design components and applications whose objects interact across languages.</span></span> <span data-ttu-id="53493-117">異なる言語で記述されたオブジェクトが相互に対話でき、それらのオブジェクトの動作が緊密に統合されます。</span><span class="sxs-lookup"><span data-stu-id="53493-117">Objects written in different languages can communicate with each other, and their behaviors can be tightly integrated.</span></span> <span data-ttu-id="53493-118">たとえば、あるクラスを定義してから、そのクラスの派生クラスを別の言語で作成したり、そのクラスに対して別の言語で記述したメソッドを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="53493-118">For example, you can define a class and then use a different language to derive a class from your original class or call a method on the original class.</span></span> <span data-ttu-id="53493-119">また、あるクラスのインスタンスを別の言語で記述されたクラスのメソッドに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="53493-119">You can also pass an instance of a class to a method of a class written in a different language.</span></span> <span data-ttu-id="53493-120">このような言語間の統合を実現できるのは、共通言語ランタイムに対応した言語コンパイラとツールが、共通言語ランタイムによって定義されている共通型システムを採用し、型の作成、使用、永続化、型へのバインディング、および新しい型の定義に関する共通言語ランタイムの規則に従っているためです。</span><span class="sxs-lookup"><span data-stu-id="53493-120">This cross-language integration is possible because language compilers and tools that target the runtime use a common type system defined by the runtime, and they follow the runtime's rules for defining new types, as well as for creating, using, persisting, and binding to types.</span></span>

<span data-ttu-id="53493-121">すべてのマネージ コンポーネントは、関連するコンポーネントとリソースについての情報をメタデータの一部として保持しています。</span><span class="sxs-lookup"><span data-stu-id="53493-121">As part of their metadata, all managed components carry information about the components and resources they were built against.</span></span> <span data-ttu-id="53493-122">共通言語ランタイムはこの情報を使用して、作成したコンポーネントまたはアプリケーションが必要とする特定バージョンのコンポーネントやリソースがあることを確認します。これにより、不明な依存関係によってコードが中断される確率が低くなります。</span><span class="sxs-lookup"><span data-stu-id="53493-122">The runtime uses this information to ensure that your component or application has the specified versions of everything it needs, which makes your code less likely to break because of some unmet dependency.</span></span> <span data-ttu-id="53493-123">登録情報や状態データはレジストリ内では設定や保守が難しくなるため、レジストリには格納されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="53493-123">Registration information and state data are no longer stored in the registry where they can be difficult to establish and maintain.</span></span> <span data-ttu-id="53493-124">代わりに、定義した型 (およびその依存関係) に関する情報はコードと共にメタデータとして保存されます。これによって、コンポーネントのレプリケーションと削除がより簡単に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="53493-124">Instead, information about the types you define (and their dependencies) is stored with the code as metadata, making the tasks of component replication and removal much less complicated.</span></span>

<span data-ttu-id="53493-125">言語コンパイラおよびツールは、開発者にとってわかりやすく役に立つ方法で共通言語ランタイムの機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="53493-125">Language compilers and tools expose the runtime's functionality in ways that are intended to be useful and intuitive to developers.</span></span> <span data-ttu-id="53493-126">つまり、ある環境では重視されている共通言語ランタイムの機能が、別の環境ではそれほど重視されていないという場合もあります。</span><span class="sxs-lookup"><span data-stu-id="53493-126">This means that some features of the runtime might be more noticeable in one environment than in another.</span></span> <span data-ttu-id="53493-127">共通言語ランタイムがどのような利点をもたらすかは、使用するコンパイラやツールによって異なります。</span><span class="sxs-lookup"><span data-stu-id="53493-127">How you experience the runtime depends on which language compilers or tools you use.</span></span> <span data-ttu-id="53493-128">たとえば、Visual Basic の開発者が共通言語ランタイムを使用した場合は、Visual Basic 言語のオブジェクト指向機能が強化されたと感じるでしょう。</span><span class="sxs-lookup"><span data-stu-id="53493-128">For example, if you are a Visual Basic developer, you might notice that with the common language runtime, the Visual Basic language has more object-oriented features than before.</span></span> <span data-ttu-id="53493-129">ランタイムの利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="53493-129">The runtime provides the following benefits:</span></span>

- <span data-ttu-id="53493-130">パフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="53493-130">Performance improvements.</span></span>

- <span data-ttu-id="53493-131">異なる言語で開発されたコンポーネントを簡単に利用可能。</span><span class="sxs-lookup"><span data-stu-id="53493-131">The ability to easily use components developed in other languages.</span></span>

- <span data-ttu-id="53493-132">クラス ライブラリによって提供される拡張性のある型。</span><span class="sxs-lookup"><span data-stu-id="53493-132">Extensible types provided by a class library.</span></span>

- <span data-ttu-id="53493-133">継承、インターフェイス、オーバーロードなどのオブジェクト指向プログラミングの言語機能。</span><span class="sxs-lookup"><span data-stu-id="53493-133">Language features such as inheritance, interfaces, and overloading for object-oriented programming.</span></span>

- <span data-ttu-id="53493-134">マルチスレッドでスケーラブルなアプリケーションの作成を可能にする明示的なフリー スレッドのサポート。</span><span class="sxs-lookup"><span data-stu-id="53493-134">Support for explicit free threading that allows creation of multithreaded, scalable applications.</span></span>

- <span data-ttu-id="53493-135">構造化例外処理のサポート。</span><span class="sxs-lookup"><span data-stu-id="53493-135">Support for structured exception handling.</span></span>

- <span data-ttu-id="53493-136">カスタム属性のサポート。</span><span class="sxs-lookup"><span data-stu-id="53493-136">Support for custom attributes.</span></span>

- <span data-ttu-id="53493-137">ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="53493-137">Garbage collection.</span></span>

- <span data-ttu-id="53493-138">タイプ セーフとセキュリティを強化するために関数ポインターではなくデリゲートを使用。</span><span class="sxs-lookup"><span data-stu-id="53493-138">Use of delegates instead of function pointers for increased type safety and security.</span></span> <span data-ttu-id="53493-139">デリゲートの詳細については、「[共通型システム](../../docs/standard/base-types/common-type-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53493-139">For more information about delegates, see [Common Type System](../../docs/standard/base-types/common-type-system.md).</span></span>

## <a name="clr-versions"></a><span data-ttu-id="53493-140">CLR のバージョン</span><span class="sxs-lookup"><span data-stu-id="53493-140">CLR versions</span></span>

<span data-ttu-id="53493-141">.NET Framework のバージョン番号はそれに含まれている CLR のバージョン番号には必ずしも対応しません。</span><span class="sxs-lookup"><span data-stu-id="53493-141">The version number of the .NET Framework doesn't necessarily correspond to the version number of the CLR it includes.</span></span> <span data-ttu-id="53493-142">2 つのバージョン番号がどのように対応しているかを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="53493-142">The following table shows how the two version numbers correlate.</span></span>

|<span data-ttu-id="53493-143">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="53493-143">.NET Framework version</span></span>|<span data-ttu-id="53493-144">含まれている CLR のバージョン</span><span class="sxs-lookup"><span data-stu-id="53493-144">Includes CLR version</span></span>|
|----------------------------|--------------------------|
|<span data-ttu-id="53493-145">1</span><span class="sxs-lookup"><span data-stu-id="53493-145">1.0</span></span>|<span data-ttu-id="53493-146">1</span><span class="sxs-lookup"><span data-stu-id="53493-146">1.0</span></span>|
|<span data-ttu-id="53493-147">1.1</span><span class="sxs-lookup"><span data-stu-id="53493-147">1.1</span></span>|<span data-ttu-id="53493-148">1.1</span><span class="sxs-lookup"><span data-stu-id="53493-148">1.1</span></span>|
|<span data-ttu-id="53493-149">2.0</span><span class="sxs-lookup"><span data-stu-id="53493-149">2.0</span></span>|<span data-ttu-id="53493-150">2.0</span><span class="sxs-lookup"><span data-stu-id="53493-150">2.0</span></span>|
|<span data-ttu-id="53493-151">3.0</span><span class="sxs-lookup"><span data-stu-id="53493-151">3.0</span></span>|<span data-ttu-id="53493-152">2.0</span><span class="sxs-lookup"><span data-stu-id="53493-152">2.0</span></span>|
|<span data-ttu-id="53493-153">3.5</span><span class="sxs-lookup"><span data-stu-id="53493-153">3.5</span></span>|<span data-ttu-id="53493-154">2.0</span><span class="sxs-lookup"><span data-stu-id="53493-154">2.0</span></span>|
|<span data-ttu-id="53493-155">4</span><span class="sxs-lookup"><span data-stu-id="53493-155">4</span></span>|<span data-ttu-id="53493-156">4</span><span class="sxs-lookup"><span data-stu-id="53493-156">4</span></span>|
|<span data-ttu-id="53493-157">4.5 (4.5.1 および 4.5.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="53493-157">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="53493-158">4</span><span class="sxs-lookup"><span data-stu-id="53493-158">4</span></span>|
|<span data-ttu-id="53493-159">4.6 (4.6.1 と 4.6.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="53493-159">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="53493-160">4</span><span class="sxs-lookup"><span data-stu-id="53493-160">4</span></span>|
|<span data-ttu-id="53493-161">4.7 (4.7.1 と 4.7.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="53493-161">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="53493-162">4</span><span class="sxs-lookup"><span data-stu-id="53493-162">4</span></span>|

## <a name="related-topics"></a><span data-ttu-id="53493-163">関連トピック</span><span class="sxs-lookup"><span data-stu-id="53493-163">Related topics</span></span>

|<span data-ttu-id="53493-164">Title</span><span class="sxs-lookup"><span data-stu-id="53493-164">Title</span></span>|<span data-ttu-id="53493-165">説明</span><span class="sxs-lookup"><span data-stu-id="53493-165">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="53493-166">マネージ実行プロセス</span><span class="sxs-lookup"><span data-stu-id="53493-166">Managed Execution Process</span></span>](managed-execution-process.md)|<span data-ttu-id="53493-167">共通言語ランタイム利用するために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="53493-167">Describes the steps required to take advantage of the common language runtime.</span></span>|
|[<span data-ttu-id="53493-168">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="53493-168">Automatic Memory Management</span></span>](automatic-memory-management.md)|<span data-ttu-id="53493-169">ガベージ コレクターによるメモリの割り当て方法および解放方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="53493-169">Describes how the garbage collector allocates and releases memory.</span></span>|
|[<span data-ttu-id="53493-170">.NET Framework の概要</span><span class="sxs-lookup"><span data-stu-id="53493-170">Overview of the .NET Framework</span></span>](../framework/get-started/overview.md)|<span data-ttu-id="53493-171">共通型システム、言語間での相互運用性、マネージ実行、アプリケーション ドメイン、アセンブリなどの .NET Framework の主要な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="53493-171">Describes key .NET Framework concepts such as the common type system, cross-language interoperability, managed execution, application domains, and assemblies.</span></span>|
|[<span data-ttu-id="53493-172">共通型システム</span><span class="sxs-lookup"><span data-stu-id="53493-172">Common Type System</span></span>](./base-types/common-type-system.md)|<span data-ttu-id="53493-173">言語間の統合をサポートするために共通言語ランタイムで型を宣言、使用、および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="53493-173">Describes how types are declared, used, and managed in the runtime in support of cross-language integration.</span></span>|

## <a name="see-also"></a><span data-ttu-id="53493-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="53493-174">See also</span></span>

[<span data-ttu-id="53493-175">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="53493-175">Versions and Dependencies</span></span>](../framework/migration-guide/versions-and-dependencies.md)
