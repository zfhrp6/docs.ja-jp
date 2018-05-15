---
title: ICorDebugType::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="b19c5-102">ICorDebugType::GetType メソッド</span><span class="sxs-lookup"><span data-stu-id="b19c5-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="b19c5-103">共通言語ランタイム (CLR) のネイティブ型を記述する CorElementType 値を取得<xref:System.Type>この ICorDebugType によって表されます。</span><span class="sxs-lookup"><span data-stu-id="b19c5-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19c5-104">構文</span><span class="sxs-lookup"><span data-stu-id="b19c5-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b19c5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b19c5-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="b19c5-106">[out]値へのポインター、`CorElementType`を CLR を示す列挙体<xref:System.Type>この`ICorDebugType`を表します。</span><span class="sxs-lookup"><span data-stu-id="b19c5-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b19c5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b19c5-107">Remarks</span></span>  
 <span data-ttu-id="b19c5-108">場合の値`ty`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE のいずれかが、 [icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)メソッドを呼び出すことが、ジェネリック型のインスタンス化されていない型を取得します。 それ以外の場合、呼び出す必要はありません`ICorDebugType::GetClass`です。</span><span class="sxs-lookup"><span data-stu-id="b19c5-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19c5-109">要件</span><span class="sxs-lookup"><span data-stu-id="b19c5-109">Requirements</span></span>  
 <span data-ttu-id="b19c5-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b19c5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19c5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b19c5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b19c5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b19c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b19c5-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
