---
title: "アンマネージ API リファレンス"
ms.custom: 
ms.date: 11/06/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7069762dd95636399c53c98e8bdef6f00be62c1
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="23895-102">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="23895-102">Unmanaged API Reference</span></span>
<span data-ttu-id="23895-103">このセクションには、ランタイム ホスト、コンパイラ、逆アセンブラー、難読化ツール、デバッガー、プロファイラーなど、マネージ コード関連のアプリケーションが使用できるアンマネージ API に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="23895-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23895-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="23895-104">In This Section</span></span>  
 [<span data-ttu-id="23895-105">一般的なデータ型</span><span class="sxs-lookup"><span data-stu-id="23895-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="23895-106">特にアンマネージ プロファイリング API とデバッギング API で使用される一般的なデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="23895-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="23895-107">ALink</span><span class="sxs-lookup"><span data-stu-id="23895-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="23895-108">ALink API について説明します。この API は .NET Framework アセンブリおよび非バインド モジュールの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="23895-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="23895-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="23895-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="23895-110">Authenticode XrML ライセンスの作成および検証モジュールをサポートします。</span><span class="sxs-lookup"><span data-stu-id="23895-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="23895-111">定数</span><span class="sxs-lookup"><span data-stu-id="23895-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="23895-112">CorSym.idl で定義される定数について説明します。</span><span class="sxs-lookup"><span data-stu-id="23895-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="23895-113">カスタム インターフェイス属性</span><span class="sxs-lookup"><span data-stu-id="23895-113">Custom Interface Attributes</span></span>](http://msdn.microsoft.com/en-us/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="23895-114">コンポーネント オブジェクト モデル (COM) のカスタム インターフェイス属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="23895-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="23895-115">デバッグ</span><span class="sxs-lookup"><span data-stu-id="23895-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="23895-116">デバッグ API について説明します。これによりデバッガーは、共通言語ランタイム (CLR) 環境で実行するコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="23895-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="23895-117">シンボル ストア診断</span><span class="sxs-lookup"><span data-stu-id="23895-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="23895-118">シンボル ストア診断 API について説明します。これによりコンパイラは、デバッガーが使用するためのシンボル情報を生成できます。</span><span class="sxs-lookup"><span data-stu-id="23895-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="23895-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="23895-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="23895-120">Fusion API について説明します。これによりランタイム ホストは、アプリケーションに対するリソースの正しいバージョンを見つけるために、アプリケーションのリソースのプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="23895-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="23895-121">ホスティング</span><span class="sxs-lookup"><span data-stu-id="23895-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="23895-122">ホスト API について説明します。これにより、アンマネージ ホストが CLR をホストのアプリケーションに統合できます。</span><span class="sxs-lookup"><span data-stu-id="23895-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="23895-123">メタデータ</span><span class="sxs-lookup"><span data-stu-id="23895-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="23895-124">メタデータ API について説明します。これによりコンパイラなどのクライアントは、CLR によって読み込まれる型を使用せずに、コンポーネントのメタデータを生成したり、メタデータにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="23895-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="23895-125">プロファイル</span><span class="sxs-lookup"><span data-stu-id="23895-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="23895-126">プロファイル API について説明します。これによりプロファイラーは CLR によるプログラムの実行を監視できます。</span><span class="sxs-lookup"><span data-stu-id="23895-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="23895-127">厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="23895-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="23895-128">厳密な名前付け API について説明します。これによりクライアントは、アセンブリに対する厳密な名前の署名を管理できます。</span><span class="sxs-lookup"><span data-stu-id="23895-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="23895-129">WMI およびパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="23895-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="23895-130">Windows Management Instrumentation (WMI) のライブラリへの呼び出しをラップする Api について説明します。</span><span class="sxs-lookup"><span data-stu-id="23895-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="23895-131">Tlbexp ヘルパー関数します。</span><span class="sxs-lookup"><span data-stu-id="23895-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="23895-132">タイプ ライブラリ エクスポーター (Tlbexp.exe) がアセンブリからタイプ ライブラリへの変換プロセス中に使用する、2 つのヘルパー関数とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="23895-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="23895-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="23895-133">Related Sections</span></span>  
 [<span data-ttu-id="23895-134">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="23895-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="23895-135">.NET Framework の高度な読み取り</span><span class="sxs-lookup"><span data-stu-id="23895-135">Advanced Reading for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)
