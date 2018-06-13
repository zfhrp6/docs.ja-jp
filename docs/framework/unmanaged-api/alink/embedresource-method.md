---
title: EmbedResource メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405399"
---
# <a name="embedresource-method"></a><span data-ttu-id="2dcdb-102">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="2dcdb-102">EmbedResource Method</span></span>
<span data-ttu-id="2dcdb-103">埋め込みリソースを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-103">Declares an embedded resource.</span></span> <span data-ttu-id="2dcdb-104">このメソッドには、リソースが実際には埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dcdb-105">構文</span><span class="sxs-lookup"><span data-stu-id="2dcdb-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2dcdb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2dcdb-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2dcdb-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2dcdb-108">ファイルのリソースを格納するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="2dcdb-109">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="2dcdb-110">RVA からのリソースのオフセット。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2dcdb-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="2dcdb-112">これらのフラグを渡すこと[DefineExportedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2dcdb-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="2dcdb-113">Return Value</span></span>  
 <span data-ttu-id="2dcdb-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dcdb-115">要件</span><span class="sxs-lookup"><span data-stu-id="2dcdb-115">Requirements</span></span>  
 <span data-ttu-id="2dcdb-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2dcdb-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcdb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dcdb-117">See Also</span></span>  
 [<span data-ttu-id="2dcdb-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dcdb-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2dcdb-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2dcdb-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2dcdb-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="2dcdb-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
