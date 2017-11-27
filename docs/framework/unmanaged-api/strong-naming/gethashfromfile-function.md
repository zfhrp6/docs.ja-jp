---
title: "GetHashFromFile 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFile
helpviewer_keywords: GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c8e84881822cbafa8c43c3669f7522c390d5c5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="2c6f1-102">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="2c6f1-102">GetHashFromFile Function</span></span>
<span data-ttu-id="2c6f1-103">指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="2c6f1-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-104">This function has been deprecated.</span></span> <span data-ttu-id="2c6f1-105">使用して、 [iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6f1-106">構文</span><span class="sxs-lookup"><span data-stu-id="2c6f1-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c6f1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c6f1-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="2c6f1-108">[in]ハッシュには、ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2c6f1-109">[入力、出力].ハッシュを生成するときに使用するアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="2c6f1-110">有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="2c6f1-111">場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2c6f1-112">[out]生成されたハッシュを含むバイト配列。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2c6f1-113">[in]バッファーの最大サイズを`pbHash`を指します。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2c6f1-114">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c6f1-115">コメント</span><span class="sxs-lookup"><span data-stu-id="2c6f1-115">Remarks</span></span>  
 <span data-ttu-id="2c6f1-116">この関数は、同じ[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)ファイル名の指定は、Unicode ではなく ANSI ことを除き、します。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c6f1-117">要件</span><span class="sxs-lookup"><span data-stu-id="2c6f1-117">Requirements</span></span>  
 <span data-ttu-id="2c6f1-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c6f1-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2c6f1-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2c6f1-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c6f1-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c6f1-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c6f1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6f1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c6f1-122">See Also</span></span>  
 [<span data-ttu-id="2c6f1-123">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="2c6f1-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="2c6f1-124">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="2c6f1-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="2c6f1-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c6f1-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
