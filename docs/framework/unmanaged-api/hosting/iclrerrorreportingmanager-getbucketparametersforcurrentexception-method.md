---
title: "ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド"
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
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f920ceb802231112ef1b855fd0a78d3a0e6ca4c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="647d4-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="647d4-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="647d4-103">呼び出し元のスレッドで現在の例外のワトソン バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="647d4-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="647d4-104">A*バケット*同じコードの欠陥に関連するエラーのデータのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="647d4-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="647d4-105">*ワトソン博士*例外に関連付けられているデータ収集および分析用のテクノロジのセットを指します。</span><span class="sxs-lookup"><span data-stu-id="647d4-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647d4-106">構文</span><span class="sxs-lookup"><span data-stu-id="647d4-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="647d4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="647d4-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="647d4-108">[out]ポインター、 [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)例外のエラー データを格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="647d4-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="647d4-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="647d4-109">Requirements</span></span>  
 <span data-ttu-id="647d4-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="647d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="647d4-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="647d4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="647d4-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="647d4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="647d4-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="647d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647d4-114">参照</span><span class="sxs-lookup"><span data-stu-id="647d4-114">See Also</span></span>  
 [<span data-ttu-id="647d4-115">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="647d4-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
