---
title: "StrongNameKeyInstall 関数"
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
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a8dbc84f375b7bbbad47971936650d81c5c63df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="4ecf0-102">StrongNameKeyInstall 関数</span><span class="sxs-lookup"><span data-stu-id="4ecf0-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="4ecf0-103">公開/秘密キー ペアをコンテナーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="4ecf0-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-104">This function has been deprecated.</span></span> <span data-ttu-id="4ecf0-105">使用して、 [iclrstrongname::strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ecf0-106">構文</span><span class="sxs-lookup"><span data-stu-id="4ecf0-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ecf0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ecf0-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4ecf0-108">[in]キー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-108">[in] The name of the key container.</span></span> <span data-ttu-id="4ecf0-109">`wszKeyContainer`空でない文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="4ecf0-110">[in]バイナリのキーのペア。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="4ecf0-111">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ecf0-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ecf0-112">Return Value</span></span>  
 <span data-ttu-id="4ecf0-113">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ecf0-114">コメント</span><span class="sxs-lookup"><span data-stu-id="4ecf0-114">Remarks</span></span>  
 <span data-ttu-id="4ecf0-115">使用して、 [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)キー コンテナーを削除する関数。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="4ecf0-116">場合、`StrongNameKeyInstall`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ecf0-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="4ecf0-117">Requirements</span></span>  
 <span data-ttu-id="4ecf0-118">**プラットフォーム:** WindSee[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ecf0-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4ecf0-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4ecf0-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ecf0-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ecf0-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ecf0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ecf0-122">参照</span><span class="sxs-lookup"><span data-stu-id="4ecf0-122">See Also</span></span>  
 [<span data-ttu-id="4ecf0-123">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="4ecf0-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="4ecf0-124">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="4ecf0-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="4ecf0-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ecf0-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
