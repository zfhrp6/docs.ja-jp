---
title: ICorDebugThread::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2dd4cded6800ce016d821f8e3ffe01dcb6264b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418260"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="728be-102">ICorDebugThread::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="728be-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="728be-103">共通言語ランタイム (CLR) のスレッドにインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="728be-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728be-104">構文</span><span class="sxs-lookup"><span data-stu-id="728be-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="728be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="728be-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="728be-106">[out]CLR スレッドを表す ICorDebugValue インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="728be-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="728be-107">要件</span><span class="sxs-lookup"><span data-stu-id="728be-107">Requirements</span></span>  
 <span data-ttu-id="728be-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="728be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="728be-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="728be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="728be-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="728be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="728be-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="728be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728be-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="728be-112">See Also</span></span>  
 <xref:System.Threading.Thread>
