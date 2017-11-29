---
title: "StrongNameGetBlobFromImage 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 423f874796320d1fbcda2ab642c71b7072642569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="59800-102">StrongNameGetBlobFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="59800-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="59800-103">指定されたメモリ アドレスでのアセンブリ イメージのバイナリ表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="59800-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="59800-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="59800-104">This function has been deprecated.</span></span> <span data-ttu-id="59800-105">使用して、 [iclrstrongname::strongnamegetblobfromimage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="59800-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59800-106">構文</span><span class="sxs-lookup"><span data-stu-id="59800-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59800-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59800-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="59800-108">[in]マップされているアセンブリ マニフェストのメモリ アドレス。</span><span class="sxs-lookup"><span data-stu-id="59800-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="59800-109">[in]サイズ (バイト単位) を画像の`pbBase`します。</span><span class="sxs-lookup"><span data-stu-id="59800-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="59800-110">[in]画像のバイナリ表現を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="59800-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="59800-111">[入力、出力].最大サイズ (バイト単位) を要求した`pbBlob`です。</span><span class="sxs-lookup"><span data-stu-id="59800-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="59800-112">関数が戻るとき、実際のサイズ (バイト単位) での`pbBlob`します。</span><span class="sxs-lookup"><span data-stu-id="59800-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59800-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="59800-113">Return Value</span></span>  
 <span data-ttu-id="59800-114">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="59800-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59800-115">コメント</span><span class="sxs-lookup"><span data-stu-id="59800-115">Remarks</span></span>  
 <span data-ttu-id="59800-116">場合、`StrongNameGetBlobFromImage`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="59800-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59800-117">要件</span><span class="sxs-lookup"><span data-stu-id="59800-117">Requirements</span></span>  
 <span data-ttu-id="59800-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="59800-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59800-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="59800-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="59800-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="59800-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59800-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59800-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59800-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="59800-122">See Also</span></span>  
 [<span data-ttu-id="59800-123">StrongNameGetBlobFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="59800-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="59800-124">StrongNameGetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="59800-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="59800-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59800-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
