---
title: ICorDebugBoxValue::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfc8800915009912716ec2ed9044a633a8ad0582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401746"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="a634f-102">ICorDebugBoxValue::GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="a634f-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="a634f-103">ボックス化された値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a634f-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a634f-104">構文</span><span class="sxs-lookup"><span data-stu-id="a634f-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a634f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a634f-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="a634f-106">[out]ボックス化された値を表す ICorDebugObjectValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a634f-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a634f-107">要件</span><span class="sxs-lookup"><span data-stu-id="a634f-107">Requirements</span></span>  
 <span data-ttu-id="a634f-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a634f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a634f-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a634f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a634f-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a634f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a634f-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a634f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
