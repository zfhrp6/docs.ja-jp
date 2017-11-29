---
title: "ICorDebugNativeFrame::GetRegisterSet メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7689632d41971d85417501e9a7f90712a07b34bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="cc3b9-102">ICorDebugNativeFrame::GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="cc3b9-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="cc3b9-103">このスタック フレームのレジスタ セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc3b9-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc3b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc3b9-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc3b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc3b9-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="cc3b9-106">[out]アドレスへのポインター、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)このスタック フレームのレジスタを表すオブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="cc3b9-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc3b9-107">要件</span><span class="sxs-lookup"><span data-stu-id="cc3b9-107">Requirements</span></span>  
 <span data-ttu-id="cc3b9-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc3b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc3b9-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc3b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc3b9-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc3b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc3b9-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc3b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3b9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc3b9-112">See Also</span></span>  
 
