---
title: RunDll32ShimW 関数
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18247a947449ea5fd19f1882031b598086332742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441741"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="62d08-102">RunDll32ShimW 関数</span><span class="sxs-lookup"><span data-stu-id="62d08-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="62d08-103">指定されたコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="62d08-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="62d08-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="62d08-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d08-105">構文</span><span class="sxs-lookup"><span data-stu-id="62d08-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62d08-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62d08-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="62d08-107">[in]コマンドの出力が表示されます ウィンドウへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="62d08-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="62d08-108">[in]コマンドが含まれたライブラリへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="62d08-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="62d08-109">[in]実行するコマンドを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="62d08-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="62d08-110">[in]出力ウィンドウの表示モードを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="62d08-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d08-111">要件</span><span class="sxs-lookup"><span data-stu-id="62d08-111">Requirements</span></span>  
 <span data-ttu-id="62d08-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62d08-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d08-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62d08-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62d08-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62d08-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62d08-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d08-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="62d08-116">See Also</span></span>  
 <span data-ttu-id="62d08-117">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="62d08-117">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
