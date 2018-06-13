---
title: STARTUP_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc1d3ffc34cd74d68bf10cb677b68f0a75bb7c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444231"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="7956c-102">STARTUP_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="7956c-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="7956c-103">共通言語ランタイム (CLR: Common Language Runtime) の起動動作を示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="7956c-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="7956c-104">既定では、ガベージ コレクションは非同時実行で、基底クラス ライブラリだけがドメイン中立領域に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7956c-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7956c-105">構文</span><span class="sxs-lookup"><span data-stu-id="7956c-105">Syntax</span></span>  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7956c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7956c-106">Members</span></span>  
  
|<span data-ttu-id="7956c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="7956c-107">Member</span></span>|<span data-ttu-id="7956c-108">説明</span><span class="sxs-lookup"><span data-stu-id="7956c-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="7956c-109">同時実行ガベージ コレクションを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="7956c-110">呼び出し元がサーバー ビルドと同時実行ガベージ コレクションをシングル プロセッサ コンピューター上で要求した場合は、代わりにワークステーション ビルドと非同時実行ガベージ コレクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7956c-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="7956c-111">**注:** WOW64 で実行されているアプリケーションでは、同時実行ガベージ コレクションはサポートされていない x86、Intel Itanium アーキテクチャ (以前の ia-64) を実装する 64 ビット システム上のエミュレーターです。</span><span class="sxs-lookup"><span data-stu-id="7956c-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="7956c-112">64 ビットの Windows システムで WOW64 の使用に関する詳細については、次を参照してください。[を実行している 32 ビット アプリケーション](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="7956c-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="7956c-113">ローダーの最適化を行う必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="7956c-114">どのアセンブリもドメイン中立として読み込まないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="7956c-115">すべてのアセンブリをドメイン中立として読み込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="7956c-116">厳密な名前を付けられたすべてのアセンブリをドメイン中立として読み込むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="7956c-117">CLR バージョン ポリシーが、渡されたバージョンに適用されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="7956c-118">指定された CLR のバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="7956c-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="7956c-119">シムは、互換性のある最新バージョンを決めるためのポリシーの評価を実行しません。</span><span class="sxs-lookup"><span data-stu-id="7956c-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="7956c-120">推奨ランタイムを設定するように指定しますが、実際には起動されません。</span><span class="sxs-lookup"><span data-stu-id="7956c-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="7956c-121">サーバー ガベージ コレクションを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="7956c-122">ガベージ コレクションで、使用された仮想アドレスを保持することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="7956c-123">ホスト インターフェイスの混合を許可しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="7956c-124">既定として偽装が非同期ポイント間をフローしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="7956c-125">スレッドが実行を開始するときにスレッド スタック全体をコミットしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="7956c-126">マネージ偽装およびプラットフォーム呼び出しによって実行された偽装が非同期ポイント間をフローするように指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="7956c-127">既定では、マネージ偽装だけが非同期ポイント間をフローします。</span><span class="sxs-lookup"><span data-stu-id="7956c-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="7956c-128">システム メモリが少ないときに、ガベージ コレクションによるコミットされた領域の使用量を抑えることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="7956c-129">参照してください`gcTrimCommitOnLowMemory`で[共有 Web ホストの最適化](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)です。</span><span class="sxs-lookup"><span data-stu-id="7956c-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="7956c-130">共通言語ランタイム イベントで Windows イベント トレーシング (ETW) が有効になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="7956c-131">Windows Vista 以降では、イベントのトレースは常に有効、ため、このフラグが影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="7956c-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="7956c-132">参照してください[.NET Framework のログ記録を制御する](../../../../docs/framework/performance/controlling-logging.md)です。</span><span class="sxs-lookup"><span data-stu-id="7956c-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="7956c-133">アプリケーション ドメインのリソース監視が有効になっていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7956c-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="7956c-134">参照してください、<xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>プロパティおよび[ \<appDomainResourceMonitoring > 要素](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="7956c-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7956c-135">要件</span><span class="sxs-lookup"><span data-stu-id="7956c-135">Requirements</span></span>  
 <span data-ttu-id="7956c-136">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7956c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7956c-137">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7956c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7956c-138">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7956c-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7956c-139">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7956c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7956c-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="7956c-140">See Also</span></span>  
 [<span data-ttu-id="7956c-141">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="7956c-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
