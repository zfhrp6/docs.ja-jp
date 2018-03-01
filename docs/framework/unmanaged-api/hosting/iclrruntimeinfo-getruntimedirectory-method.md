---
title: "ICLRRuntimeInfo::GetRuntimeDirectory メソッド"
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
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f185ed474234a33988e1946b2f69da373096e19b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="bc8c7-102">ICLRRuntimeInfo::GetRuntimeDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="bc8c7-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="bc8c7-103">このインターフェイスに関連付けられている共通言語ランタイム (CLR) のインストール ディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="bc8c7-104">このメソッドは、 [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET Framework のバージョン 2.0、3.0、および 3.5 で提供される関数。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8c7-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc8c7-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc8c7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc8c7-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="bc8c7-107">[out]CLR のインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="bc8c7-108">インストール パスが完全修飾;たとえば、"c:\windows\microsoft.net\framework\v1.0.3705\\"です。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="bc8c7-109">[入力、出力].サイズを指定`pwzBuffer`バッファー オーバーランを回避します。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="bc8c7-110">場合`pwzBuffer`が null、`pchBuffer`の必要なサイズを返します`pwzBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc8c7-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="bc8c7-111">Return Value</span></span>  
 <span data-ttu-id="bc8c7-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bc8c7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc8c7-113">HRESULT</span></span>|<span data-ttu-id="bc8c7-114">説明</span><span class="sxs-lookup"><span data-stu-id="bc8c7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc8c7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc8c7-115">S_OK</span></span>|<span data-ttu-id="bc8c7-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="bc8c7-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bc8c7-117">E_POINTER</span></span>|<span data-ttu-id="bc8c7-118">`pwzBuffer` または `pchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc8c7-119">コメント</span><span class="sxs-lookup"><span data-stu-id="bc8c7-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc8c7-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="bc8c7-120">Requirements</span></span>  
 <span data-ttu-id="bc8c7-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc8c7-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bc8c7-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bc8c7-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc8c7-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc8c7-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc8c7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8c7-125">参照</span><span class="sxs-lookup"><span data-stu-id="bc8c7-125">See Also</span></span>  
 [<span data-ttu-id="bc8c7-126">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc8c7-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="bc8c7-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="bc8c7-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
