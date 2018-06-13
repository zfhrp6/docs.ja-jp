---
title: ICorDebugProcess6::EnableVirtualModuleSplitting メソッド
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4565deddee2e7714d937bf61574243cc07a4602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423476"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="74f22-102">ICorDebugProcess6::EnableVirtualModuleSplitting メソッド</span><span class="sxs-lookup"><span data-stu-id="74f22-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>
<span data-ttu-id="74f22-103">仮想モジュール分割を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="74f22-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f22-104">構文</span><span class="sxs-lookup"><span data-stu-id="74f22-104">Syntax</span></span>  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74f22-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74f22-105">Parameters</span></span>  
 `enableSplitting`  
 <span data-ttu-id="74f22-106">仮想モジュール分割を有効にするには、`true`。無効にするには、`false`。</span><span class="sxs-lookup"><span data-stu-id="74f22-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f22-107">コメント</span><span class="sxs-lookup"><span data-stu-id="74f22-107">Remarks</span></span>  
 <span data-ttu-id="74f22-108">仮想モジュール分割原因[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)をビルド中にマージされたモジュールが処理され、1 つの大規模なモジュールではなく、個別のモジュールのグループとして表さを認識します。</span><span class="sxs-lookup"><span data-stu-id="74f22-108">Virtual module splitting causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="74f22-109">これにさまざまな動作を変更[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)メソッドを次に説明します。</span><span class="sxs-lookup"><span data-stu-id="74f22-109">Doing this changes the behavior of various [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74f22-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="74f22-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="74f22-111">このメソッドを呼び出し、`enableSplitting` の値をいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="74f22-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="74f22-112">ステートフル関数変更は行われません、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)で示されているメソッドの動作を変更する以外のオブジェクト、[仮想モジュール分割とアンマネージ デバッグ Api](#APIs)呼び出された時点で参照してください。</span><span class="sxs-lookup"><span data-stu-id="74f22-112">It does not cause any stateful functional changes in an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="74f22-113">仮想モジュールを使用しても、これらのメソッドの呼び出し時にパフォーマンスの低下は発生しません。</span><span class="sxs-lookup"><span data-stu-id="74f22-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="74f22-114">さらに、仮想化されたメタデータの重大なメモリ内キャッシュ必要がありますを正しく実装する、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)仮想モジュール分割がオフになった後も、Api、およびこれらのキャッシュを保持可能性があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="74f22-115">用語</span><span class="sxs-lookup"><span data-stu-id="74f22-115">Terminology</span></span>  
 <span data-ttu-id="74f22-116">仮想モジュール分割について説明する場合には、次の用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="74f22-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="74f22-117">コンテナー モジュールまたはコンテナー</span><span class="sxs-lookup"><span data-stu-id="74f22-117">container modules, or containers</span></span>  
 <span data-ttu-id="74f22-118">集計モジュール。</span><span class="sxs-lookup"><span data-stu-id="74f22-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="74f22-119">サブモジュール、または仮想モジュール</span><span class="sxs-lookup"><span data-stu-id="74f22-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="74f22-120">コンテナー内にあるモジュール。</span><span class="sxs-lookup"><span data-stu-id="74f22-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="74f22-121">標準モジュール</span><span class="sxs-lookup"><span data-stu-id="74f22-121">regular modules</span></span>  
 <span data-ttu-id="74f22-122">ビルド時にマージされなかったモジュール。</span><span class="sxs-lookup"><span data-stu-id="74f22-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="74f22-123">コンテナー モジュールでもサブモジュールでもありません。</span><span class="sxs-lookup"><span data-stu-id="74f22-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="74f22-124">ICorDebugModule インターフェイス オブジェクトでは、コンテナー モジュールとサブモジュールの両方が表されます。</span><span class="sxs-lookup"><span data-stu-id="74f22-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="74f22-125">ただし、インターフェイスの動作は、各ケースで若干異なるとして、\<セクションに x-ref > セクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="74f22-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="74f22-126">モジュールとアセンブリ</span><span class="sxs-lookup"><span data-stu-id="74f22-126">Modules and assemblies</span></span>  
 <span data-ttu-id="74f22-127">アセンブリ マージ シナリオではマルチモジュール アセンブリはサポートされないため、モジュールとアセンブリの間には一対一リレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="74f22-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="74f22-128">コンテナー モジュールまたはサブモジュールを表すかどうかに関係なく、各 ICorDebugModule オブジェクトには、対応する ICorDebugAssembly オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="74f22-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="74f22-129">[Icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドは、モジュールからアセンブリに変換します。</span><span class="sxs-lookup"><span data-stu-id="74f22-129">The [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="74f22-130">その他の方向にマップするため、 [icordebugassembly::enumeratemodules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)メソッドを 1 つだけのモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="74f22-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="74f22-131">この場合、アセンブリとモジュールは緊密に結合されたペアとなるため、アセンブリとモジュールはほぼ同義の用語となります。</span><span class="sxs-lookup"><span data-stu-id="74f22-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="74f22-132">動作の違い</span><span class="sxs-lookup"><span data-stu-id="74f22-132">Behavioral differences</span></span>  
 <span data-ttu-id="74f22-133">コンテナー モジュールには、次の動作と特性があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-133">Container modules have the following behaviors and characteristics:</span></span>  
  
-   <span data-ttu-id="74f22-134">構成要素であるすべてのサブモジュールのメタデータはマージされます。</span><span class="sxs-lookup"><span data-stu-id="74f22-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
-   <span data-ttu-id="74f22-135">型名は変形する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-135">Their type names may be mangled.</span></span>  
  
-   <span data-ttu-id="74f22-136">[Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッドは、ディスク上のモジュールへのパスを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-136">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
-   <span data-ttu-id="74f22-137">[Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、そのイメージのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-137">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
-   <span data-ttu-id="74f22-138">ICorDebugAssembly3.EnumerateContainedAssemblies メソッドは、サブモジュールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="74f22-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
-   <span data-ttu-id="74f22-139">ICorDebugAssembly3.GetContainerAssembly メソッドは、`S_FALSE` を返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="74f22-140">サブモジュールには、次の動作と特性があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
-   <span data-ttu-id="74f22-141">マージされた元のアセンブリのみに対応する削減されたメタデータのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="74f22-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
-   <span data-ttu-id="74f22-142">メタデータ名は、変形しません。</span><span class="sxs-lookup"><span data-stu-id="74f22-142">The metadata names are not mangled.</span></span>  
  
-   <span data-ttu-id="74f22-143">メタデータ トークンは、ビルド プロセスでマージされる前の元のアセンブリ内のトークンと一致することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="74f22-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
-   <span data-ttu-id="74f22-144">[Icordebugmodule::getname](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)メソッド アセンブリ名、ファイル パスではなくを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-144">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
-   <span data-ttu-id="74f22-145">[Icordebugmodule::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)メソッドは、元のマージされていないイメージのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-145">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
-   <span data-ttu-id="74f22-146">ICorDebugModule3.EnumerateContainedAssemblies メソッドは、`S_FALSE` を返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
-   <span data-ttu-id="74f22-147">ICorDebugAssembly3.GetContainerAssembly メソッドは、格納しているモジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="74f22-148">モジュールから取得されるインターフェイス</span><span class="sxs-lookup"><span data-stu-id="74f22-148">Interfaces retrieved from modules</span></span>  
 <span data-ttu-id="74f22-149">さまざまなインターフェイスをモジュールから作成または取得できます。</span><span class="sxs-lookup"><span data-stu-id="74f22-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="74f22-150">その例には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="74f22-150">Some of these include:</span></span>  
  
-   <span data-ttu-id="74f22-151">ICorDebugClass オブジェクトによって返される、 [icordebugmodule::getclassfromtoken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="74f22-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
-   <span data-ttu-id="74f22-152">ICorDebugAssembly オブジェクトによって返される、 [icordebugmodule::getassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="74f22-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="74f22-153">これらのオブジェクトは常にキャッシュ[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)が作成またはコンテナー モジュールまたはサブモジュールから照会されたのかどうかに関係なく、同じポインター id が必要であるとします。</span><span class="sxs-lookup"><span data-stu-id="74f22-153">These objects are always cached by [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="74f22-154">サブモジュールは、独自のコピーを持つ個別のキャッシュではなく、これらのキャッシュされたオブジェクトのフィルター処理されたビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="74f22-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="74f22-155">仮想モジュール分割とアンマネージ デバッグ API</span><span class="sxs-lookup"><span data-stu-id="74f22-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  
 <span data-ttu-id="74f22-156">次の表に、仮想モジュール分割がアンマネージ デバッグ API の他のメソッドの動作に影響する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="74f22-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="74f22-157">メソッド</span><span class="sxs-lookup"><span data-stu-id="74f22-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="74f22-158">Icordebugfunction::getmodule</span><span class="sxs-lookup"><span data-stu-id="74f22-158">ICorDebugFunction::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="74f22-159">この関数が最初に定義されたサブモジュールを返します</span><span class="sxs-lookup"><span data-stu-id="74f22-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="74f22-160">この関数がマージされたコンテナー モジュールを返します</span><span class="sxs-lookup"><span data-stu-id="74f22-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="74f22-161">Icordebugclass::getmodule</span><span class="sxs-lookup"><span data-stu-id="74f22-161">ICorDebugClass::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="74f22-162">このクラスが最初に定義されたサブモジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="74f22-163">このクラスがマージされたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="74f22-164">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="74f22-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="74f22-165">読み込まれたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="74f22-166">サブモジュールは、この設定に関係なく、読み込みイベントを提供されません。</span><span class="sxs-lookup"><span data-stu-id="74f22-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="74f22-167">読み込まれたコンテナー モジュールを返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="74f22-168">Icordebugappdomain::enumerateassemblies</span><span class="sxs-lookup"><span data-stu-id="74f22-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="74f22-169">サブアセンブリと標準アセンブリのリストを返します。コンテナー アセンブリは含まれません。</span><span class="sxs-lookup"><span data-stu-id="74f22-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="74f22-170">**注:** 任意のコンテナー アセンブリのシンボルがない場合そのサブアセンブリのいずれも列挙されます。</span><span class="sxs-lookup"><span data-stu-id="74f22-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="74f22-171">いずれかの標準アセンブリにシンボルがない場合、列挙される場合と列挙されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="74f22-172">コンテナー アセンブリと標準アセンブリのリストを返します。サブアセンブリは含まれません。</span><span class="sxs-lookup"><span data-stu-id="74f22-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="74f22-173">**注:** 可能性がありますが、標準のアセンブリのシンボルがない場合、または列挙されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="74f22-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="74f22-174">[Icordebugcode::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (を参照する際の IL コードのみ)</span><span class="sxs-lookup"><span data-stu-id="74f22-174">[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="74f22-175">マージ前のアセンブリ イメージ内で有効な IL を返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="74f22-176">具体的には、参照先の型が IL を含む仮想モジュールで定義されていない場合、インライン メタデータ トークンは正確に TypeRef または MemberRef トークンになります。</span><span class="sxs-lookup"><span data-stu-id="74f22-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="74f22-177">これらの TypeRef または MemberRef トークン検索できます、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)の対応する仮想 ICorDebugModule オブジェクトのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="74f22-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="74f22-178">マージ後のアセンブリ イメージ内の IL を返します。</span><span class="sxs-lookup"><span data-stu-id="74f22-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74f22-179">要件</span><span class="sxs-lookup"><span data-stu-id="74f22-179">Requirements</span></span>  
 <span data-ttu-id="74f22-180">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74f22-180">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f22-181">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74f22-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74f22-182">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74f22-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f22-183">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f22-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f22-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="74f22-184">See Also</span></span>  
 [<span data-ttu-id="74f22-185">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74f22-185">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="74f22-186">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74f22-186">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
