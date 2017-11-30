---
title: "IDebuggerInfo::IsDebuggerAttached メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerInfo.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6e1f11939bc4f11b1fb49dc44f129176143fbca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="4c0eb-102">IDebuggerInfo::IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="4c0eb-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="4c0eb-103">このプロセスにマネージ デバッガーをアタッチするかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4c0eb-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c0eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="4c0eb-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c0eb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c0eb-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="4c0eb-106">[out]ある値へのポインター`true`マネージ デバッガーがプロセスに接続されている、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="4c0eb-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c0eb-107">要件</span><span class="sxs-lookup"><span data-stu-id="4c0eb-107">Requirements</span></span>  
 <span data-ttu-id="4c0eb-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c0eb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c0eb-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c0eb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c0eb-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c0eb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c0eb-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c0eb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c0eb-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c0eb-112">See Also</span></span>  
 [<span data-ttu-id="4c0eb-113">IDebuggerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c0eb-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
