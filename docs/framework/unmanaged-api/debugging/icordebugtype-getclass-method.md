---
title: "ICorDebugType::GetClass メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32462159bc00ea766af3e3bc0f9d3d7a35eb2e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="02f52-102">ICorDebugType::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="02f52-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="02f52-103">インスタンス化されていないジェネリック型を表す ICorDebugClass へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="02f52-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f52-104">構文</span><span class="sxs-lookup"><span data-stu-id="02f52-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02f52-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02f52-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="02f52-106">[out]アドレスへのポインター、`ICorDebugClass`をインスタンス化されていないジェネリック型を表すインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="02f52-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f52-107">コメント</span><span class="sxs-lookup"><span data-stu-id="02f52-107">Remarks</span></span>  
 <span data-ttu-id="02f52-108">`GetClass`特定の条件下でのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="02f52-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="02f52-109">呼び出す[icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)呼び出す前に`GetClass`です。</span><span class="sxs-lookup"><span data-stu-id="02f52-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="02f52-110">場合`ICorDebugType::GetType`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE、CorElementType 値を返します`GetClass`を呼び出すと、ジェネリック型のインスタンス化されていない型を取得します。</span><span class="sxs-lookup"><span data-stu-id="02f52-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f52-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="02f52-111">Requirements</span></span>  
 <span data-ttu-id="02f52-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="02f52-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f52-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02f52-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02f52-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f52-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f52-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f52-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
