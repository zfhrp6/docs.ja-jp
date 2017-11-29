---
title: "ImportFileEx2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2416a630f9bd763d4d4d31170cc606b160bb854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex2-method"></a><span data-ttu-id="2e578-102">ImportFileEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2e578-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="2e578-103">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="2e578-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="2e578-104">同様に、このメソッドは[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)、いますが、インポートするファイルがディスクに存在しない場合でも動作します。</span><span class="sxs-lookup"><span data-stu-id="2e578-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e578-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e578-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e578-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e578-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="2e578-107">インポートするファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="2e578-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="2e578-108">ターゲット ファイルの省略可能な名前です。</span><span class="sxs-lookup"><span data-stu-id="2e578-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="2e578-109">省略可能なインポート スコープ[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2e578-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="2e578-110">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e578-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="2e578-111">に沿ってに渡されるフラグ[OpenScope メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e578-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="2e578-112">アセンブリまたはファイルの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2e578-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="2e578-113">インポートのアセンブリのスコープを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2e578-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="2e578-114">ファイルがアセンブリではない場合、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2e578-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="2e578-115">ファイルまたはインポートされたスコープの数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2e578-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e578-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e578-116">Return Value</span></span>  
 <span data-ttu-id="2e578-117">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2e578-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e578-118">要件</span><span class="sxs-lookup"><span data-stu-id="2e578-118">Requirements</span></span>  
 <span data-ttu-id="2e578-119">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2e578-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e578-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e578-120">See Also</span></span>  
 [<span data-ttu-id="2e578-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e578-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2e578-122">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e578-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2e578-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="2e578-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
