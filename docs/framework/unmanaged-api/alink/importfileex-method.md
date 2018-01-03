---
title: "ImportFileEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc2af9db27c5194a1bdcef875b8db8d458d0edfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="79efe-102">ImportFileEx メソッド</span><span class="sxs-lookup"><span data-stu-id="79efe-102">ImportFileEx Method</span></span>
<span data-ttu-id="79efe-103">インポートには、アセンブリまたは非バインド モジュールが示されます。</span><span class="sxs-lookup"><span data-stu-id="79efe-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79efe-104">構文</span><span class="sxs-lookup"><span data-stu-id="79efe-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79efe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79efe-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="79efe-106">インポート元のファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="79efe-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="79efe-107">ターゲット ファイルの省略可能な名前です。</span><span class="sxs-lookup"><span data-stu-id="79efe-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="79efe-108">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79efe-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="79efe-109">に沿ってに渡されるフラグ[OpenScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="79efe-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="79efe-110">インポートされるファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="79efe-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="79efe-111">インポートのアセンブリのスコープを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="79efe-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="79efe-112">ファイルがアセンブリではない場合、NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="79efe-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="79efe-113">インポートされたファイルまたはスコープの数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="79efe-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79efe-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="79efe-114">Return Value</span></span>  
 <span data-ttu-id="79efe-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="79efe-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79efe-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="79efe-116">Requirements</span></span>  
 <span data-ttu-id="79efe-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="79efe-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79efe-118">参照</span><span class="sxs-lookup"><span data-stu-id="79efe-118">See Also</span></span>  
 [<span data-ttu-id="79efe-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79efe-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="79efe-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79efe-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="79efe-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="79efe-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
