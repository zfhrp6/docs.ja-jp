---
title: LinkResource メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f75ebc3a40bddbaf2347b9ef559139888f83900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401109"
---
# <a name="linkresource-method"></a><span data-ttu-id="344ea-102">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="344ea-102">LinkResource Method</span></span>
<span data-ttu-id="344ea-103">リソースにリンクしています。</span><span class="sxs-lookup"><span data-stu-id="344ea-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="344ea-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="344ea-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="344ea-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="344ea-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="344ea-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="344ea-107">ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="344ea-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="344ea-108">省略可能な新しいファイル名です。</span><span class="sxs-lookup"><span data-stu-id="344ea-108">Optional new file name.</span></span> <span data-ttu-id="344ea-109">Null 以外の場合、 `pszFileName` pszNewLocation にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="344ea-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="344ea-110">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="344ea-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="344ea-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="344ea-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="344ea-112">このパラメーターを渡すことがあります[DefineManifestResource メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="344ea-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="344ea-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="344ea-113">Return Value</span></span>  
 <span data-ttu-id="344ea-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="344ea-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344ea-115">要件</span><span class="sxs-lookup"><span data-stu-id="344ea-115">Requirements</span></span>  
 <span data-ttu-id="344ea-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="344ea-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344ea-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="344ea-117">See Also</span></span>  
 [<span data-ttu-id="344ea-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="344ea-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="344ea-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="344ea-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="344ea-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="344ea-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
