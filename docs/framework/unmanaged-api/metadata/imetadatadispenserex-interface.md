---
title: "IMetaDataDispenserEx インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5ecb4e94c0deed3ed62b2d2eb8b0309ca092abf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="87e35-102">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e35-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="87e35-103">拡張、 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)メタデータ Api が現在のメタデータ スコープにどのように動作する方法を制御する機能を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="87e35-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87e35-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-104">Methods</span></span>  
  
|<span data-ttu-id="87e35-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-105">Method</span></span>|<span data-ttu-id="87e35-106">説明</span><span class="sxs-lookup"><span data-stu-id="87e35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87e35-107">FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="87e35-108">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="87e35-108">This method is not implemented.</span></span> <span data-ttu-id="87e35-109">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="87e35-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="87e35-110">FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="87e35-111">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="87e35-111">This method is not implemented.</span></span> <span data-ttu-id="87e35-112">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="87e35-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="87e35-113">GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="87e35-114">現在の共通言語ランタイム (CLR) を保持するディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="87e35-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="87e35-115">このメソッドは、アウト プロセスのデバッガーで使用するためだけサポートします。</span><span class="sxs-lookup"><span data-stu-id="87e35-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="87e35-116">別のコンポーネントから呼び出す場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="87e35-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="87e35-117">GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="87e35-118">現在のメタデータ スコープに指定されたオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="87e35-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="87e35-119">オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="87e35-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="87e35-120">OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="87e35-121">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="87e35-121">This method is not implemented.</span></span> <span data-ttu-id="87e35-122">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="87e35-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="87e35-123">SetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="87e35-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="87e35-124">現在のメタデータ スコープに指定された値を指定されたオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="87e35-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="87e35-125">オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="87e35-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87e35-126">要件</span><span class="sxs-lookup"><span data-stu-id="87e35-126">Requirements</span></span>  
 <span data-ttu-id="87e35-127">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87e35-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e35-128">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="87e35-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87e35-129">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="87e35-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87e35-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e35-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e35-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="87e35-131">See Also</span></span>  
 [<span data-ttu-id="87e35-132">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e35-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="87e35-133">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e35-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="87e35-134">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e35-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="87e35-135">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e35-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
