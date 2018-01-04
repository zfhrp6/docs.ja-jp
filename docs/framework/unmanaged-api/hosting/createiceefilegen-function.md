---
title: "CreateICeeFileGen 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e3f5f2f35e47ea938cde924dc4b15d7f4617500
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="f0398-102">CreateICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="f0398-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="f0398-103">作成、 [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f0398-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="f0398-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="f0398-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0398-105">構文</span><span class="sxs-lookup"><span data-stu-id="f0398-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0398-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0398-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="f0398-107">[out]新しいアドレスへのポインター`ICeeFileGen`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f0398-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0398-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f0398-108">Return Value</span></span>  
 <span data-ttu-id="f0398-109">このメソッドは、標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="f0398-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0398-110">コメント</span><span class="sxs-lookup"><span data-stu-id="f0398-110">Remarks</span></span>  
 <span data-ttu-id="f0398-111">`ICeeFileGen`オブジェクトが共通言語ランタイム (CLR) のポータブル実行可能 (PE) ファイルを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f0398-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="f0398-112">呼び出す、 [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)を破棄する関数、`ICeeFileGen`オブジェクトが完了します。</span><span class="sxs-lookup"><span data-stu-id="f0398-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0398-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="f0398-113">Requirements</span></span>  
 <span data-ttu-id="f0398-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0398-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0398-115">**ヘッダー:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="f0398-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="f0398-116">**ライブラリ:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="f0398-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="f0398-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0398-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0398-118">参照</span><span class="sxs-lookup"><span data-stu-id="f0398-118">See Also</span></span>  
 [<span data-ttu-id="f0398-119">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="f0398-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
