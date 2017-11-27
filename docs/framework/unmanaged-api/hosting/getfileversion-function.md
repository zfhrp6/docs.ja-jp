---
title: "GetFileVersion 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetFileVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetFileVersion
helpviewer_keywords: GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654cda723db9910fb80d32bc08c393a44f04b586
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getfileversion-function"></a><span data-ttu-id="2c447-102">GetFileVersion 関数</span><span class="sxs-lookup"><span data-stu-id="2c447-102">GetFileVersion Function</span></span>
<span data-ttu-id="2c447-103">指定されたバッファーを使用して、指定されたファイルの共通言語ランタイム (CLR) バージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2c447-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="2c447-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="2c447-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c447-105">構文</span><span class="sxs-lookup"><span data-stu-id="2c447-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c447-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2c447-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="2c447-107">[in]調査するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="2c447-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2c447-108">[入力、出力].返されるバージョン情報に割り当てられたバッファー。</span><span class="sxs-lookup"><span data-stu-id="2c447-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2c447-109">[in]ワイド文字単位のサイズの`szBuffer`します。</span><span class="sxs-lookup"><span data-stu-id="2c447-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2c447-110">[out]サイズ (バイト単位)、返された`szBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="2c447-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c447-111">要件</span><span class="sxs-lookup"><span data-stu-id="2c447-111">Requirements</span></span>  
 <span data-ttu-id="2c447-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c447-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c447-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c447-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c447-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c447-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c447-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c447-115">See Also</span></span>  
 [<span data-ttu-id="2c447-116">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="2c447-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
