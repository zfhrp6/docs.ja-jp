---
title: "CoInitializeEE 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeEE
helpviewer_keywords: CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ca564830411a9df0d47cc9765958286bbd40f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="d620e-102">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="d620e-102">CoInitializeEE Function</span></span>
<span data-ttu-id="d620e-103">共通言語ランタイムの実行エンジンがプロセスに読み込まれることになります。</span><span class="sxs-lookup"><span data-stu-id="d620e-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="d620e-104">この関数は非推奨、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d620e-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="d620e-105">使用して、 [iclrruntimehost::start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="d620e-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d620e-106">構文</span><span class="sxs-lookup"><span data-stu-id="d620e-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d620e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d620e-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="d620e-108">[in]1 つ、 [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列挙定数。</span><span class="sxs-lookup"><span data-stu-id="d620e-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d620e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d620e-109">Return Value</span></span>  
 <span data-ttu-id="d620e-110">このメソッドは、Winerror.h、および次の表の値で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="d620e-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="d620e-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="d620e-111">Return code</span></span>|<span data-ttu-id="d620e-112">説明</span><span class="sxs-lookup"><span data-stu-id="d620e-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d620e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d620e-113">S_OK</span></span>|<span data-ttu-id="d620e-114">実行エンジンは正常に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d620e-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="d620e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d620e-115">S_FALSE</span></span>|<span data-ttu-id="d620e-116">実行エンジンは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d620e-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="d620e-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d620e-117">E_FAIL</span></span>|<span data-ttu-id="d620e-118">実行エンジンを読み込むことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="d620e-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d620e-119">コメント</span><span class="sxs-lookup"><span data-stu-id="d620e-119">Remarks</span></span>  
 <span data-ttu-id="d620e-120">このメソッドは、既に読み込まれていない場合に、実行エンジンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d620e-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d620e-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="d620e-121">Requirements</span></span>  
 <span data-ttu-id="d620e-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d620e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d620e-123">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d620e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d620e-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d620e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d620e-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d620e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d620e-126">参照</span><span class="sxs-lookup"><span data-stu-id="d620e-126">See Also</span></span>  
 [<span data-ttu-id="d620e-127">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="d620e-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
