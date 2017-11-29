---
title: "StrongNameTokenFromAssemblyEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssemblyEx
helpviewer_keywords: StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef530595d92995124c590e70ac5ffc32a228c67a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="0bd4a-102">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="0bd4a-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="0bd4a-103">指定したアセンブリ ファイルから厳密な名前トークンを作成し、公開キー トークンを表すを返します。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="0bd4a-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-104">This function has been deprecated.</span></span> <span data-ttu-id="0bd4a-105">使用して、 [iclrstrongname::strongnametokenfromassemblyex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd4a-106">構文</span><span class="sxs-lookup"><span data-stu-id="0bd4a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bd4a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0bd4a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0bd4a-108">[in]アセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="0bd4a-109">[out]厳密な名前が返されたトークンです。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="0bd4a-110">[out]厳密な名前のトークンのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="0bd4a-111">[out]返される公開キー。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="0bd4a-112">[out]公開キーのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bd4a-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="0bd4a-113">Return Value</span></span>  
 <span data-ttu-id="0bd4a-114">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bd4a-115">コメント</span><span class="sxs-lookup"><span data-stu-id="0bd4a-115">Remarks</span></span>  
 <span data-ttu-id="0bd4a-116">厳密な名前のトークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="0bd4a-117">トークンは、アセンブリの署名に使用する公開キーから作成される 64 ビット ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="0bd4a-118">トークンは、アセンブリの厳密な名前の一部であるし、アセンブリのメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="0bd4a-119">キーを取得し、トークンを作成を呼び出す必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="0bd4a-120">場合、`StrongNameTokenFromAssemblyEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd4a-121">要件</span><span class="sxs-lookup"><span data-stu-id="0bd4a-121">Requirements</span></span>  
 <span data-ttu-id="0bd4a-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd4a-123">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0bd4a-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0bd4a-124">**ライブラリ:** mscoree.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0bd4a-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="0bd4a-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd4a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd4a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bd4a-126">See Also</span></span>  
 [<span data-ttu-id="0bd4a-127">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="0bd4a-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="0bd4a-128">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="0bd4a-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="0bd4a-129">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0bd4a-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
