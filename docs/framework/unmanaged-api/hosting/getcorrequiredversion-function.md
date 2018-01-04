---
title: "GetCORRequiredVersion 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORRequiredVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetCORRequiredVersion
helpviewer_keywords: GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65505243d7d1691f0458d614fd878b054916f113
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="f3863-102">GetCORRequiredVersion 関数</span><span class="sxs-lookup"><span data-stu-id="f3863-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="f3863-103">必要な共通言語ランタイム (CLR) バージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="f3863-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="f3863-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="f3863-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3863-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3863-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3863-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3863-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="f3863-107">[out]バージョン番号を指定する文字列を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="f3863-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f3863-108">[in]バッファーのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f3863-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f3863-109">[out]バッファー内のバイト数が返されます。</span><span class="sxs-lookup"><span data-stu-id="f3863-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3863-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f3863-110">Requirements</span></span>  
 <span data-ttu-id="f3863-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3863-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3863-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3863-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3863-113">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3863-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3863-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3863-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3863-115">参照</span><span class="sxs-lookup"><span data-stu-id="f3863-115">See Also</span></span>  
 [<span data-ttu-id="f3863-116">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="f3863-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
