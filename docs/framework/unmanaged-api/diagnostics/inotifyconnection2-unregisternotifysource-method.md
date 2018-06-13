---
title: INotifyConnection2::UnregisterNotifySource メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4b4f90f918c872f3227ac22f4cccadcbf3194a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425481"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="a1d82-102">INotifyConnection2::UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="a1d82-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="a1d82-103">接続から、指定された通知のソース オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="a1d82-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d82-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1d82-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1d82-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1d82-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="a1d82-106">[in]登録解除する通知オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a1d82-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1d82-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1d82-107">Return Value</span></span>  
 <span data-ttu-id="a1d82-108">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="a1d82-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d82-109">要件</span><span class="sxs-lookup"><span data-stu-id="a1d82-109">Requirements</span></span>  
 <span data-ttu-id="a1d82-110">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a1d82-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d82-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1d82-111">See Also</span></span>  
 [<span data-ttu-id="a1d82-112">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d82-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="a1d82-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d82-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="a1d82-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d82-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="a1d82-115">RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="a1d82-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
