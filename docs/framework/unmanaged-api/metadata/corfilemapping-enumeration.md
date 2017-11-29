---
title: "CorFileMapping 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileMapping
helpviewer_keywords: CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6736f154ef6b03c0bfe34d16a419955324316273
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="60c98-102">CorFileMapping 列挙体</span><span class="sxs-lookup"><span data-stu-id="60c98-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="60c98-103">呼び出しから返されるファイル マッピングの種類を記述する値が含まれています、 [imetadatainfo::getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="60c98-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60c98-104">構文</span><span class="sxs-lookup"><span data-stu-id="60c98-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="60c98-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="60c98-105">Members</span></span>  
  
|<span data-ttu-id="60c98-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="60c98-106">Member</span></span>|<span data-ttu-id="60c98-107">説明</span><span class="sxs-lookup"><span data-stu-id="60c98-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="60c98-108">ファイルは、データ ファイルとしてマップされます。</span><span class="sxs-lookup"><span data-stu-id="60c98-108">The file is mapped as a data file.</span></span> <span data-ttu-id="60c98-109">つまり、`SEC_IMAGE`フラグは、Microsoft Win32 に渡されなかった`CreateFileMapping`関数。</span><span class="sxs-lookup"><span data-stu-id="60c98-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="60c98-110">いずれかを使用して実行のため、ファイルがマップされている、`LoadLibrary`関数または`CreateFileMapping`で機能、`SEC_IMAGE`フラグ。</span><span class="sxs-lookup"><span data-stu-id="60c98-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60c98-111">要件</span><span class="sxs-lookup"><span data-stu-id="60c98-111">Requirements</span></span>  
 <span data-ttu-id="60c98-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="60c98-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c98-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="60c98-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="60c98-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c98-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="60c98-115">See Also</span></span>  
 [<span data-ttu-id="60c98-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="60c98-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="60c98-117">GetFileMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="60c98-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
