---
title: "ImportFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d4f93336fe19210086c39b8db6d167b3caa222
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="importfile-method"></a><span data-ttu-id="8056f-102">ImportFile メソッド</span><span class="sxs-lookup"><span data-stu-id="8056f-102">ImportFile Method</span></span>
<span data-ttu-id="8056f-103">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="8056f-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8056f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8056f-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8056f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8056f-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8056f-106">インポートするファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="8056f-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="8056f-107">アセンブリにリンクされていると、ファイルの名前を変更するために使用する省略可能な出力ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="8056f-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="8056f-108">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8056f-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="8056f-109">トークンの一意のファイル ID を格納する場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8056f-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="8056f-110">ファイルには、アセンブリまたはファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8056f-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="8056f-111">ポインターを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="8056f-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="8056f-112">ファイルがアセンブリではない場合、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8056f-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="8056f-113">ファイルまたはインポートされているスコープの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8056f-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8056f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="8056f-114">Return Value</span></span>  
 <span data-ttu-id="8056f-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="8056f-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8056f-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="8056f-116">Requirements</span></span>  
 <span data-ttu-id="8056f-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="8056f-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8056f-118">参照</span><span class="sxs-lookup"><span data-stu-id="8056f-118">See Also</span></span>  
 [<span data-ttu-id="8056f-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8056f-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8056f-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8056f-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8056f-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="8056f-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
