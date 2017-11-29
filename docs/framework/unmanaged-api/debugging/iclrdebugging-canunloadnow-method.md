---
title: "ICLRDebugging::CanUnloadNow メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging.CanUnloadNow Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b013231666ca6dfde5ab16e58023da1ae2a72941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="c6c86-102">ICLRDebugging::CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="c6c86-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="c6c86-103">ライブラリで提供されているかどうかを判断、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)インターフェイスが使用されているまたは読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="c6c86-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c86-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6c86-104">Syntax</span></span>  
  
```  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6c86-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6c86-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="c6c86-106">[in]ターゲット プロセスのモジュールのベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="c6c86-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6c86-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="c6c86-107">Return Value</span></span>  
 <span data-ttu-id="c6c86-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="c6c86-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c6c86-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6c86-109">HRESULT</span></span>|<span data-ttu-id="c6c86-110">説明</span><span class="sxs-lookup"><span data-stu-id="c6c86-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6c86-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6c86-111">S_OK</span></span>|<span data-ttu-id="c6c86-112">によって参照されるモジュール`hmodule`アンロードできます。</span><span class="sxs-lookup"><span data-stu-id="c6c86-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="c6c86-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c6c86-113">S_FALSE</span></span>|<span data-ttu-id="c6c86-114">によって参照されるモジュール`hmodule`はまだ使用されています。</span><span class="sxs-lookup"><span data-stu-id="c6c86-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="c6c86-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="c6c86-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="c6c86-116">指定されたモジュールが CLR モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="c6c86-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c6c86-117">例外</span><span class="sxs-lookup"><span data-stu-id="c6c86-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6c86-118">コメント</span><span class="sxs-lookup"><span data-stu-id="c6c86-118">Remarks</span></span>  
 <span data-ttu-id="c6c86-119">このメソッドはすべてかどうかを確認のインスタンス`ICorDebug*`インターフェイスが解放されているし、スレッドが現在内に存在する呼び出し、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c6c86-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6c86-120">要件</span><span class="sxs-lookup"><span data-stu-id="c6c86-120">Requirements</span></span>  
 <span data-ttu-id="c6c86-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6c86-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6c86-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6c86-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6c86-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6c86-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6c86-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6c86-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c86-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6c86-125">See Also</span></span>  
 [<span data-ttu-id="c6c86-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c6c86-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c6c86-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c6c86-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
