---
title: "LinkResource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1ff38bf0017cf400d8f35f0ddf265f8628c82d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="b6500-102">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="b6500-102">LinkResource Method</span></span>
<span data-ttu-id="b6500-103">リソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="b6500-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6500-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6500-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6500-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6500-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b6500-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="b6500-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="b6500-107">ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="b6500-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="b6500-108">省略可能な新しいファイル名です。</span><span class="sxs-lookup"><span data-stu-id="b6500-108">Optional new file name.</span></span> <span data-ttu-id="b6500-109">Null 以外の場合、 `pszFileName` pszNewLocation にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b6500-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="b6500-110">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="b6500-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b6500-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="b6500-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="b6500-112">このパラメーターを渡すことがあります[DefineManifestResource メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6500-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6500-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="b6500-113">Return Value</span></span>  
 <span data-ttu-id="b6500-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="b6500-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6500-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="b6500-115">Requirements</span></span>  
 <span data-ttu-id="b6500-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="b6500-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6500-117">参照</span><span class="sxs-lookup"><span data-stu-id="b6500-117">See Also</span></span>  
 [<span data-ttu-id="b6500-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6500-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b6500-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6500-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b6500-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="b6500-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
