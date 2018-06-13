---
title: CLRRuntimeHost コクラス
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59fed7519402b4c3c1b2405ea99f8ba484781e95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430744"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="5358d-102">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="5358d-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="5358d-103">ランタイムによってコードの実行を管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5358d-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5358d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5358d-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="5358d-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5358d-105">Interfaces</span></span>  
  
|<span data-ttu-id="5358d-106">Interface</span><span class="sxs-lookup"><span data-stu-id="5358d-106">Interface</span></span>|<span data-ttu-id="5358d-107">説明</span><span class="sxs-lookup"><span data-stu-id="5358d-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="5358d-108">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5358d-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="5358d-109">ランタイムによってアプリケーションの実行を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5358d-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="5358d-110">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5358d-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="5358d-111">ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5358d-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5358d-112">要件</span><span class="sxs-lookup"><span data-stu-id="5358d-112">Requirements</span></span>  
 <span data-ttu-id="5358d-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5358d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5358d-114">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="5358d-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="5358d-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5358d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5358d-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5358d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5358d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5358d-117">See Also</span></span>  
 [<span data-ttu-id="5358d-118">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="5358d-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
