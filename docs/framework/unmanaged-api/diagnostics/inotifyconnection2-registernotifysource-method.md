---
title: "INotifyConnection2::RegisterNotifySource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifyConnection2.RegisterNotifySource
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 370f19d9fd1cbc268d43b9970b0cf27290796562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="bc1d8-102">INotifyConnection2::RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1d8-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="bc1d8-103">指定された通知のソースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc1d8-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc1d8-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc1d8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc1d8-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="bc1d8-106">[in]通知のソースとして使用するオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="bc1d8-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="bc1d8-107">[out]通知シンクとして使用するオブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bc1d8-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc1d8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bc1d8-108">Return Value</span></span>  
 <span data-ttu-id="bc1d8-109">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="bc1d8-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1d8-110">要件</span><span class="sxs-lookup"><span data-stu-id="bc1d8-110">Requirements</span></span>  
 <span data-ttu-id="bc1d8-111">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="bc1d8-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1d8-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc1d8-112">See Also</span></span>  
 [<span data-ttu-id="bc1d8-113">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc1d8-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="bc1d8-114">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc1d8-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="bc1d8-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc1d8-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="bc1d8-116">UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1d8-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
