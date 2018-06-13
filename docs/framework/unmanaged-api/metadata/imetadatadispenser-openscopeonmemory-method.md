---
title: IMetaDataDispenser::OpenScopeOnMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f184c04db384c2b9bdbce2d8ae6919c05a2ab425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448896"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="a446e-102">IMetaDataDispenser::OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="a446e-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="a446e-103">既存のメタデータを含んでいるメモリの領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="a446e-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="a446e-104">つまり、このメソッドは、既存のデータはメタデータとして扱われますメモリの指定された領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="a446e-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a446e-105">構文</span><span class="sxs-lookup"><span data-stu-id="a446e-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a446e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a446e-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="a446e-107">[in]メモリ領域の開始アドレスを指定するポインター。</span><span class="sxs-lookup"><span data-stu-id="a446e-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="a446e-108">[in]\(バイト単位) のメモリ領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a446e-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="a446e-109">[in]値、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)開くのためのモード (読み取り、書き込み、およびなど) を指定する列挙体です。</span><span class="sxs-lookup"><span data-stu-id="a446e-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="a446e-110">[in]返される; 必要なメタデータ インターフェイスの IID呼び出し元は (読み取り) をインポートまたは (書き込み) メタデータを生成するインターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a446e-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="a446e-111">値`riid`"import"や「生成」のインターフェイスのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a446e-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="a446e-112">有効な値は IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。</span><span class="sxs-lookup"><span data-stu-id="a446e-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="a446e-113">[out]返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a446e-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a446e-114">コメント</span><span class="sxs-lookup"><span data-stu-id="a446e-114">Remarks</span></span>  
 <span data-ttu-id="a446e-115">「インポート」インターフェイスの 1 つからメソッドを使用または「生成」インターフェイスのいずれかからメソッドを使用する追加のメタデータのメモリ内のコピーを照会できます。</span><span class="sxs-lookup"><span data-stu-id="a446e-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="a446e-116">`OpenScopeOnMemory`メソッドがに似ていますが、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッド、関心のあるメタデータは、ディスク上のファイルではなく、メモリ内に既に存在する点を除いて。</span><span class="sxs-lookup"><span data-stu-id="a446e-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="a446e-117">メモリの対象領域に共通言語ランタイム (CLR) メタデータが含まれていない場合、`OpenScopeOnMemory`メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="a446e-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a446e-118">要件</span><span class="sxs-lookup"><span data-stu-id="a446e-118">Requirements</span></span>  
 <span data-ttu-id="a446e-119">**Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a446e-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a446e-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a446e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a446e-121">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="a446e-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a446e-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a446e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a446e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a446e-123">See Also</span></span>  
 [<span data-ttu-id="a446e-124">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="a446e-125">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="a446e-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="a446e-127">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="a446e-128">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a446e-129">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="a446e-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a446e-131">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a446e-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
