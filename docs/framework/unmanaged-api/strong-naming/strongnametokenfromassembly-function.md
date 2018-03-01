---
title: "StrongNameTokenFromAssembly 関数"
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
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29414522eb2586b00ba3158d79155675cb468815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="cb014-102">StrongNameTokenFromAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="cb014-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="cb014-103">指定したアセンブリ ファイルから、厳密な名前のトークンを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb014-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="cb014-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="cb014-104">This function has been deprecated.</span></span> <span data-ttu-id="cb014-105">使用して、 [iclrstrongname::strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="cb014-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb014-106">構文</span><span class="sxs-lookup"><span data-stu-id="cb014-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb014-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb014-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cb014-108">[in]アセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="cb014-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="cb014-109">[out]厳密な名前が返されたトークンです。</span><span class="sxs-lookup"><span data-stu-id="cb014-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="cb014-110">[out]厳密な名前のトークンのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="cb014-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb014-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="cb014-111">Return Value</span></span>  
 <span data-ttu-id="cb014-112">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="cb014-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb014-113">コメント</span><span class="sxs-lookup"><span data-stu-id="cb014-113">Remarks</span></span>  
 <span data-ttu-id="cb014-114">厳密な名前のトークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="cb014-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="cb014-115">トークンは、アセンブリの署名に使用する公開キーから作成される 64 ビット ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="cb014-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="cb014-116">トークンは、アセンブリの厳密な名前の一部であるし、アセンブリのメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="cb014-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="cb014-117">トークンの作成後を呼び出す必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。</span><span class="sxs-lookup"><span data-stu-id="cb014-117">After the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="cb014-118">場合、`StrongNameTokenFromAssembly`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="cb014-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb014-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="cb014-119">Requirements</span></span>  
 <span data-ttu-id="cb014-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb014-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb014-121">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cb014-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cb014-122">**ライブラリ:** mscoree.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb014-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="cb014-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb014-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb014-124">参照</span><span class="sxs-lookup"><span data-stu-id="cb014-124">See Also</span></span>  
 [<span data-ttu-id="cb014-125">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="cb014-125">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="cb014-126">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="cb014-126">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="cb014-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb014-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
