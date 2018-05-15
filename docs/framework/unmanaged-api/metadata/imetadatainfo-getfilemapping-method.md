---
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 562b6fcd015441ce5eb6b5f0ab7a4f361bb229c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="b390e-102">IMetaDataInfo::GetFileMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="b390e-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="b390e-103">メモリの領域、マップされたファイルとマッピングの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="b390e-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b390e-104">構文</span><span class="sxs-lookup"><span data-stu-id="b390e-104">Syntax</span></span>  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b390e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b390e-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="b390e-106">[out]マップされたファイルの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b390e-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b390e-107">[out]マップ領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b390e-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="b390e-108">場合`pdwMappingType`は`fmFlat`、これは、ファイルのサイズ。</span><span class="sxs-lookup"><span data-stu-id="b390e-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="b390e-109">[out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)マッピングの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="b390e-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="b390e-110">現在の実装の共通言語ランタイム (CLR) 常に返します`fmFlat`です。</span><span class="sxs-lookup"><span data-stu-id="b390e-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="b390e-111">その他の値は、将来の使用に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="b390e-111">Other values are reserved for future use.</span></span> <span data-ttu-id="b390e-112">ただし、その他の値は、将来のバージョンで有効にすることがありますか、サービス リリースために、常に、返される値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b390e-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b390e-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="b390e-113">Return Value</span></span>  
  
|<span data-ttu-id="b390e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b390e-114">HRESULT</span></span>|<span data-ttu-id="b390e-115">説明</span><span class="sxs-lookup"><span data-stu-id="b390e-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b390e-116">すべての出力が入力されます。</span><span class="sxs-lookup"><span data-stu-id="b390e-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b390e-117">引数の値として NULL が渡されました。</span><span class="sxs-lookup"><span data-stu-id="b390e-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="b390e-118">CLR 実装には、メモリ領域に関する情報を提供できません。</span><span class="sxs-lookup"><span data-stu-id="b390e-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="b390e-119">これは、次の理由が考えられます。</span><span class="sxs-lookup"><span data-stu-id="b390e-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="b390e-120">メタデータ スコープが開かれた、`ofWrite`または`ofCopyMemory`フラグ。</span><span class="sxs-lookup"><span data-stu-id="b390e-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="b390e-121">-なしのメタデータ スコープが開かれて、`ofReadOnly`フラグ。</span><span class="sxs-lookup"><span data-stu-id="b390e-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="b390e-122">- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)を開くには、ファイルのメタデータ部分だけにメソッドが使用されました。</span><span class="sxs-lookup"><span data-stu-id="b390e-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="b390e-123">-ファイルは、ポータブル実行可能 (PE) ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="b390e-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="b390e-124">**注:** CLR 実装に依存してこれらの条件とする可能性がありますが脆弱になる将来のバージョンの CLR です。</span><span class="sxs-lookup"><span data-stu-id="b390e-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b390e-125">コメント</span><span class="sxs-lookup"><span data-stu-id="b390e-125">Remarks</span></span>  
 <span data-ttu-id="b390e-126">メモリを`ppvData`へのポインターが有効ではだけの基になるメタデータ スコープが開かれています。</span><span class="sxs-lookup"><span data-stu-id="b390e-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="b390e-127">このメソッドを呼び出してメモリ、ディスク上のファイルのメタデータをマップするときに、作業をするために、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)を指定する必要があります、メソッド、`ofReadOnly`フラグとする必要がありますを指定しない、`ofWrite`または`ofCopyMemory`フラグ。</span><span class="sxs-lookup"><span data-stu-id="b390e-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="b390e-128">各スコープのファイル マッピングの種類の選択は、CLR の特定の実装に固有です。</span><span class="sxs-lookup"><span data-stu-id="b390e-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="b390e-129">ユーザーがこれを設定できません。</span><span class="sxs-lookup"><span data-stu-id="b390e-129">It cannot be set by the user.</span></span> <span data-ttu-id="b390e-130">現在の実装、CLR の常に返します`fmFlat`で`pdwMappingType`が変わることが将来のバージョンの CLR または将来の指定したバージョンのサービス リリースです。</span><span class="sxs-lookup"><span data-stu-id="b390e-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="b390e-131">返される値を常に確認する必要があります`pdwMappingType`のため、さまざまな種類はさまざまなレイアウト、およびオフセットします。</span><span class="sxs-lookup"><span data-stu-id="b390e-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="b390e-132">3 つのパラメーターのいずれかに NULL を渡すことはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b390e-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="b390e-133">このメソッドを返します`E_INVALIDARG`出力のいずれもがいっぱいになるとします。</span><span class="sxs-lookup"><span data-stu-id="b390e-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="b390e-134">マッピングの種類や領域のサイズを無視すると、プログラムが異常終了が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="b390e-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b390e-135">要件</span><span class="sxs-lookup"><span data-stu-id="b390e-135">Requirements</span></span>  
 <span data-ttu-id="b390e-136">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b390e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b390e-137">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b390e-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b390e-138">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b390e-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b390e-139">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b390e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b390e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b390e-140">See Also</span></span>  
 [<span data-ttu-id="b390e-141">IMetaDataInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b390e-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [<span data-ttu-id="b390e-142">CorFileMapping 列挙型</span><span class="sxs-lookup"><span data-stu-id="b390e-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
