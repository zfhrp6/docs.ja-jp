---
title: "ICorDebugThread2::GetConnectionID メソッド"
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
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28fa949de768191061bd747034a5c951a03b8596
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="fc31f-102">ICorDebugThread2::GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="fc31f-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="fc31f-103">この ICorDebugThread2 オブジェクトの接続識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="fc31f-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc31f-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc31f-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc31f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc31f-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="fc31f-106">[out]A`CONNID`接続識別子を表すです。</span><span class="sxs-lookup"><span data-stu-id="fc31f-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc31f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="fc31f-107">Remarks</span></span>  
 <span data-ttu-id="fc31f-108">`GetConnectionID`にゼロが返される、`pdwConnectionId`パラメーターでは、このスレッドは、接続の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="fc31f-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="fc31f-109">このスレッドがの Microsoft SQL Server 2005 Analysis Services (SSAS)、インスタンスに接続されている場合、`CONNID`サーバー プロセス識別子 (SPID) にマップします。</span><span class="sxs-lookup"><span data-stu-id="fc31f-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc31f-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="fc31f-110">Requirements</span></span>  
 <span data-ttu-id="fc31f-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc31f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc31f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc31f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc31f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc31f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc31f-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc31f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
