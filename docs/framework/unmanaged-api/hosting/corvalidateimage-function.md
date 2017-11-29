---
title: "_CorValidateImage 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorValidateImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorValidateImage
helpviewer_keywords: _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e2396219a5e4bfd95a9dc7134e2e603ed7a15a3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="2be24-102">_CorValidateImage 関数</span><span class="sxs-lookup"><span data-stu-id="2be24-102">_CorValidateImage Function</span></span>
<span data-ttu-id="2be24-103">マネージ モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2be24-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be24-104">構文</span><span class="sxs-lookup"><span data-stu-id="2be24-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2be24-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2be24-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="2be24-106">[in]として検証するイメージの開始位置を指すポインターはマネージ コードです。</span><span class="sxs-lookup"><span data-stu-id="2be24-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="2be24-107">イメージは、メモリに既に読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2be24-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="2be24-108">[in]イメージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="2be24-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2be24-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2be24-109">Return Value</span></span>  
 <span data-ttu-id="2be24-110">この関数は、標準の値を返します`E_INVALIDARG`、 `E_OUTOFMEMORY`、 `E_UNEXPECTED`、および`E_FAIL`、だけでなく、次の値。</span><span class="sxs-lookup"><span data-stu-id="2be24-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="2be24-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="2be24-111">Return value</span></span>|<span data-ttu-id="2be24-112">説明</span><span class="sxs-lookup"><span data-stu-id="2be24-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="2be24-113">イメージが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="2be24-113">The image is invalid.</span></span> <span data-ttu-id="2be24-114">この値は、HRESULT 0xC000007BL を持っています。</span><span class="sxs-lookup"><span data-stu-id="2be24-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="2be24-115">イメージは有効です。</span><span class="sxs-lookup"><span data-stu-id="2be24-115">The image is valid.</span></span> <span data-ttu-id="2be24-116">この値は、HRESULT 0x00000000L を持っています。</span><span class="sxs-lookup"><span data-stu-id="2be24-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2be24-117">コメント</span><span class="sxs-lookup"><span data-stu-id="2be24-117">Remarks</span></span>  
 <span data-ttu-id="2be24-118">Windows XP およびそれ以降のバージョンでは、オペレーティング システム ローダーは、共通のオブジェクト ファイル coff ヘッダー内の COM 記述子ディレクトリ ビットを調べることによってマネージ モジュールをチェックします。</span><span class="sxs-lookup"><span data-stu-id="2be24-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="2be24-119">設定済みビットでは、マネージ モジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="2be24-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="2be24-120">MsCorEE.dll と呼び出し読み込む場合は、ローダーがマネージ モジュールを検出`_CorValidateImage`、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="2be24-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="2be24-121">イメージが有効なマネージ モジュールであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2be24-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="2be24-122">共通言語ランタイム (CLR) のエントリ ポイントにイメージ内のエントリ ポイントを変更します。</span><span class="sxs-lookup"><span data-stu-id="2be24-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="2be24-123">64 ビット バージョンの Windows でイメージを PE32 から pe 32 + 形式に変換することによってがメモリ内に変更されます。</span><span class="sxs-lookup"><span data-stu-id="2be24-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="2be24-124">マネージ モジュール イメージが読み込まれるときに、ローダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="2be24-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="2be24-125">実行可能イメージは、オペレーティング システム ローダーし、呼び出し、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数の実行可能ファイルで指定されたエントリ ポイントに関係なく、します。</span><span class="sxs-lookup"><span data-stu-id="2be24-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="2be24-126">ローダーの呼び出し、DLL アセンブリのイメージ、 [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="2be24-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="2be24-127">`_CorExeMain`または`_CorDllMain`は、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="2be24-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="2be24-128">CLR を初期化します。</span><span class="sxs-lookup"><span data-stu-id="2be24-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="2be24-129">アセンブリの CLR ヘッダーからマネージ エントリ ポイントを検索します。</span><span class="sxs-lookup"><span data-stu-id="2be24-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="2be24-130">実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="2be24-130">Begins execution.</span></span>  
  
 <span data-ttu-id="2be24-131">ローダーの呼び出し、 [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)管理されているときに機能モジュール イメージがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="2be24-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="2be24-132">ただし、この関数に任意のアクションを実行しませんだけを返します。</span><span class="sxs-lookup"><span data-stu-id="2be24-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be24-133">要件</span><span class="sxs-lookup"><span data-stu-id="2be24-133">Requirements</span></span>  
 <span data-ttu-id="2be24-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2be24-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be24-135">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2be24-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2be24-136">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2be24-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2be24-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be24-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be24-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="2be24-138">See Also</span></span>  
 [<span data-ttu-id="2be24-139">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2be24-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
