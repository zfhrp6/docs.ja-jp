---
title: ICLRStrongName::StrongNameKeyDelete メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9cd423bd351d9e4b12f21fe3a4a52c9909b7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="65d8a-102">ICLRStrongName::StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="65d8a-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="65d8a-103">指定したキー コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="65d8a-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d8a-104">構文</span><span class="sxs-lookup"><span data-stu-id="65d8a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65d8a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65d8a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="65d8a-106">[in]削除するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="65d8a-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65d8a-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="65d8a-107">Return Value</span></span>  
 <span data-ttu-id="65d8a-108">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="65d8a-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65d8a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="65d8a-109">Remarks</span></span>  
 <span data-ttu-id="65d8a-110">使用して、 [iclrstrongname::strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)公開/秘密キー ペアをコンテナーにインポートする方法です。</span><span class="sxs-lookup"><span data-stu-id="65d8a-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d8a-111">要件</span><span class="sxs-lookup"><span data-stu-id="65d8a-111">Requirements</span></span>  
 <span data-ttu-id="65d8a-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="65d8a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d8a-113">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="65d8a-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="65d8a-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="65d8a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65d8a-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d8a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d8a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="65d8a-116">See Also</span></span>  
 [<span data-ttu-id="65d8a-117">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="65d8a-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="65d8a-118">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65d8a-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
