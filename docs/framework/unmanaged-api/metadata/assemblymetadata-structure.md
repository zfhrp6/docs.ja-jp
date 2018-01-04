---
title: "ASSEMBLYMETADATA 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 819510c14bd67e7fcc739a19ea945f16b2a66c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="e6c1f-102">ASSEMBLYMETADATA 構造体</span><span class="sxs-lookup"><span data-stu-id="e6c1f-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="e6c1f-103">そのバージョンと、ロケール、プロセッサ、およびオペレーティング システムのサポートのレベルを含む、参照先アセンブリに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c1f-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6c1f-104">Syntax</span></span>  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="e6c1f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e6c1f-105">Members</span></span>  
  
|<span data-ttu-id="e6c1f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e6c1f-106">Member</span></span>|<span data-ttu-id="e6c1f-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6c1f-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="e6c1f-108">参照されたアセンブリのメジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="e6c1f-109">この値を 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-109">This value cannot be zero.</span></span> <span data-ttu-id="e6c1f-110">場合のすべてのビット`usMajorVersion`が設定された場合、メジャー バージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="e6c1f-111">参照されたアセンブリのマイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="e6c1f-112">この値を 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-112">This value cannot be zero.</span></span> <span data-ttu-id="e6c1f-113">場合のすべてのビット`usMinorVersion`は設定されて、マイナー バージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="e6c1f-114">参照されたアセンブリのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="e6c1f-115">この値を 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-115">This value cannot be zero.</span></span> <span data-ttu-id="e6c1f-116">場合のすべてのビット`usBuildNumber`が設定された場合、ビルド番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="e6c1f-117">参照されたアセンブリのリビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="e6c1f-118">この値を 0 にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-118">This value cannot be zero.</span></span> <span data-ttu-id="e6c1f-119">場合のすべてのビット`usRevisionNumber`は設定されて、リビジョン番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="e6c1f-120">参照されたアセンブリでサポートされているロケールを指定する、セミコロンで区切られた、RFC1766 仕様に準拠しているロケール名の一覧。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="e6c1f-121">Null 値には、ロケールに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-121">A null value indicates locale independence.</span></span> <span data-ttu-id="e6c1f-122">**注:** .NET Framework version 1.0 の 2 つ以上のロケールを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="e6c1f-123">ワイド文字単位のサイズ`szLocale`です。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="e6c1f-124">参照されたアセンブリでサポートされているプロセッサの種類について、Winnt.h で定義されている、識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="e6c1f-125">NULL 値では、プロセッサの独立性を示します。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="e6c1f-126">長さ、`rdwProcessor`配列。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="e6c1f-127">配列[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)参照されたアセンブリでサポートされているオペレーティング システムを指定するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="e6c1f-128">NULL 値には、オペレーティング システムに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="e6c1f-129">長さ、`rOS`配列。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6c1f-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="e6c1f-130">Requirements</span></span>  
 <span data-ttu-id="e6c1f-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6c1f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6c1f-132">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6c1f-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6c1f-133">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="e6c1f-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6c1f-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6c1f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c1f-135">参照</span><span class="sxs-lookup"><span data-stu-id="e6c1f-135">See Also</span></span>  
 [<span data-ttu-id="e6c1f-136">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="e6c1f-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="e6c1f-137">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6c1f-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="e6c1f-138">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="e6c1f-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
