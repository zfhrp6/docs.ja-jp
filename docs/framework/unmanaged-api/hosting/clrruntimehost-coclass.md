---
title: "CLRRuntimeHost コクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="fc435-102">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="fc435-102">CLRRuntimeHost Coclass</span></span>
<span data-ttu-id="fc435-103">ランタイムによってコードの実行を管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc435-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc435-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc435-104">Syntax</span></span>  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fc435-105">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc435-105">Interfaces</span></span>  
  
|<span data-ttu-id="fc435-106">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc435-106">Interface</span></span>|<span data-ttu-id="fc435-107">説明</span><span class="sxs-lookup"><span data-stu-id="fc435-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fc435-108">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc435-108">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|<span data-ttu-id="fc435-109">ランタイムによってアプリケーションの実行を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc435-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="fc435-110">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc435-110">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|<span data-ttu-id="fc435-111">ポータブル実行可能イメージの検証と検証エラーの詳細なレポート作成のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc435-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc435-112">要件</span><span class="sxs-lookup"><span data-stu-id="fc435-112">Requirements</span></span>  
 <span data-ttu-id="fc435-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc435-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc435-114">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="fc435-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fc435-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc435-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc435-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc435-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc435-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc435-117">See Also</span></span>  
 [<span data-ttu-id="fc435-118">ホスト コクラス</span><span class="sxs-lookup"><span data-stu-id="fc435-118">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
