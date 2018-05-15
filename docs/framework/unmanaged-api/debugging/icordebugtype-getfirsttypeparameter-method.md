---
title: ICorDebugType::GetFirstTypeParameter メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d6754d7a8224249582df56ab674932f065f581d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="45333-102">ICorDebugType::GetFirstTypeParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="45333-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="45333-103">1 つを表す ICorDebugType へのインターフェイス ポインターを取得<xref:System.Type>これによって表される型のパラメーター`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="45333-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45333-104">構文</span><span class="sxs-lookup"><span data-stu-id="45333-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45333-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45333-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="45333-106">[out]アドレスへのポインター、`ICorDebugType`を最初のパラメーターを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="45333-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45333-107">コメント</span><span class="sxs-lookup"><span data-stu-id="45333-107">Remarks</span></span>  
 <span data-ttu-id="45333-108">`GetFirstTypeParameter` 呼び出せるケースの場所の種類に関する追加情報では、多くても 1 つの型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="45333-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="45333-109">具体的には、使用できます、型が ELEMENT_TYPE_ARRAY、インポートする場合、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR 場合、によって示される、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="45333-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45333-110">要件</span><span class="sxs-lookup"><span data-stu-id="45333-110">Requirements</span></span>  
 <span data-ttu-id="45333-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="45333-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45333-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45333-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45333-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45333-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45333-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45333-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
