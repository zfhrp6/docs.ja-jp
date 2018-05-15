---
title: ICorDebugNativeFrame::GetRegisterSet メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6880ed3a2519ad7d4a415e4fcc4510668a0852f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="7ef91-102">ICorDebugNativeFrame::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="7ef91-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="7ef91-103">このスタック フレームのレジスタ セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="7ef91-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef91-104">構文</span><span class="sxs-lookup"><span data-stu-id="7ef91-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ef91-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ef91-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="7ef91-106">[out]アドレスへのポインター、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)このスタック フレームのレジスタを表すオブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="7ef91-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ef91-107">要件</span><span class="sxs-lookup"><span data-stu-id="7ef91-107">Requirements</span></span>  
 <span data-ttu-id="7ef91-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ef91-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ef91-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ef91-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ef91-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ef91-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ef91-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef91-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef91-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ef91-112">See Also</span></span>  
 
