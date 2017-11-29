---
title: "IMetaDataImport2::GetPEKind メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fc963f38a845db67bb5b5d377ecabf9a40c359f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="0a785-102">IMetaDataImport2::GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="0a785-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="0a785-103">取得ポータブル実行可能 (PE) 内のコードの種類を識別する値ファイルで、通常、DLL または EXE ファイルで現在のメタデータ スコープで定義されています。</span><span class="sxs-lookup"><span data-stu-id="0a785-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a785-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a785-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a785-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a785-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="0a785-106">[out]値へのポインター、 [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) PE ファイルを表す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="0a785-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="0a785-107">[out]コンピューターのアーキテクチャを識別する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0a785-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="0a785-108">使用可能な値については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a785-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a785-109">コメント</span><span class="sxs-lookup"><span data-stu-id="0a785-109">Remarks</span></span>  
 <span data-ttu-id="0a785-110">によって参照される値、`pdwMachine`パラメーターは、次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0a785-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="0a785-111">値</span><span class="sxs-lookup"><span data-stu-id="0a785-111">Value</span></span>|<span data-ttu-id="0a785-112">コンピューターのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="0a785-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="0a785-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="0a785-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="0a785-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="0a785-114">0x014C</span></span>|<span data-ttu-id="0a785-115">x86</span><span class="sxs-lookup"><span data-stu-id="0a785-115">x86</span></span>|  
|<span data-ttu-id="0a785-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="0a785-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="0a785-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="0a785-117">0x0200</span></span>|<span data-ttu-id="0a785-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="0a785-118">Intel IPF</span></span>|  
|<span data-ttu-id="0a785-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="0a785-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="0a785-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="0a785-120">0x8664</span></span>|<span data-ttu-id="0a785-121">x64</span><span class="sxs-lookup"><span data-stu-id="0a785-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a785-122">要件</span><span class="sxs-lookup"><span data-stu-id="0a785-122">Requirements</span></span>  
 <span data-ttu-id="0a785-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a785-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a785-124">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a785-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a785-125">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0a785-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a785-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a785-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a785-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a785-127">See Also</span></span>  
 [<span data-ttu-id="0a785-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a785-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="0a785-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a785-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0a785-130">CorPEKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="0a785-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
