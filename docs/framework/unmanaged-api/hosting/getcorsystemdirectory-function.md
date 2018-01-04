---
title: "GetCORSystemDirectory 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="92961-102">GetCORSystemDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="92961-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="92961-103">プロセスに読み込まれる共通言語ランタイム (CLR) のインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="92961-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="92961-104">完全修飾のインストール ディレクトリはたとえば、"c:\windows\microsoft.net\framework\v1.0.3705"です。</span><span class="sxs-lookup"><span data-stu-id="92961-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="92961-105">この関数は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="92961-105">This function is deprecated.</span></span> <span data-ttu-id="92961-106">によって置き換えられた、 [iclrruntimeinfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)で提供されるメソッド、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="92961-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92961-107">構文</span><span class="sxs-lookup"><span data-stu-id="92961-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="92961-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92961-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="92961-109">[out]ランタイムが、プロセスに読み込まれたランタイムのインストール ディレクトリの完全修飾名を表す文字列を返すにバッファーです。</span><span class="sxs-lookup"><span data-stu-id="92961-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="92961-110">ランタイムがプロセスにまだ読み込まれていない場合は、コンピューターにインストールされているランタイムの最新バージョンの適切なディレクトリ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="92961-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="92961-111">[in]サイズをバイト単位での`pbuffer`します。</span><span class="sxs-lookup"><span data-stu-id="92961-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="92961-112">[out]返される文字数`pbuffer`です。</span><span class="sxs-lookup"><span data-stu-id="92961-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92961-113">コメント</span><span class="sxs-lookup"><span data-stu-id="92961-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="92961-114">CLR の version 4 を実行しているプロセスでは、この関数は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="92961-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="92961-115">CLR の以前のバージョンがコンピューターにインストールされている場合、この関数は、そのバージョンのインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="92961-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92961-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="92961-116">Requirements</span></span>  
 <span data-ttu-id="92961-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="92961-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92961-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92961-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92961-119">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92961-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92961-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92961-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92961-121">参照</span><span class="sxs-lookup"><span data-stu-id="92961-121">See Also</span></span>  
 [<span data-ttu-id="92961-122">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="92961-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
