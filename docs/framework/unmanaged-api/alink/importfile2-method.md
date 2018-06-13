---
title: ImportFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61bc7783823408164ae2b073e097a0e85e193be6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401243"
---
# <a name="importfile2-method"></a><span data-ttu-id="7a463-102">ImportFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="7a463-102">ImportFile2 Method</span></span>
<span data-ttu-id="7a463-103">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="7a463-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="7a463-104">同様に、このメソッドは[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)、いますが、インポートするファイルがディスクに存在しない場合でも動作します。</span><span class="sxs-lookup"><span data-stu-id="7a463-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a463-105">構文</span><span class="sxs-lookup"><span data-stu-id="7a463-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a463-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a463-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7a463-107">インポートするファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="7a463-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="7a463-108">アセンブリにリンクされていると、ファイルの名前を変更するために使用する省略可能な出力ファイル名です。</span><span class="sxs-lookup"><span data-stu-id="7a463-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="7a463-109">省略可能なスコープ[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7a463-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="7a463-110">TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a463-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="7a463-111">ファイルまたはアセンブリの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7a463-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="7a463-112">受信、 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7a463-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="7a463-113">ファイルがアセンブリではない場合は NULL です。</span><span class="sxs-lookup"><span data-stu-id="7a463-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="7a463-114">ファイルやインポートのスコープには、検出されたを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7a463-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a463-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a463-115">Return Value</span></span>  
 <span data-ttu-id="7a463-116">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="7a463-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a463-117">要件</span><span class="sxs-lookup"><span data-stu-id="7a463-117">Requirements</span></span>  
 <span data-ttu-id="7a463-118">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a463-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a463-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a463-119">See Also</span></span>  
 [<span data-ttu-id="7a463-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a463-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7a463-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a463-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7a463-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="7a463-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
