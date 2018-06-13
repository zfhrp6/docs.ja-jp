---
title: ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ac041db64a874cc143657c601f30e4482dd2462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434436"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="b154f-102">ICLRMetaHost::RequestRuntimeLoadedNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="b154f-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="b154f-103">共通言語ランタイム (CLR) のバージョンが最初に読み込まれましたが、開始していないときに呼び出される保証されているコールバック関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="b154f-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="b154f-104">このメソッドは、 [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="b154f-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b154f-105">構文</span><span class="sxs-lookup"><span data-stu-id="b154f-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b154f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b154f-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="b154f-107">[in]新しいランタイムが読み込まれたときに呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="b154f-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b154f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b154f-108">Return Value</span></span>  
 <span data-ttu-id="b154f-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="b154f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b154f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b154f-110">HRESULT</span></span>|<span data-ttu-id="b154f-111">説明</span><span class="sxs-lookup"><span data-stu-id="b154f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b154f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b154f-112">S_OK</span></span>|<span data-ttu-id="b154f-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="b154f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b154f-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b154f-114">E_POINTER</span></span>|<span data-ttu-id="b154f-115">`pCallbackFunction` が null です。</span><span class="sxs-lookup"><span data-stu-id="b154f-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b154f-116">コメント</span><span class="sxs-lookup"><span data-stu-id="b154f-116">Remarks</span></span>  
 <span data-ttu-id="b154f-117">コールバックは、次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="b154f-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="b154f-118">最初に、ランタイムが読み込まれるときにのみ、コールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b154f-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="b154f-119">コールバックは、同じランタイムの再入可能な負荷に対しては呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="b154f-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="b154f-120">再入不可能なランタイムの読み込み、コールバック関数への呼び出しがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="b154f-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="b154f-121">コールバック関数では、次のプロトタイプには。</span><span class="sxs-lookup"><span data-stu-id="b154f-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="b154f-122">コールバック関数のプロトタイプは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b154f-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="b154f-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="b154f-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="b154f-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="b154f-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="b154f-125">ホストにより、再入可能な方法で読み込まれる別のランタイムの読み込みまたはしているつもりの場合、`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`次のように、コールバック関数を使用する必要がありますに用意されているパラメーター。</span><span class="sxs-lookup"><span data-stu-id="b154f-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="b154f-126">`pfnCallbackThreadSet` このような負荷が試みられる前に、実行時の負荷を引き起こす可能性のあるスレッドから呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b154f-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="b154f-127">`pfnCallbackThreadUnset` スレッドがランタイム負荷がかかるおそれが不要になった場合 (および初期コールバックから戻る前に) 呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b154f-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="b154f-128">`pfnCallbackThreadSet` および`pfnCallbackThreadUnset`再入不可能なは、どちらもします。</span><span class="sxs-lookup"><span data-stu-id="b154f-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b154f-129">ホスト アプリケーションを呼び出してはならない`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`のスコープ外、`pCallbackFunction`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b154f-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b154f-130">要件</span><span class="sxs-lookup"><span data-stu-id="b154f-130">Requirements</span></span>  
 <span data-ttu-id="b154f-131">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b154f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b154f-132">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b154f-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b154f-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b154f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b154f-134">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b154f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b154f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b154f-135">See Also</span></span>  
 [<span data-ttu-id="b154f-136">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b154f-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="b154f-137">ホスティング</span><span class="sxs-lookup"><span data-stu-id="b154f-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
