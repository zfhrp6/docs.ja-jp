---
title: "ICorDebugAppDomain::GetId メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetId
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a8dcbc1fd710513b2b27e92f4d2e1e1b5c72092
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="c288a-102">ICorDebugAppDomain::GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="c288a-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="c288a-103">アプリケーション ドメインの一意識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="c288a-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c288a-104">構文</span><span class="sxs-lookup"><span data-stu-id="c288a-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c288a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c288a-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="c288a-106">[out]アプリケーション ドメインの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="c288a-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c288a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c288a-107">Remarks</span></span>  
 <span data-ttu-id="c288a-108">アプリケーション ドメインの識別子は、格納しているプロセス内で一意です。</span><span class="sxs-lookup"><span data-stu-id="c288a-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c288a-109">要件</span><span class="sxs-lookup"><span data-stu-id="c288a-109">Requirements</span></span>  
 <span data-ttu-id="c288a-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c288a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c288a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c288a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c288a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c288a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c288a-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c288a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
