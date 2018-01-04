---
title: "GetHashFromFileW 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7d62526a6ac9bb06a7de8287c9687933402bfb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="bec41-102">GetHashFromFileW 関数</span><span class="sxs-lookup"><span data-stu-id="bec41-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="bec41-103">Unicode 文字列で指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="bec41-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="bec41-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="bec41-104">This function has been deprecated.</span></span> <span data-ttu-id="bec41-105">使用して、 [iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="bec41-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec41-106">構文</span><span class="sxs-lookup"><span data-stu-id="bec41-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="bec41-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bec41-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="bec41-108">[in]ハッシュには、ファイルの Unicode の名前。</span><span class="sxs-lookup"><span data-stu-id="bec41-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bec41-109">[入力、出力].ハッシュを生成するときに使用するアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="bec41-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="bec41-110">有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。</span><span class="sxs-lookup"><span data-stu-id="bec41-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="bec41-111">場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。</span><span class="sxs-lookup"><span data-stu-id="bec41-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bec41-112">[out]生成されたハッシュを含むバイト配列。</span><span class="sxs-lookup"><span data-stu-id="bec41-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bec41-113">[in]バッファーの最大サイズを指す`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="bec41-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bec41-114">[out]サイズをバイト単位での`pbHash`します。</span><span class="sxs-lookup"><span data-stu-id="bec41-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bec41-115">コメント</span><span class="sxs-lookup"><span data-stu-id="bec41-115">Remarks</span></span>  
 <span data-ttu-id="bec41-116">この関数は、同じ[GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)ファイル名の指定は、ANSI ではなく Unicode ことを除き、します。</span><span class="sxs-lookup"><span data-stu-id="bec41-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec41-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="bec41-117">Requirements</span></span>  
 <span data-ttu-id="bec41-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bec41-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec41-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="bec41-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bec41-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bec41-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bec41-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec41-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec41-122">参照</span><span class="sxs-lookup"><span data-stu-id="bec41-122">See Also</span></span>  
 [<span data-ttu-id="bec41-123">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="bec41-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="bec41-124">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="bec41-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="bec41-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bec41-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
