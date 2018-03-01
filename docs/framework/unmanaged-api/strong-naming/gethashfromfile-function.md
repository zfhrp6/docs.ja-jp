---
title: "GetHashFromFile 関数"
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
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="71fd7-102">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="71fd7-102">GetHashFromFile Function</span></span>
<span data-ttu-id="71fd7-103">指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="71fd7-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="71fd7-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="71fd7-104">This function has been deprecated.</span></span> <span data-ttu-id="71fd7-105">使用して、 [iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="71fd7-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71fd7-106">構文</span><span class="sxs-lookup"><span data-stu-id="71fd7-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71fd7-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71fd7-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="71fd7-108">[in]ハッシュには、ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="71fd7-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="71fd7-109">[入力、出力].ハッシュを生成するときに使用するアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="71fd7-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="71fd7-110">有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。</span><span class="sxs-lookup"><span data-stu-id="71fd7-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="71fd7-111">場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。</span><span class="sxs-lookup"><span data-stu-id="71fd7-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="71fd7-112">[out]生成されたハッシュを含むバイト配列。</span><span class="sxs-lookup"><span data-stu-id="71fd7-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="71fd7-113">[in]バッファーの最大サイズを`pbHash`を指します。</span><span class="sxs-lookup"><span data-stu-id="71fd7-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="71fd7-114">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="71fd7-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71fd7-115">コメント</span><span class="sxs-lookup"><span data-stu-id="71fd7-115">Remarks</span></span>  
 <span data-ttu-id="71fd7-116">この関数は、同じ[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)ファイル名の指定は、Unicode ではなく ANSI ことを除き、します。</span><span class="sxs-lookup"><span data-stu-id="71fd7-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71fd7-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="71fd7-117">Requirements</span></span>  
 <span data-ttu-id="71fd7-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="71fd7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71fd7-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="71fd7-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="71fd7-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="71fd7-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="71fd7-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71fd7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fd7-122">参照</span><span class="sxs-lookup"><span data-stu-id="71fd7-122">See Also</span></span>  
 [<span data-ttu-id="71fd7-123">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="71fd7-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="71fd7-124">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="71fd7-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="71fd7-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71fd7-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
