---
title: GetHashFromFile 関数
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f98f888280090bfa613acf6ae37bc60ab63c371e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="de4d9-102">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="de4d9-102">GetHashFromFile Function</span></span>
<span data-ttu-id="de4d9-103">指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="de4d9-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="de4d9-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="de4d9-104">This function has been deprecated.</span></span> <span data-ttu-id="de4d9-105">使用して、 [iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="de4d9-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4d9-106">構文</span><span class="sxs-lookup"><span data-stu-id="de4d9-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de4d9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de4d9-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="de4d9-108">[in]ハッシュには、ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="de4d9-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="de4d9-109">[入力、出力].ハッシュを生成するときに使用するアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="de4d9-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="de4d9-110">有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。</span><span class="sxs-lookup"><span data-stu-id="de4d9-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="de4d9-111">場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。</span><span class="sxs-lookup"><span data-stu-id="de4d9-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="de4d9-112">[out]生成されたハッシュを含むバイト配列。</span><span class="sxs-lookup"><span data-stu-id="de4d9-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="de4d9-113">[in]バッファーの最大サイズを`pbHash`を指します。</span><span class="sxs-lookup"><span data-stu-id="de4d9-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="de4d9-114">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="de4d9-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de4d9-115">コメント</span><span class="sxs-lookup"><span data-stu-id="de4d9-115">Remarks</span></span>  
 <span data-ttu-id="de4d9-116">この関数は、同じ[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)ファイル名の指定は、Unicode ではなく ANSI ことを除き、します。</span><span class="sxs-lookup"><span data-stu-id="de4d9-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de4d9-117">要件</span><span class="sxs-lookup"><span data-stu-id="de4d9-117">Requirements</span></span>  
 <span data-ttu-id="de4d9-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="de4d9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de4d9-119">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="de4d9-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="de4d9-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="de4d9-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de4d9-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de4d9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4d9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="de4d9-122">See Also</span></span>  
 [<span data-ttu-id="de4d9-123">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="de4d9-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="de4d9-124">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="de4d9-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="de4d9-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de4d9-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
