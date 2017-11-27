---
title: "CreateAssemblyNameObject 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyNameObject
helpviewer_keywords: CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8281c7944ff96110145a6f5c43a0a0e7da58fdcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="99bf8-102">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="99bf8-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="99bf8-103">インターフェイス ポインターを取得、 [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)を指定した名前を持つアセンブリの一意の id を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="99bf8-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99bf8-104">構文</span><span class="sxs-lookup"><span data-stu-id="99bf8-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99bf8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99bf8-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="99bf8-106">[out]返された`IAssemblyName`です。</span><span class="sxs-lookup"><span data-stu-id="99bf8-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="99bf8-107">[in]新しいを作成する対象のアセンブリの名前`IAssemblyName`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="99bf8-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="99bf8-108">[in]オブジェクトのコンス トラクターに渡すフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="99bf8-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="99bf8-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="99bf8-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="99bf8-110">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="99bf8-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bf8-111">要件</span><span class="sxs-lookup"><span data-stu-id="99bf8-111">Requirements</span></span>  
 <span data-ttu-id="99bf8-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99bf8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bf8-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="99bf8-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="99bf8-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="99bf8-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99bf8-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99bf8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bf8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="99bf8-116">See Also</span></span>  
 [<span data-ttu-id="99bf8-117">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99bf8-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="99bf8-118">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="99bf8-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
