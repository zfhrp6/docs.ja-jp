---
title: GetRealProcAddress 関数
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256afe9a4304654ddb263a0671db7525f3bedcba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429638"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="83694-102">GetRealProcAddress 関数</span><span class="sxs-lookup"><span data-stu-id="83694-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="83694-103">共通言語ランタイム (CLR) の最後にインストールされているバージョンからエクスポートされる、指定された関数のアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="83694-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="83694-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="83694-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83694-105">構文</span><span class="sxs-lookup"><span data-stu-id="83694-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83694-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83694-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="83694-107">[in]関数の名前です。</span><span class="sxs-lookup"><span data-stu-id="83694-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="83694-108">[out]関数のアドレスへのポインターを受け取る場所です。</span><span class="sxs-lookup"><span data-stu-id="83694-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83694-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="83694-109">Return Value</span></span>  
 <span data-ttu-id="83694-110">このメソッドは、CorError.h で定義されている次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="83694-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="83694-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="83694-111">Return code</span></span>|<span data-ttu-id="83694-112">説明</span><span class="sxs-lookup"><span data-stu-id="83694-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="83694-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="83694-113">S_OK</span></span>|<span data-ttu-id="83694-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="83694-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="83694-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="83694-115">E_POINTER</span></span>|<span data-ttu-id="83694-116">`ppv` が無効です。</span><span class="sxs-lookup"><span data-stu-id="83694-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="83694-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="83694-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="83694-118">関数は、ランタイムからはエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="83694-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83694-119">要件</span><span class="sxs-lookup"><span data-stu-id="83694-119">Requirements</span></span>  
 <span data-ttu-id="83694-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83694-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83694-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83694-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83694-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83694-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83694-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83694-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83694-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="83694-124">See Also</span></span>  
 <span data-ttu-id="83694-125">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="83694-125">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
