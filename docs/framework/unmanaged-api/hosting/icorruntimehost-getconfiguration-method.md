---
title: "ICorRuntimeHost::GetConfiguration メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c0a95df2140d2eaf771fcd8f50cd733b9133e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="ab60e-102">ICorRuntimeHost::GetConfiguration メソッド</span><span class="sxs-lookup"><span data-stu-id="ab60e-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="ab60e-103">ホストが共通言語ランタイム (CLR) のコールバックの構成を指定できるようにするオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="ab60e-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab60e-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab60e-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab60e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab60e-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="ab60e-106">[out]アドレスへのポインター、 [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) CLR を構成するために使用できるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ab60e-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab60e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ab60e-107">Remarks</span></span>  
 <span data-ttu-id="ab60e-108">CLR は、初期化する前に構成する必要があります。それ以外の場合、`GetConfiguration`メソッドがエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="ab60e-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab60e-109">要件</span><span class="sxs-lookup"><span data-stu-id="ab60e-109">Requirements</span></span>  
 <span data-ttu-id="ab60e-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab60e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab60e-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab60e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab60e-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ab60e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab60e-113">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="ab60e-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab60e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab60e-114">See Also</span></span>  
 [<span data-ttu-id="ab60e-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab60e-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
