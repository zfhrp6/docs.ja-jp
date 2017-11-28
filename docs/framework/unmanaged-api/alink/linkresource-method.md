---
title: "LinkResource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="38ad0-102">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="38ad0-102">LinkResource Method</span></span>
<span data-ttu-id="38ad0-103">リソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="38ad0-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38ad0-104">構文</span><span class="sxs-lookup"><span data-stu-id="38ad0-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38ad0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38ad0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="38ad0-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="38ad0-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="38ad0-107">ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="38ad0-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="38ad0-108">省略可能な新しいファイル名です。</span><span class="sxs-lookup"><span data-stu-id="38ad0-108">Optional new file name.</span></span> <span data-ttu-id="38ad0-109">Null 以外の場合、 `pszFileName` pszNewLocation にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="38ad0-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="38ad0-110">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="38ad0-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="38ad0-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="38ad0-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="38ad0-112">このパラメーターを渡すことがあります[DefineManifestResource メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="38ad0-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38ad0-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="38ad0-113">Return Value</span></span>  
 <span data-ttu-id="38ad0-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="38ad0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38ad0-115">要件</span><span class="sxs-lookup"><span data-stu-id="38ad0-115">Requirements</span></span>  
 <span data-ttu-id="38ad0-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="38ad0-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ad0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="38ad0-117">See Also</span></span>  
 [<span data-ttu-id="38ad0-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38ad0-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="38ad0-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38ad0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="38ad0-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="38ad0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
