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
ms.openlocfilehash: 71a7bc1ba9f23f1c581ca3528752e04003d9857c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="d2d9f-102">ImportFileEx メソッド</span><span class="sxs-lookup"><span data-stu-id="d2d9f-102">ImportFileEx Method</span></span>
<span data-ttu-id="d2d9f-103">インポートには、アセンブリまたは非バインド モジュールが示されます。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d9f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2d9f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d2d9f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2d9f-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d2d9f-106">インポート元のファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="d2d9f-107">ターゲット ファイルの省略可能な名前です。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="d2d9f-108">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="d2d9f-109">に沿ってに渡されるフラグ[OpenScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="d2d9f-110">インポートされるファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="d2d9f-111">インポートのアセンブリのスコープを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="d2d9f-112">ファイルがアセンブリではない場合、NULL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="d2d9f-113">インポートされたファイルまたはスコープの数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2d9f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="d2d9f-114">Return Value</span></span>  
 <span data-ttu-id="d2d9f-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d9f-116">要件</span><span class="sxs-lookup"><span data-stu-id="d2d9f-116">Requirements</span></span>  
 <span data-ttu-id="d2d9f-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2d9f-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d9f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2d9f-118">See Also</span></span>  
 [<span data-ttu-id="d2d9f-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2d9f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d2d9f-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2d9f-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d2d9f-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="d2d9f-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
