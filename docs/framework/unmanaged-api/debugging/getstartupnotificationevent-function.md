---
title: "GetStartupNotificationEvent 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 305350a9186c90af1e8646bc230536dcd2de47cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="b8c6c-102">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="b8c6c-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="b8c6c-103">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c6c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8c6c-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8c6c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8c6c-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="b8c6c-106">[in] 受信する CLR スタートアップ通知の送信元である対象プロセスのプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="b8c6c-107">[out] スタートアップ時に CLR によって通知されるハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8c6c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b8c6c-108">Return Value</span></span>  
 <span data-ttu-id="b8c6c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8c6c-109">S_OK</span></span>  
 <span data-ttu-id="b8c6c-110">スタートアップ通知イベントに対するハンドルを正常に取得しました。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="b8c6c-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b8c6c-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="b8c6c-112">`phStartupEvent` が nullであるか、または `debuggeePID` が現在実行されているプロセスを参照していません。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="b8c6c-113">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="b8c6c-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b8c6c-114">スタートアップ通知イベントに対するハンドルを取得できません。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8c6c-115">コメント</span><span class="sxs-lookup"><span data-stu-id="b8c6c-115">Remarks</span></span>  
 <span data-ttu-id="b8c6c-116">Windows オペレーティング システムでは、`debuggeePID` が OS プロセス識別子に対応づけられます。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="b8c6c-117">イベントは、通知元の CLR によってマネージ コードが実行される前に通知されます。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c6c-118">要件</span><span class="sxs-lookup"><span data-stu-id="b8c6c-118">Requirements</span></span>  
 <span data-ttu-id="b8c6c-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8c6c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c6c-120">**ヘッダー:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="b8c6c-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="b8c6c-121">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="b8c6c-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="b8c6c-122">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b8c6c-122">**.NET Framework Versions:** 3.5 SP1</span></span>
