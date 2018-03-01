---
title: "INotifyConnection2::UnregisterNotifySource メソッド"
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
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 308055a0b8a5d07d93838479de6c1dae3c29517d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="3eff6-102">INotifyConnection2::UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="3eff6-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="3eff6-103">接続から、指定された通知のソース オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="3eff6-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eff6-104">構文</span><span class="sxs-lookup"><span data-stu-id="3eff6-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3eff6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3eff6-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="3eff6-106">[in]登録解除する通知オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="3eff6-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3eff6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3eff6-107">Return Value</span></span>  
 <span data-ttu-id="3eff6-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="3eff6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eff6-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="3eff6-109">Requirements</span></span>  
 <span data-ttu-id="3eff6-110">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3eff6-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eff6-111">参照</span><span class="sxs-lookup"><span data-stu-id="3eff6-111">See Also</span></span>  
 [<span data-ttu-id="3eff6-112">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3eff6-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="3eff6-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3eff6-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="3eff6-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3eff6-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="3eff6-115">RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="3eff6-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
