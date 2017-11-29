---
title: "ICorDebugType::GetStaticFieldValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34a37ef9a28dd0e6325db9bee61146f14d4638a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="9b0fc-102">ICorDebugType::GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="9b0fc-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="9b0fc-103">指定したスタック フレームでトークンを指定したフィールドによって参照される静的フィールドの値を格納している ICorDebugValue オブジェクト インターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b0fc-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b0fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b0fc-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="9b0fc-106">[in]`mdFieldDef`静的フィールドを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="9b0fc-107">[in]スタック フレームを表す ICorDebugFrame へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9b0fc-108">[out]アドレスへのポインター、`ICorDebugValue`静的フィールドの値を格納します。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0fc-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9b0fc-109">Remarks</span></span>  
 <span data-ttu-id="9b0fc-110">`GetStaticFieldValue`メソッドとして使用できる型が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE 場合に、のみによって示される、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="9b0fc-111">非ジェネリック型の場合、操作を実行して`GetStaticFieldValue`を呼び出すことと同じ[icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass オブジェクトによって返される[icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="9b0fc-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="9b0fc-112">ジェネリック型の静的フィールドの値を特定のインスタンス化の基準としたされます。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="9b0fc-113">また、静的フィールドは、スレッド、コンテキスト、またはアプリケーション ドメインを基準とした可能性ありますでした、スタック フレームは適切な値を決定するデバッガーを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0fc-114">コメント</span><span class="sxs-lookup"><span data-stu-id="9b0fc-114">Remarks</span></span>  
 <span data-ttu-id="9b0fc-115">`GetStaticFieldValue`呼び出すときにのみ使用できます`ICorDebugType::GetType`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の値を返します。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0fc-116">要件</span><span class="sxs-lookup"><span data-stu-id="9b0fc-116">Requirements</span></span>  
 <span data-ttu-id="9b0fc-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b0fc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0fc-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b0fc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b0fc-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b0fc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b0fc-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0fc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
