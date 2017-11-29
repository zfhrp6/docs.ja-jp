---
title: "StrongNameSignatureVerificationFromImage 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab890451c44b19be6472ae6c7da060ae71612bc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="3aa31-102">StrongNameSignatureVerificationFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="3aa31-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="3aa31-103">メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="3aa31-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="3aa31-104">This function has been deprecated.</span></span> <span data-ttu-id="3aa31-105">使用して、 [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="3aa31-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa31-106">構文</span><span class="sxs-lookup"><span data-stu-id="3aa31-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3aa31-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3aa31-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="3aa31-108">[in]マップされているアセンブリ マニフェストの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="3aa31-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3aa31-109">[in]マップされたイメージのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3aa31-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="3aa31-110">[in]検証動作を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="3aa31-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="3aa31-111">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3aa31-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="3aa31-112">`SN_INFLAG_FORCE_VER`(0x00000001) のレジストリ設定を上書きする必要がある場合でも強制的に検証します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="3aa31-113">`SN_INFLAG_INSTALL`(0x00000002) - これが初めてこのイメージ上で実行する検証であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="3aa31-114">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) のキャッシュで管理者特権を持っているユーザーにのみアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="3aa31-115">`SN_INFLAG_USER_ACCESS`(0x00000008) のアセンブリが現在のユーザーのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="3aa31-116">`SN_INFLAG_ALL_ACCESS`(0x00000010) のキャッシュはしないことを指定のアクセス制限を保証します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="3aa31-117">`SN_INFLAG_RUNTIME`(0x80000000) - 内部デバッグのために予約されています。</span><span class="sxs-lookup"><span data-stu-id="3aa31-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="3aa31-118">[out]追加の出力情報に対するフラグです。</span><span class="sxs-lookup"><span data-stu-id="3aa31-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="3aa31-119">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3aa31-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="3aa31-120">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - この値は設定`false`レジストリ設定のために、検証が成功したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aa31-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="3aa31-121">Return Value</span></span>  
 <span data-ttu-id="3aa31-122">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="3aa31-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aa31-123">コメント</span><span class="sxs-lookup"><span data-stu-id="3aa31-123">Remarks</span></span>  
 <span data-ttu-id="3aa31-124">場合、`StrongNameSignatureVerificationFromImage`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="3aa31-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aa31-125">要件</span><span class="sxs-lookup"><span data-stu-id="3aa31-125">Requirements</span></span>  
 <span data-ttu-id="3aa31-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3aa31-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aa31-127">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3aa31-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3aa31-128">**ライブラリ:** mscoree.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3aa31-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3aa31-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aa31-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa31-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="3aa31-130">See Also</span></span>  
 [<span data-ttu-id="3aa31-131">StrongNameSignatureVerificationFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="3aa31-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [<span data-ttu-id="3aa31-132">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3aa31-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
