---
title: "LoadLibraryShim 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="35c0a-102">LoadLibraryShim 関数</span><span class="sxs-lookup"><span data-stu-id="35c0a-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="35c0a-103">指定したバージョンの .NET Framework 再頒布可能パッケージに含まれている DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="35c0a-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="35c0a-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="35c0a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="35c0a-105">使用して、 [iclrruntimeinfo::loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="35c0a-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c0a-106">構文</span><span class="sxs-lookup"><span data-stu-id="35c0a-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35c0a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35c0a-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="35c0a-108">[in].NET Framework ライブラリから読み込まれる DLL の名前を表す 0 で終わる文字列。</span><span class="sxs-lookup"><span data-stu-id="35c0a-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="35c0a-109">[in]読み込まれる DLL のバージョンを表す、0 で終わる文字列。</span><span class="sxs-lookup"><span data-stu-id="35c0a-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="35c0a-110">場合`szVersion`は null、読み込みはバージョン 4 未満である指定された DLL の最新バージョン用に選択したバージョンです。</span><span class="sxs-lookup"><span data-stu-id="35c0a-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="35c0a-111">つまり、同じかまたは version 4 より大きいすべてのバージョン パラメーターは無視されます`szVersion`が null で、バージョン 4 未満のバージョンがインストールされていない場合、DLL 読み込みに失敗するとします。</span><span class="sxs-lookup"><span data-stu-id="35c0a-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="35c0a-112">これはのインストールを行うことを確認するため、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]既存のアプリケーションまたはコンポーネントには影響しません。</span><span class="sxs-lookup"><span data-stu-id="35c0a-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="35c0a-113">エントリを参照して[インプロセス SxS と移行のクイック スタート](http://go.microsoft.com/fwlink/?LinkId=200329)CLR チームのブログでします。</span><span class="sxs-lookup"><span data-stu-id="35c0a-113">See the entry [In-Proc SxS and Migration Quick Start](http://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="35c0a-114">将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="35c0a-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="35c0a-115">[out]モジュールのハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="35c0a-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35c0a-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="35c0a-116">Return Value</span></span>  
 <span data-ttu-id="35c0a-117">このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="35c0a-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="35c0a-118">リターン コード</span><span class="sxs-lookup"><span data-stu-id="35c0a-118">Return code</span></span>|<span data-ttu-id="35c0a-119">説明</span><span class="sxs-lookup"><span data-stu-id="35c0a-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="35c0a-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="35c0a-120">S_OK</span></span>|<span data-ttu-id="35c0a-121">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="35c0a-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="35c0a-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="35c0a-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="35c0a-123">読み込み`szDllName`共通言語ランタイム (CLR)、および必要なバージョンの CLR を読み込めません。 読み込みが必要です。</span><span class="sxs-lookup"><span data-stu-id="35c0a-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35c0a-124">コメント</span><span class="sxs-lookup"><span data-stu-id="35c0a-124">Remarks</span></span>  
 <span data-ttu-id="35c0a-125">この関数は、.NET Framework 再頒布可能パッケージに含まれている Dll の読み込みに使用されます。</span><span class="sxs-lookup"><span data-stu-id="35c0a-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="35c0a-126">ユーザーが生成した Dll は読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="35c0a-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35c0a-127">以降、.NET Framework version 2.0 と、読み込まれる CLR Fusion.dll の読み込みとします。</span><span class="sxs-lookup"><span data-stu-id="35c0a-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="35c0a-128">Fusion.dll で関数が、ラッパーが、この実装は、ランタイムによって提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="35c0a-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35c0a-129">要件</span><span class="sxs-lookup"><span data-stu-id="35c0a-129">Requirements</span></span>  
 <span data-ttu-id="35c0a-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="35c0a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35c0a-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35c0a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35c0a-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c0a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c0a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="35c0a-133">See Also</span></span>  
 [<span data-ttu-id="35c0a-134">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="35c0a-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
