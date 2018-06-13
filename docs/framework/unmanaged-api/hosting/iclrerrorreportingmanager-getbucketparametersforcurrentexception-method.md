---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f37bbe7d9e76d76bfe4c0f80b6f2343a5598bbfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431751"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="9183f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="9183f-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="9183f-103">呼び出し元のスレッドで現在の例外のワトソン バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="9183f-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="9183f-104">A*バケット*同じコードの欠陥に関連するエラーのデータのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="9183f-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="9183f-105">*ワトソン博士*例外に関連付けられているデータ収集および分析用のテクノロジのセットを指します。</span><span class="sxs-lookup"><span data-stu-id="9183f-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9183f-106">構文</span><span class="sxs-lookup"><span data-stu-id="9183f-106">Syntax</span></span>  
  
```  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9183f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9183f-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="9183f-108">[out]ポインター、 [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)例外のエラー データを格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="9183f-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9183f-109">要件</span><span class="sxs-lookup"><span data-stu-id="9183f-109">Requirements</span></span>  
 <span data-ttu-id="9183f-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9183f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9183f-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9183f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9183f-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9183f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9183f-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9183f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9183f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9183f-114">See Also</span></span>  
 [<span data-ttu-id="9183f-115">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9183f-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
