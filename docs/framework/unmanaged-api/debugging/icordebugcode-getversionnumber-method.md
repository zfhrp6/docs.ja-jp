---
title: ICorDebugCode::GetVersionNumber メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3d4609d79bb424cabc011122480f952f0f877f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411235"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="84646-102">ICorDebugCode::GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="84646-102">ICorDebugCode::GetVersionNumber Method</span></span>
<span data-ttu-id="84646-103">この"ICorDebugCode"を表すコードのバージョンを識別する 1 から始まる番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="84646-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84646-104">構文</span><span class="sxs-lookup"><span data-stu-id="84646-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32    *nVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84646-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84646-105">Parameters</span></span>  
 `nVersion`  
 <span data-ttu-id="84646-106">[out]コードのバージョン番号へのポインター。</span><span class="sxs-lookup"><span data-stu-id="84646-106">[out] A pointer to the version number of the code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84646-107">コメント</span><span class="sxs-lookup"><span data-stu-id="84646-107">Remarks</span></span>  
 <span data-ttu-id="84646-108">バージョン番号は、コードでエディット コンティニュ (EnC) 操作を実行するたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="84646-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84646-109">要件</span><span class="sxs-lookup"><span data-stu-id="84646-109">Requirements</span></span>  
 <span data-ttu-id="84646-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="84646-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84646-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84646-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84646-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84646-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84646-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84646-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84646-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="84646-114">See Also</span></span>  
 
