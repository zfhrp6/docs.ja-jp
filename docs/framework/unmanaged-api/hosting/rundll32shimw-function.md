---
title: "RunDll32ShimW 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RunDll32ShimW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: RunDll32ShimW
helpviewer_keywords: RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a046ed8d540b27bfb73a6e94f148d41f8ac7b264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="dab3e-102">RunDll32ShimW 関数</span><span class="sxs-lookup"><span data-stu-id="dab3e-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="dab3e-103">指定されたコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dab3e-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="dab3e-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="dab3e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab3e-105">構文</span><span class="sxs-lookup"><span data-stu-id="dab3e-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dab3e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dab3e-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="dab3e-107">[in]コマンドの出力が表示されますウィンドウへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="dab3e-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="dab3e-108">[in]コマンドが含まれたライブラリへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="dab3e-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="dab3e-109">[in]実行するコマンドを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="dab3e-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="dab3e-110">[in]出力ウィンドウの表示モードを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="dab3e-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab3e-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="dab3e-111">Requirements</span></span>  
 <span data-ttu-id="dab3e-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dab3e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab3e-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dab3e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dab3e-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dab3e-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dab3e-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab3e-116">参照</span><span class="sxs-lookup"><span data-stu-id="dab3e-116">See Also</span></span>  
 [<span data-ttu-id="dab3e-117">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="dab3e-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
