---
title: ICLRMetaHost::EnumerateInstalledRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ed4c09d910db6fa2e61d44e4ac777f9b6095a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434282"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="3dcc2-102">ICLRMetaHost::EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="3dcc2-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>
<span data-ttu-id="3dcc2-103">含む有効な列挙体を返します[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)コンピューターにインストールされている共通言語ランタイム (CLR) の各バージョン用のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcc2-104">構文</span><span class="sxs-lookup"><span data-stu-id="3dcc2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dcc2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3dcc2-105">Parameters</span></span>  
 `ppEnumerator`  
 <span data-ttu-id="3dcc2-106">[out]列挙体[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)コンピューターにインストールされている CLR の各バージョンに対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-106">[out] An enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dcc2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3dcc2-107">Return Value</span></span>  
 <span data-ttu-id="3dcc2-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3dcc2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3dcc2-109">HRESULT</span></span>|<span data-ttu-id="3dcc2-110">説明</span><span class="sxs-lookup"><span data-stu-id="3dcc2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dcc2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3dcc2-111">S_OK</span></span>|<span data-ttu-id="3dcc2-112">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="3dcc2-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3dcc2-113">E_POINTER</span></span>|<span data-ttu-id="3dcc2-114">`ppEnumerator` が null です。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3dcc2-115">要件</span><span class="sxs-lookup"><span data-stu-id="3dcc2-115">Requirements</span></span>  
 <span data-ttu-id="3dcc2-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcc2-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3dcc2-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3dcc2-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dcc2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dcc2-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dcc2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcc2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dcc2-120">See Also</span></span>  
 [<span data-ttu-id="3dcc2-121">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dcc2-121">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="3dcc2-122">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3dcc2-122">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
