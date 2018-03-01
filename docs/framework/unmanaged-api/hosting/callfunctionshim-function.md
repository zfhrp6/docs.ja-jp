---
title: "CallFunctionShim 関数"
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
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12c399c876a244d0c27e34b41e08c284d7429bac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="87580-102">CallFunctionShim 関数</span><span class="sxs-lookup"><span data-stu-id="87580-102">CallFunctionShim Function</span></span>
<span data-ttu-id="87580-103">指定したライブラリ内の関数を、名前とパラメーターを指定して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="87580-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="87580-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="87580-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87580-105">構文</span><span class="sxs-lookup"><span data-stu-id="87580-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87580-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87580-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="87580-107">[in]関数を含むライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="87580-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="87580-108">[in]関数の名前です。</span><span class="sxs-lookup"><span data-stu-id="87580-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="87580-109">[in]関数に渡す 1 番目の引数。</span><span class="sxs-lookup"><span data-stu-id="87580-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="87580-110">[in]関数に渡す 2 番目の引数。</span><span class="sxs-lookup"><span data-stu-id="87580-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="87580-111">[in]関数が含まれているライブラリのバージョン。</span><span class="sxs-lookup"><span data-stu-id="87580-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="87580-112">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="87580-112">[in] Reserved for future use.</span></span> <span data-ttu-id="87580-113">このパラメーターに 0 を渡します。</span><span class="sxs-lookup"><span data-stu-id="87580-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87580-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="87580-114">Requirements</span></span>  
 <span data-ttu-id="87580-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87580-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87580-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="87580-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87580-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87580-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87580-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87580-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87580-119">参照</span><span class="sxs-lookup"><span data-stu-id="87580-119">See Also</span></span>  
 [<span data-ttu-id="87580-120">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="87580-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
