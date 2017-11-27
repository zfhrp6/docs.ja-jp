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
ms.openlocfilehash: 802e9a7bd4e6caedd657a8e8cf0132d75b4cbc2e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="b6e7a-102">GetCORSystemDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="b6e7a-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="b6e7a-103">プロセスに読み込まれる共通言語ランタイム (CLR) のインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="b6e7a-104">完全修飾のインストール ディレクトリはたとえば、"c:\windows\microsoft.net\framework\v1.0.3705"です。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="b6e7a-105">この関数は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-105">This function is deprecated.</span></span> <span data-ttu-id="b6e7a-106">によって置き換えられた、 [iclrruntimeinfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)で提供されるメソッド、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e7a-107">構文</span><span class="sxs-lookup"><span data-stu-id="b6e7a-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6e7a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6e7a-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="b6e7a-109">[out]ランタイムが、プロセスに読み込まれたランタイムのインストール ディレクトリの完全修飾名を表す文字列を返すにバッファーです。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="b6e7a-110">ランタイムがプロセスにまだ読み込まれていない場合は、コンピューターにインストールされているランタイムの最新バージョンの適切なディレクトリ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b6e7a-111">[in]サイズをバイト単位での`pbuffer`します。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b6e7a-112">[out]返される文字数`pbuffer`です。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6e7a-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b6e7a-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b6e7a-114">CLR の version 4 を実行しているプロセスでは、この関数は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="b6e7a-115">CLR の以前のバージョンがコンピューターにインストールされている場合、この関数は、そのバージョンのインストール ディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6e7a-116">要件</span><span class="sxs-lookup"><span data-stu-id="b6e7a-116">Requirements</span></span>  
 <span data-ttu-id="b6e7a-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6e7a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e7a-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6e7a-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6e7a-119">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6e7a-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6e7a-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e7a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e7a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6e7a-121">See Also</span></span>  
 [<span data-ttu-id="b6e7a-122">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="b6e7a-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
