---
title: ICorDebugAppDomain::GetId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8122f1b5017faac3425d59d12d77f84180134d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401630"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="8ed15-102">ICorDebugAppDomain::GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="8ed15-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="8ed15-103">アプリケーション ドメインの一意識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ed15-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed15-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ed15-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ed15-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ed15-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="8ed15-106">[out]アプリケーション ドメインの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="8ed15-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ed15-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8ed15-107">Remarks</span></span>  
 <span data-ttu-id="8ed15-108">アプリケーション ドメインの識別子は、格納しているプロセス内で一意です。</span><span class="sxs-lookup"><span data-stu-id="8ed15-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed15-109">要件</span><span class="sxs-lookup"><span data-stu-id="8ed15-109">Requirements</span></span>  
 <span data-ttu-id="8ed15-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ed15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed15-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ed15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ed15-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ed15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ed15-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
