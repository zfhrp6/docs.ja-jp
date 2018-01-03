---
title: "CreateVersionStringFromModule 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateVersionStringFromModule
api_location: dbgshim.dll
api_type: COM
f1_keywords: CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d7d545256393cfbe37216f0d6db064d5e7cb410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="83aab-102">CreateVersionStringFromModule 関数</span><span class="sxs-lookup"><span data-stu-id="83aab-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="83aab-103">対象プロセス内の共通言語ランタイム (CLR: Common Language Runtime) パスからバージョン文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="83aab-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83aab-104">構文</span><span class="sxs-lookup"><span data-stu-id="83aab-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83aab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83aab-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="83aab-106">[in] 対象 CLR が読み込まれているプロセスの識別子。</span><span class="sxs-lookup"><span data-stu-id="83aab-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="83aab-107">[in] プロセスに読み込まれている対象 CLR の完全パスまたは相対パス。</span><span class="sxs-lookup"><span data-stu-id="83aab-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="83aab-108">[out] 対象 CLR のバージョン文字列を格納する戻りバッファー。</span><span class="sxs-lookup"><span data-stu-id="83aab-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="83aab-109">[in] `pBuffer` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="83aab-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="83aab-110">[out] `pBuffer` によって返されるバージョン文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="83aab-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83aab-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="83aab-111">Return Value</span></span>  
 <span data-ttu-id="83aab-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="83aab-112">S_OK</span></span>  
 <span data-ttu-id="83aab-113">対象 CLR のバージョン文字列が `pBuffer` に正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="83aab-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="83aab-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="83aab-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="83aab-115">`szModuleName` が null であるか、`pBuffer` または `cchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="83aab-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="83aab-116">`pBuffer` と `cchBuffer` は、両方が null であるか、両方が null 以外である必要があります。</span><span class="sxs-lookup"><span data-stu-id="83aab-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="83aab-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="83aab-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="83aab-118">`pdwLength` が `cchBuffer` より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="83aab-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="83aab-119">`pBuffer` と `cchBuffer` の両方に null を渡して、`pdwLength` を使用して必要なバッファー サイズを照会した場合に、このような結果になることが予期されます。</span><span class="sxs-lookup"><span data-stu-id="83aab-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="83aab-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="83aab-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="83aab-121">`szModuleName` に、対象プロセスの有効な CLR のパスが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="83aab-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="83aab-122">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="83aab-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="83aab-123">`pidDebuggee` が有効なプロセスを参照していません。または、その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="83aab-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83aab-124">コメント</span><span class="sxs-lookup"><span data-stu-id="83aab-124">Remarks</span></span>  
 <span data-ttu-id="83aab-125">この関数は、`pidDebuggee` が識別した CLR プロセスと、`szModuleName` で指定された文字列パスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="83aab-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="83aab-126">バージョン文字列は、`pBuffer` が指すバッファーに返されます。</span><span class="sxs-lookup"><span data-stu-id="83aab-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="83aab-127">この文字列は関数のユーザーには不透明です。つまり、バージョン文字列自体に特別な意味はありません。</span><span class="sxs-lookup"><span data-stu-id="83aab-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="83aab-128">この関数のコンテキストでのみ使用されていると、 [CreateDebuggingInterfaceFromVersion 関数](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)です。</span><span class="sxs-lookup"><span data-stu-id="83aab-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="83aab-129">この関数は、2 回呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="83aab-129">This function should be called twice.</span></span> <span data-ttu-id="83aab-130">1 回目の呼び出しでは、`pBuffer` と `cchBuffer` の両方に null を渡します。</span><span class="sxs-lookup"><span data-stu-id="83aab-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="83aab-131">これにより、`pBuffer` に必要なバッファーのサイズが `pdwLength` に返されます。</span><span class="sxs-lookup"><span data-stu-id="83aab-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="83aab-132">その後、2 回目の関数呼び出しを実行し、`pBuffer` にはバッファーを、`cchBuffer` にはバッファーのサイズを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="83aab-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83aab-133">必要条件</span><span class="sxs-lookup"><span data-stu-id="83aab-133">Requirements</span></span>  
 <span data-ttu-id="83aab-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83aab-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83aab-135">**ヘッダー:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="83aab-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="83aab-136">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="83aab-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="83aab-137">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="83aab-137">**.NET Framework Versions:** 3.5 SP1</span></span>
