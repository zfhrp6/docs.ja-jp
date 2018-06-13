---
title: ICorDebugManagedCallback::LoadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1d920a97338bba3e90ec8f0c440f6dd2a93e722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416206"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="92eac-102">ICorDebugManagedCallback::LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="92eac-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="92eac-103">クラスが読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="92eac-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92eac-104">構文</span><span class="sxs-lookup"><span data-stu-id="92eac-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92eac-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92eac-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="92eac-106">[in]ICorDebugAppDomain を表すオブジェクトをクラスが読み込まれたアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92eac-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="92eac-107">[in]クラスを表す ICorDebugClass オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92eac-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92eac-108">コメント</span><span class="sxs-lookup"><span data-stu-id="92eac-108">Remarks</span></span>  
 <span data-ttu-id="92eac-109">このコールバックは、クラスを含むモジュールのクラスの読み込みが有効になっている場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="92eac-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="92eac-110">クラスの読み込みは動的モジュールを常に有効にします。</span><span class="sxs-lookup"><span data-stu-id="92eac-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="92eac-111">`LoadClass`コールバックが動的モジュールの新しく生成されたクラスにブレークポイントをバインドするには適切な期間を提供します。</span><span class="sxs-lookup"><span data-stu-id="92eac-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92eac-112">要件</span><span class="sxs-lookup"><span data-stu-id="92eac-112">Requirements</span></span>  
 <span data-ttu-id="92eac-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="92eac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92eac-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92eac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92eac-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92eac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92eac-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92eac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92eac-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="92eac-117">See Also</span></span>  
 [<span data-ttu-id="92eac-118">UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="92eac-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="92eac-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92eac-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
