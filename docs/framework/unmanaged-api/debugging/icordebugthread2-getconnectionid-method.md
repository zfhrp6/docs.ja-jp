---
title: "ICorDebugThread2::GetConnectionID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetConnectionID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae852fe91bdb15007437ea6f2c61cbaa49a6918b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="93f0c-102">ICorDebugThread2::GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="93f0c-102">ICorDebugThread2::GetConnectionID Method</span></span>
<span data-ttu-id="93f0c-103">この ICorDebugThread2 オブジェクトの接続識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="93f0c-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f0c-104">構文</span><span class="sxs-lookup"><span data-stu-id="93f0c-104">Syntax</span></span>  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93f0c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93f0c-105">Parameters</span></span>  
 `pdwConnectionId`  
 <span data-ttu-id="93f0c-106">[out]A`CONNID`接続識別子を表すです。</span><span class="sxs-lookup"><span data-stu-id="93f0c-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93f0c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="93f0c-107">Remarks</span></span>  
 <span data-ttu-id="93f0c-108">`GetConnectionID`にゼロが返される、`pdwConnectionId`パラメーターでは、このスレッドは、接続の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="93f0c-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="93f0c-109">このスレッドがの Microsoft SQL Server 2005 Analysis Services (SSAS)、インスタンスに接続されている場合、`CONNID`サーバー プロセス識別子 (SPID) にマップします。</span><span class="sxs-lookup"><span data-stu-id="93f0c-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f0c-110">要件</span><span class="sxs-lookup"><span data-stu-id="93f0c-110">Requirements</span></span>  
 <span data-ttu-id="93f0c-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93f0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f0c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93f0c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93f0c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93f0c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f0c-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
