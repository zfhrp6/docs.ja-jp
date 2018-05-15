---
title: ICorDebugManagedCallback::LoadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1d05914004d3c1fcc5ff109e854d01661367835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="b694d-102">ICorDebugManagedCallback::LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="b694d-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="b694d-103">共通言語ランタイム (CLR) アセンブリが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b694d-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b694d-104">構文</span><span class="sxs-lookup"><span data-stu-id="b694d-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b694d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b694d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b694d-106">[in]ICorDebugAppDomain を表すオブジェクトをアセンブリが読み込まれたアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b694d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="b694d-107">[in]アセンブリを表す ICorDebugAssembly オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b694d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b694d-108">要件</span><span class="sxs-lookup"><span data-stu-id="b694d-108">Requirements</span></span>  
 <span data-ttu-id="b694d-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b694d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b694d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b694d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b694d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b694d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b694d-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b694d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b694d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b694d-113">See Also</span></span>  
 [<span data-ttu-id="b694d-114">UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="b694d-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="b694d-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b694d-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
