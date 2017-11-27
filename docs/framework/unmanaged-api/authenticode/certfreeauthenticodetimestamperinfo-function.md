---
title: "CertFreeAuthenticodeTimestamperInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeTimestamperInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8b6392e57e641d25d07580fcb6bf630f8d983be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="bf981-102">CertFreeAuthenticodeTimestamperInfo 関数</span><span class="sxs-lookup"><span data-stu-id="bf981-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="bf981-103">割り当てられたリソースを解放、 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="bf981-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf981-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf981-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf981-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf981-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="bf981-106">[入力、出力] 解放されるタイム スタンパー情報。</span><span class="sxs-lookup"><span data-stu-id="bf981-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="bf981-107">参照してください、 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="bf981-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf981-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf981-108">Return Value</span></span>  
 <span data-ttu-id="bf981-109">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="bf981-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bf981-110">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="bf981-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf981-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf981-111">See Also</span></span>  
 [<span data-ttu-id="bf981-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bf981-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
