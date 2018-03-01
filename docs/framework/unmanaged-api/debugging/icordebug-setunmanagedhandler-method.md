---
title: "ICorDebug::SetUnmanagedHandler メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c1b6da9db047321583de8c3c9238ed9ad4d4ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="f32f8-102">ICorDebug::SetUnmanagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="f32f8-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="f32f8-103">管理されていないイベントのイベント ハンドラー オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f32f8-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="f32f8-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f32f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f32f8-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="f32f8-106">[in]ポインター、 [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)アンマネージ イベントのイベント ハンドラーを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f32f8-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f32f8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f32f8-107">Remarks</span></span>  
 <span data-ttu-id="f32f8-108">イベント ハンドラー オブジェクトのアンマネージ呼び出しの後にイベントを設定する必要があります[icordebug::initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)と呼び出しの前に[icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)または[icordebug::debugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="f32f8-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="f32f8-109">ただし、レガシー目的のため、する必要はありません、最初のネイティブのデバッグ イベントが発生するまで、管理されていないイベントのイベント ハンドラー オブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="f32f8-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="f32f8-110">具体的には場合、 `ICorDebug::CreateProcess` CREATE_SUSPENDED フラグ、メイン スレッドが再開されるまで、イベントをディスパッチできないネイティブのデバッグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f32f8-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f32f8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="f32f8-111">Requirements</span></span>  
 <span data-ttu-id="f32f8-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f32f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f32f8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f32f8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f32f8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f32f8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f32f8-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f32f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32f8-116">参照</span><span class="sxs-lookup"><span data-stu-id="f32f8-116">See Also</span></span>  
 [<span data-ttu-id="f32f8-117">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f32f8-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
