---
title: "ICLRStrongName::StrongNameKeyDelete メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyDelete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8fbb6af492007eb0dc2a9ea83c53e3559225428d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="e9fad-102">ICLRStrongName::StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fad-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="e9fad-103">指定したキー コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="e9fad-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9fad-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9fad-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9fad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9fad-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e9fad-106">[in]削除するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="e9fad-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9fad-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e9fad-107">Return Value</span></span>  
 <span data-ttu-id="e9fad-108">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="e9fad-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9fad-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e9fad-109">Remarks</span></span>  
 <span data-ttu-id="e9fad-110">使用して、 [iclrstrongname::strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)公開/秘密キー ペアをコンテナーにインポートする方法です。</span><span class="sxs-lookup"><span data-stu-id="e9fad-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9fad-111">要件</span><span class="sxs-lookup"><span data-stu-id="e9fad-111">Requirements</span></span>  
 <span data-ttu-id="e9fad-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9fad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9fad-113">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e9fad-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e9fad-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9fad-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9fad-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fad-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9fad-116">See Also</span></span>  
 [<span data-ttu-id="e9fad-117">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fad-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="e9fad-118">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9fad-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
