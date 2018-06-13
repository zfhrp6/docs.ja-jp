---
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e4db5f3c7deb300a9666182cb6b712eacf42cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436229"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="ed977-102">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed977-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="ed977-103">そのバージョン番号に基づいた、共通言語ランタイム (CLR) の特定のバージョンを返す、インストールされている Clr のすべてを一覧表示、指定されたプロセスに読み込まれるすべてのランタイムの一覧で、アセンブリをコンパイル、プロセスを終了するために使用する CLR バージョンを検出するメソッドを提供します。クリーン ランタイムがシャット ダウン、および従来の API バインドをクエリします。</span><span class="sxs-lookup"><span data-stu-id="ed977-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed977-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-104">Methods</span></span>  
  
|<span data-ttu-id="ed977-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-105">Method</span></span>|<span data-ttu-id="ed977-106">説明</span><span class="sxs-lookup"><span data-stu-id="ed977-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed977-107">EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="ed977-108">含む有効な列挙体を返します[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)コンピューターにインストールされている CLR バージョンごとにインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="ed977-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="ed977-109">EnumerateLoadedRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="ed977-110">含む有効な列挙体を返します[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)特定のプロセスに読み込まれている各 CLR へのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="ed977-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="ed977-111">このメソッドに置き換えられる[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed977-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="ed977-112">ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="ed977-113">正常に読み込まれているすべてのランタイムをシャット ダウンしようとして、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="ed977-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="ed977-114">置き換えるソフトウェア更新プログラム、 [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="ed977-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="ed977-115">GetRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="ed977-116">取得、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)特定の CLR バージョンに対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ed977-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="ed977-117">このメソッドは、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)で使用される関数、 [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)フラグ。</span><span class="sxs-lookup"><span data-stu-id="ed977-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="ed977-118">GetVersionFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="ed977-119">指定されたファイル パスから、アセンブリの元の .NET Framework コンパイル バージョン (メタデータに格納されている) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ed977-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="ed977-120">このメソッドに置き換えられる[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed977-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="ed977-121">QueryLegacyV2RuntimeBinding メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="ed977-122">レガシ アクティブ化ポリシーが関連付けられて、例を使用してランタイムを表すインターフェイスを返します、`useLegacyV2RuntimeActivationPolicy`属性を[\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)ダイレクトを使用して、構成ファイルのエントリApi のレガシ アクティブ化のまたは呼び出すことによって、 [iclrruntimeinfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ed977-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="ed977-123">RequestRuntimeLoadedNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="ed977-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="ed977-124">CLR バージョンは、最初に読み込まれたが、開始していない場合に、指定した関数ポインターへのコールバックが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ed977-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="ed977-125">このメソッドに置き換えられる[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="ed977-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed977-126">コメント</span><span class="sxs-lookup"><span data-stu-id="ed977-126">Remarks</span></span>  
 <span data-ttu-id="ed977-127">このインターフェイスのインスタンスを取得する唯一の方法は、呼び出すことによって、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数の次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ed977-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ed977-128">要件</span><span class="sxs-lookup"><span data-stu-id="ed977-128">Requirements</span></span>  
 <span data-ttu-id="ed977-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ed977-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed977-130">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ed977-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ed977-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ed977-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed977-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed977-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed977-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed977-133">See Also</span></span>  
 [<span data-ttu-id="ed977-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed977-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ed977-135">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ed977-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
