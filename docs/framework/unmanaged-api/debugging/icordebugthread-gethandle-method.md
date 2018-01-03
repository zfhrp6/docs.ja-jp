---
title: "ICorDebugThread::GetHandle メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a932d04fef438e19176af565c92e0673339e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="52f4c-102">ICorDebugThread::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="52f4c-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="52f4c-103">この ICorDebugThread のアクティブな部分の現在のハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="52f4c-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f4c-104">構文</span><span class="sxs-lookup"><span data-stu-id="52f4c-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52f4c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52f4c-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="52f4c-106">[out]このスレッドのアクティブな部分のハンドルである HTHREAD へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52f4c-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f4c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="52f4c-107">Remarks</span></span>  
 <span data-ttu-id="52f4c-108">ハンドルは、プロセスを実行すると、スレッドのさまざまな部分は異なる場合がありますを変更できます。</span><span class="sxs-lookup"><span data-stu-id="52f4c-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="52f4c-109">このハンドルは、デバッグ API が所有します。</span><span class="sxs-lookup"><span data-stu-id="52f4c-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="52f4c-110">デバッガーを使用する前に複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52f4c-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f4c-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="52f4c-111">Requirements</span></span>  
 <span data-ttu-id="52f4c-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="52f4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f4c-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52f4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52f4c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f4c-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
