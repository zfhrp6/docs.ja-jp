---
title: "StrongNameTokenFromPublicKey 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: COM
f1_keywords: StrongNameTokenFromPublicKey
helpviewer_keywords: StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfde09f6383646f24077c3bdc0efa4b31bc50ba0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="f2dfd-102">StrongNameTokenFromPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="f2dfd-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="f2dfd-103">公開キーを表すトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-103">Gets a token representing a public key.</span></span> <span data-ttu-id="f2dfd-104">厳密な名前のトークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="f2dfd-105">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-105">This function has been deprecated.</span></span> <span data-ttu-id="f2dfd-106">使用して、 [iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dfd-107">構文</span><span class="sxs-lookup"><span data-stu-id="f2dfd-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2dfd-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2dfd-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="f2dfd-109">[in]型の構造体[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)厳密な名前の署名を生成するためのキー ペアの公開部分を格納しています。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="f2dfd-110">[in]サイズをバイト単位での`pbPublicKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f2dfd-111">[out]キーに対応する厳密な名前トークンが渡される`pbPublicKeyBlob`です。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="f2dfd-112">共通言語ランタイムは、トークンを返すメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="f2dfd-113">呼び出し元を使用してこのメモリを解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f2dfd-114">[out]厳密な名前が返されたトークンのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2dfd-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="f2dfd-115">Return Value</span></span>  
 <span data-ttu-id="f2dfd-116">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2dfd-117">コメント</span><span class="sxs-lookup"><span data-stu-id="f2dfd-117">Remarks</span></span>  
 <span data-ttu-id="f2dfd-118">厳密な名前のトークンは、メタデータに重要な情報を格納する場合は、領域を節約するために使用する公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="f2dfd-119">具体的には、厳密な名前のトークンは、依存アセンブリを参照するアセンブリ参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="f2dfd-120">場合、`StrongNameTokenFromPublicKey`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dfd-121">要件</span><span class="sxs-lookup"><span data-stu-id="f2dfd-121">Requirements</span></span>  
 <span data-ttu-id="f2dfd-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2dfd-123">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f2dfd-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f2dfd-124">**ライブラリ:** mscoree.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2dfd-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f2dfd-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2dfd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dfd-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2dfd-126">See Also</span></span>  
 [<span data-ttu-id="f2dfd-127">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="f2dfd-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="f2dfd-128">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="f2dfd-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="f2dfd-129">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="f2dfd-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
