---
title: ICorDebugType::GetBase メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b96c6ab8fb9065e1a08ad45a7f4482ef0b32788b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418885"
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="966e5-102">ICorDebugType::GetBase メソッド</span><span class="sxs-lookup"><span data-stu-id="966e5-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="966e5-103">1 つが存在する場合、これによって表される型の基本型を表す ICorDebugType へのインターフェイス ポインターを取得`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="966e5-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="966e5-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="966e5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="966e5-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="966e5-106">[out]アドレスへのポインター、`ICorDebugType`基本型を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="966e5-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966e5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="966e5-107">Remarks</span></span>  
 <span data-ttu-id="966e5-108">型の基本データ型の検索はオブジェクトまたはその親クラスのすべてのフィールドに印刷などの共通のデバッガー機能を実装すると便利です。</span><span class="sxs-lookup"><span data-stu-id="966e5-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="966e5-109">要件</span><span class="sxs-lookup"><span data-stu-id="966e5-109">Requirements</span></span>  
 <span data-ttu-id="966e5-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="966e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="966e5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="966e5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="966e5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="966e5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="966e5-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="966e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
