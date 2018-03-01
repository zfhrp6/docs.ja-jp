---
title: "ICorDebugType::GetBase メソッド"
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
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c28c88988155cf5e00897858d4306e4cb2ea78a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="82388-102">ICorDebugType::GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="82388-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="82388-103">1 つが存在する場合、これによって表される型の基本型を表す ICorDebugType へのインターフェイス ポインターを取得`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="82388-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82388-104">構文</span><span class="sxs-lookup"><span data-stu-id="82388-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82388-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82388-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="82388-106">[out]アドレスへのポインター、`ICorDebugType`基本型を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="82388-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82388-107">コメント</span><span class="sxs-lookup"><span data-stu-id="82388-107">Remarks</span></span>  
 <span data-ttu-id="82388-108">型の基本データ型の検索はオブジェクトまたはその親クラスのすべてのフィールドに印刷などの共通のデバッガー機能を実装すると便利です。</span><span class="sxs-lookup"><span data-stu-id="82388-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82388-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="82388-109">Requirements</span></span>  
 <span data-ttu-id="82388-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82388-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82388-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82388-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82388-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82388-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82388-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82388-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
