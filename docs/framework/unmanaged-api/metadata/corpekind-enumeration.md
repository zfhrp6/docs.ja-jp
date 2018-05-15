---
title: CorPEKind 列挙型
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="d4d58-102">CorPEKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="d4d58-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="d4d58-103">呼び出しから返されるよう、ポータブル実行可能 (PE) ファイルを記述する値を含む[imetadataimport 2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4d58-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d58-104">構文</span><span class="sxs-lookup"><span data-stu-id="d4d58-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="d4d58-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d4d58-105">Members</span></span>  
  
|<span data-ttu-id="d4d58-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d4d58-106">Member</span></span>|<span data-ttu-id="d4d58-107">説明</span><span class="sxs-lookup"><span data-stu-id="d4d58-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="d4d58-108">PE ファイルではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="d4d58-109">この PE ファイルには、マネージ コードだけが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="d4d58-110">この PE ファイルが Win32 呼び出しを行うことを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="d4d58-111">この PE ファイルが 64 ビット プラットフォームで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="d4d58-112">この PE ファイルがネイティブ コードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="d4d58-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="d4d58-113">pe32BitPreferred</span></span>|<span data-ttu-id="d4d58-114">この PE ファイルがプラットフォームに依存しない、優先的に 32 ビット環境で読み込まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4d58-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d58-115">コメント</span><span class="sxs-lookup"><span data-stu-id="d4d58-115">Remarks</span></span>  
 <span data-ttu-id="d4d58-116">これらの値は、ビットごとの組み合わせで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4d58-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d58-117">要件</span><span class="sxs-lookup"><span data-stu-id="d4d58-117">Requirements</span></span>  
 <span data-ttu-id="d4d58-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4d58-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d58-119">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d4d58-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d4d58-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d58-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4d58-121">See Also</span></span>  
 [<span data-ttu-id="d4d58-122">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="d4d58-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
