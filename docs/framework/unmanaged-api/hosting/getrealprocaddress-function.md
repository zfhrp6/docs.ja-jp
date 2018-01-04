---
title: "GetRealProcAddress 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ade1c902d00e991612406041ef0a0b2c1bb884e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="a4166-102">GetRealProcAddress 関数</span><span class="sxs-lookup"><span data-stu-id="a4166-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="a4166-103">共通言語ランタイム (CLR) の最後にインストールされているバージョンからエクスポートされる、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a4166-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="a4166-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="a4166-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4166-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4166-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4166-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4166-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="a4166-107">[in]関数の名前です。</span><span class="sxs-lookup"><span data-stu-id="a4166-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a4166-108">[out]関数のアドレスへのポインターを受け取る場所です。</span><span class="sxs-lookup"><span data-stu-id="a4166-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4166-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4166-109">Return Value</span></span>  
 <span data-ttu-id="a4166-110">このメソッドは、CorError.h で定義されている次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="a4166-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="a4166-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="a4166-111">Return code</span></span>|<span data-ttu-id="a4166-112">説明</span><span class="sxs-lookup"><span data-stu-id="a4166-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a4166-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4166-113">S_OK</span></span>|<span data-ttu-id="a4166-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="a4166-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4166-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a4166-115">E_POINTER</span></span>|<span data-ttu-id="a4166-116">`ppv` が無効です。</span><span class="sxs-lookup"><span data-stu-id="a4166-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="a4166-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="a4166-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="a4166-118">関数は、ランタイムからはエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="a4166-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4166-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4166-119">Requirements</span></span>  
 <span data-ttu-id="a4166-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4166-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4166-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4166-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4166-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4166-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4166-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4166-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4166-124">参照</span><span class="sxs-lookup"><span data-stu-id="a4166-124">See Also</span></span>  
 [<span data-ttu-id="a4166-125">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="a4166-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
