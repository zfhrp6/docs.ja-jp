---
title: "StrongNameGetBlob 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="91dd2-102">StrongNameGetBlob 関数</span><span class="sxs-lookup"><span data-stu-id="91dd2-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="91dd2-103">指定したアドレスに実行可能ファイルのバイナリ表現を指定したバッファーに設定します。</span><span class="sxs-lookup"><span data-stu-id="91dd2-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="91dd2-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="91dd2-104">This function has been deprecated.</span></span> <span data-ttu-id="91dd2-105">使用して、 [iclrstrongname::strongnamegetblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="91dd2-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91dd2-106">構文</span><span class="sxs-lookup"><span data-stu-id="91dd2-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91dd2-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91dd2-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="91dd2-108">[in]読み込まれる実行可能ファイルへの有効なパス。</span><span class="sxs-lookup"><span data-stu-id="91dd2-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="91dd2-109">[in]実行可能ファイルの読み込み先となるバッファー。</span><span class="sxs-lookup"><span data-stu-id="91dd2-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="91dd2-110">[入力、出力].最大サイズ (バイト単位) を要求した`pbBlob`です。</span><span class="sxs-lookup"><span data-stu-id="91dd2-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="91dd2-111">関数が戻るとき、実際のサイズ (バイト単位) での`pbBlob`します。</span><span class="sxs-lookup"><span data-stu-id="91dd2-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91dd2-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="91dd2-112">Return Value</span></span>  
 <span data-ttu-id="91dd2-113">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="91dd2-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91dd2-114">コメント</span><span class="sxs-lookup"><span data-stu-id="91dd2-114">Remarks</span></span>  
 <span data-ttu-id="91dd2-115">場合、`StrongNameGetBlob`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="91dd2-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91dd2-116">要件</span><span class="sxs-lookup"><span data-stu-id="91dd2-116">Requirements</span></span>  
 <span data-ttu-id="91dd2-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="91dd2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91dd2-118">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="91dd2-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="91dd2-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="91dd2-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91dd2-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91dd2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91dd2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="91dd2-121">See Also</span></span>  
 [<span data-ttu-id="91dd2-122">StrongNameGetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="91dd2-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="91dd2-123">StrongNameGetBlobFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="91dd2-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="91dd2-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91dd2-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
