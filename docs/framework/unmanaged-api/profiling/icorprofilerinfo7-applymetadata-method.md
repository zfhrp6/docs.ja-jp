---
title: "ICorProfilerInfo7::ApplyMetaData メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorProfilerInfo7.ApplyMetaData
api_location: mscorwks.dll
api_type: COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3724555df58392e5ab59ccb4f52dd2de860b8d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="8433e-102">ICorProfilerInfo7::ApplyMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="8433e-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="8433e-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="8433e-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8433e-104">新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドを指定されたモジュール。</span><span class="sxs-lookup"><span data-stu-id="8433e-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8433e-105">構文</span><span class="sxs-lookup"><span data-stu-id="8433e-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8433e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8433e-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8433e-107">[in]変更されたメタデータを持つモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="8433e-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8433e-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8433e-108">Remarks</span></span>  
 <span data-ttu-id="8433e-109">後のメタデータの変更が加えられた場合、 [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックを新しいメタデータを使用する前にこのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8433e-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="8433e-110">`ApplyMetaData`次の種類のメタデータを追加するにのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8433e-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="8433e-111">`AssemblyRef`呼び出して作成した、レコード、 [imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="8433e-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="8433e-112">メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="8433e-112">method.</span></span>  
  
-   <span data-ttu-id="8433e-113">`TypeRef`呼び出して作成した、レコード、 [imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8433e-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="8433e-114">`TypeSpec`呼び出して作成した、レコード、 [imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8433e-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="8433e-115">`MemberRef`呼び出して作成した、レコード、 [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8433e-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="8433e-116">`MemberSpec`呼び出して作成した、レコード、 [imetadataemit 2::definemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8433e-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="8433e-117">`UserString`呼び出して作成した、レコード、 [imetadataemit::defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8433e-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8433e-118">要件</span><span class="sxs-lookup"><span data-stu-id="8433e-118">Requirements</span></span>  
 <span data-ttu-id="8433e-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8433e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8433e-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8433e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8433e-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8433e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8433e-122">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8433e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8433e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8433e-123">See Also</span></span>  
 [<span data-ttu-id="8433e-124">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8433e-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
