---
title: "ICLRDebuggingLibraryProvider::ProvideLibrary メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf6860a616312504e3d23177734cb532405bd714
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="ff2cb-102">ICLRDebuggingLibraryProvider::ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="ff2cb-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="ff2cb-103">コールバック インターフェイスの共通言語ランタイム (CLR) バージョン固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff2cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff2cb-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff2cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff2cb-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="ff2cb-106">[in]要求されたモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-106">[in] The name of the module being requested .</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="ff2cb-107">[in]COFF ファイルのヘッダーの PE ファイルに格納されている日付時刻のタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="ff2cb-108">[in]`SizeOfImage` PE ファイルの COFF 省略可能なファイルのヘッダーに格納されているフィールドです。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="ff2cb-109">[out]要求されたモジュールへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff2cb-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff2cb-110">Return Value</span></span>  
 <span data-ttu-id="ff2cb-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ff2cb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff2cb-112">HRESULT</span></span>|<span data-ttu-id="ff2cb-113">説明</span><span class="sxs-lookup"><span data-stu-id="ff2cb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff2cb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff2cb-114">S_OK</span></span>|<span data-ttu-id="ff2cb-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ff2cb-116">例外</span><span class="sxs-lookup"><span data-stu-id="ff2cb-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff2cb-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ff2cb-117">Remarks</span></span>  
 <span data-ttu-id="ff2cb-118">`ProvideLibrary`により、デバッガーは mscordbi.dll mscordacwks.dll などの特定の CLR ファイルのデバッグに必要なモジュールを提供します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="ff2cb-119">モジュール ハンドルが有効になるまでの呼び出しが、 [iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)メソッドは、これら解放される可能性があります、この時点で、ハンドルを解放する、呼び出し元の責任であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="ff2cb-120">デバッガーは、すべて使用可能な方法を使用して、検索またはデバッグのモジュールを調達する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff2cb-121">この機能は、実行可能ファイル、および可能性のある悪意のあるコードが含まれているモジュールを提供する API の呼び出し元を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="ff2cb-122">セキュリティ上の予防措置として呼び出し元は、使用しないでください`ProvideLibrary`はそれ自体を実行するすべてのコードを配布します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="ff2cb-123">Mscordbi.dll または mscordacwks.dll などの既にリリースされてライブラリで重大なセキュリティ上の問題が検出された場合、shim にパッチできるの不適切なバージョンのファイルを認識するようにします。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="ff2cb-124">Shim は、によるパッチ形式のバージョンのファイルに対する要求を発行し、すべての要求に対する応答で提供される場合は、不適切なバージョンを拒否します。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="ff2cb-125">これは、shim の新しいバージョンに、ユーザーがパッチされている場合にのみに発生することができます。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="ff2cb-126">未修正のバージョンは、脆弱なままです。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2cb-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="ff2cb-127">Requirements</span></span>  
 <span data-ttu-id="ff2cb-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff2cb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2cb-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff2cb-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff2cb-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2cb-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2cb-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2cb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2cb-132">参照</span><span class="sxs-lookup"><span data-stu-id="ff2cb-132">See Also</span></span>  
 [<span data-ttu-id="ff2cb-133">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff2cb-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ff2cb-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ff2cb-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
