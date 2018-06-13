---
title: StrongNameSignatureVerificationEx2 メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d2ac3788b68626eb04a6f2cbac995b8e5b4ebf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442583"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="b5001-102">StrongNameSignatureVerificationEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="b5001-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="b5001-103">厳密な名前付きのアセンブリの署名を確認しの ECMA キーから実際のキーへのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5001-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5001-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5001-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5001-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5001-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b5001-106">[in]検証するアセンブリのポータブル実行可能 (.exe または .dll) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="b5001-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="b5001-107">[in]`true` 、それ以外のレジストリ設定を上書きする必要がある場合でも、検証を実行する`false`です。</span><span class="sxs-lookup"><span data-stu-id="b5001-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="b5001-108">[in]実際のキーの公開キーを ECMA からマッピングへのポインターの検証に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5001-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="b5001-109">[in]実際の ECMA パブリック キーの長さ。</span><span class="sxs-lookup"><span data-stu-id="b5001-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="b5001-110">[out]`true`厳密な名前の署名が確認済み、それ以外の場合は`false`します。</span><span class="sxs-lookup"><span data-stu-id="b5001-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="b5001-111">このパラメーターに設定されても`false`検証は、レジストリ設定のために成功した場合。</span><span class="sxs-lookup"><span data-stu-id="b5001-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5001-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b5001-112">Return Value</span></span>  
 <span data-ttu-id="b5001-113">`S_OK` 検証が成功した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="b5001-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5001-114">要件</span><span class="sxs-lookup"><span data-stu-id="b5001-114">Requirements</span></span>  
 <span data-ttu-id="b5001-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5001-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5001-116">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b5001-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b5001-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5001-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5001-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5001-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5001-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5001-119">See Also</span></span>  
 [<span data-ttu-id="b5001-120">StrongNameSignatureVerification メソッド</span><span class="sxs-lookup"><span data-stu-id="b5001-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="b5001-121">StrongNameSignatureVerificationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b5001-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="b5001-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5001-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
