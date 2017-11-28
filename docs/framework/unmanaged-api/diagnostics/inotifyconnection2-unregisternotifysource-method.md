---
title: "INotifyConnection2::UnregisterNotifySource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.UnregisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 063a146d31031f0cb14e00278819e8cd874f98c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="19eaa-102">INotifyConnection2::UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="19eaa-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="19eaa-103">接続から、指定された通知のソース オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="19eaa-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19eaa-104">構文</span><span class="sxs-lookup"><span data-stu-id="19eaa-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19eaa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19eaa-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="19eaa-106">[in]登録解除する通知オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="19eaa-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19eaa-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="19eaa-107">Return Value</span></span>  
 <span data-ttu-id="19eaa-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="19eaa-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19eaa-109">要件</span><span class="sxs-lookup"><span data-stu-id="19eaa-109">Requirements</span></span>  
 <span data-ttu-id="19eaa-110">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="19eaa-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19eaa-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="19eaa-111">See Also</span></span>  
 [<span data-ttu-id="19eaa-112">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19eaa-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="19eaa-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19eaa-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="19eaa-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19eaa-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="19eaa-115">RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="19eaa-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
