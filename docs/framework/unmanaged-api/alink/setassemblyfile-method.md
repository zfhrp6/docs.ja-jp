---
title: "SetAssemblyFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyFile
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile
helpviewer_keywords: SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0be76e93ab41860f7f3416d0baffe3e4daf84c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="e43a3-102">SetAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="e43a3-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="e43a3-103">作成するアセンブリの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e43a3-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="e43a3-104">非バインド モジュールを生成するときに使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e43a3-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e43a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="e43a3-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e43a3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e43a3-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e43a3-107">マニフェスト ファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="e43a3-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e43a3-108">ポインター [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="e43a3-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="e43a3-109">定義されているフラグ[AssemblyFlags 列挙体](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="e43a3-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="e43a3-110">結果として得られるアセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e43a3-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e43a3-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="e43a3-111">Return Value</span></span>  
 <span data-ttu-id="e43a3-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="e43a3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e43a3-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="e43a3-113">Requirements</span></span>  
 <span data-ttu-id="e43a3-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="e43a3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e43a3-115">参照</span><span class="sxs-lookup"><span data-stu-id="e43a3-115">See Also</span></span>  
 [<span data-ttu-id="e43a3-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e43a3-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e43a3-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e43a3-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e43a3-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="e43a3-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
