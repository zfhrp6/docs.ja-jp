---
title: ImportFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54b0a02af7f22e775e3f9567de79664c9805b4e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400651"
---
# <a name="importfile-method"></a><span data-ttu-id="03aa5-102">ImportFile メソッド</span><span class="sxs-lookup"><span data-stu-id="03aa5-102">ImportFile Method</span></span>
<span data-ttu-id="03aa5-103">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="03aa5-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03aa5-104">構文</span><span class="sxs-lookup"><span data-stu-id="03aa5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="03aa5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03aa5-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="03aa5-106">インポートするファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="03aa5-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="03aa5-107">アセンブリにリンクされていると、ファイルの名前を変更するために使用する省略可能な出力ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="03aa5-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="03aa5-108">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03aa5-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="03aa5-109">トークンの一意のファイル ID を格納する場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="03aa5-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="03aa5-110">ファイルには、アセンブリまたはファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="03aa5-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="03aa5-111">ポインターを受け取る[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="03aa5-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="03aa5-112">ファイルがアセンブリではない場合、NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="03aa5-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="03aa5-113">ファイルまたはインポートされているスコープの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="03aa5-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03aa5-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="03aa5-114">Return Value</span></span>  
 <span data-ttu-id="03aa5-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="03aa5-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03aa5-116">要件</span><span class="sxs-lookup"><span data-stu-id="03aa5-116">Requirements</span></span>  
 <span data-ttu-id="03aa5-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="03aa5-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03aa5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="03aa5-118">See Also</span></span>  
 [<span data-ttu-id="03aa5-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03aa5-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="03aa5-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03aa5-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="03aa5-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="03aa5-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
