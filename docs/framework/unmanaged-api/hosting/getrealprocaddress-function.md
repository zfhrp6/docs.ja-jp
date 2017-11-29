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
ms.openlocfilehash: 53e51bcf72f1a59f5c471564022d0d8c415381a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="8cbde-102">GetRealProcAddress 関数</span><span class="sxs-lookup"><span data-stu-id="8cbde-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="8cbde-103">共通言語ランタイム (CLR) の最後にインストールされているバージョンからエクスポートされる、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8cbde-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="8cbde-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="8cbde-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbde-105">構文</span><span class="sxs-lookup"><span data-stu-id="8cbde-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8cbde-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8cbde-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="8cbde-107">[in]関数の名前です。</span><span class="sxs-lookup"><span data-stu-id="8cbde-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8cbde-108">[out]関数のアドレスへのポインターを受け取る場所です。</span><span class="sxs-lookup"><span data-stu-id="8cbde-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cbde-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8cbde-109">Return Value</span></span>  
 <span data-ttu-id="8cbde-110">このメソッドは、CorError.h で定義されている次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="8cbde-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="8cbde-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="8cbde-111">Return code</span></span>|<span data-ttu-id="8cbde-112">説明</span><span class="sxs-lookup"><span data-stu-id="8cbde-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8cbde-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cbde-113">S_OK</span></span>|<span data-ttu-id="8cbde-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="8cbde-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="8cbde-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8cbde-115">E_POINTER</span></span>|<span data-ttu-id="8cbde-116">`ppv` が無効です。</span><span class="sxs-lookup"><span data-stu-id="8cbde-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="8cbde-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="8cbde-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="8cbde-118">関数は、ランタイムからはエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="8cbde-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cbde-119">要件</span><span class="sxs-lookup"><span data-stu-id="8cbde-119">Requirements</span></span>  
 <span data-ttu-id="8cbde-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8cbde-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbde-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8cbde-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cbde-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8cbde-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cbde-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbde-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbde-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cbde-124">See Also</span></span>  
 [<span data-ttu-id="8cbde-125">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="8cbde-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
