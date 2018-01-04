---
title: "IValidator インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: IValidator
helpviewer_keywords: IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afa255fa0b1baec35dbd8aa6e0beef62d240c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidator-interface"></a><span data-ttu-id="1a216-102">IValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a216-102">IValidator Interface</span></span>
<span data-ttu-id="1a216-103">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a216-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a216-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a216-104">Methods</span></span>  
  
|<span data-ttu-id="1a216-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a216-105">Method</span></span>|<span data-ttu-id="1a216-106">説明</span><span class="sxs-lookup"><span data-stu-id="1a216-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1a216-107">検証</span><span class="sxs-lookup"><span data-stu-id="1a216-107">Validate</span></span>|<span data-ttu-id="1a216-108">指定した PE または Microsoft intermediate language (MSIL) ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="1a216-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="1a216-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="1a216-109">FormatEventInfo</span></span>|<span data-ttu-id="1a216-110">指定された検証エラーに対応するエラー メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="1a216-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a216-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="1a216-111">Requirements</span></span>  
 <span data-ttu-id="1a216-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a216-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a216-113">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="1a216-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="1a216-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a216-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a216-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a216-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a216-116">参照</span><span class="sxs-lookup"><span data-stu-id="1a216-116">See Also</span></span>  
 [<span data-ttu-id="1a216-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a216-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1a216-118">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="1a216-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
