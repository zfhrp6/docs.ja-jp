---
title: ImportTypes メソッド
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321038a148c27086ca499e2f448eb50cb93525ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405513"
---
# <a name="importtypes-method"></a><span data-ttu-id="7051a-102">ImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="7051a-102">ImportTypes Method</span></span>
<span data-ttu-id="7051a-103">使用してインポートする各スコープの種類のインポートを開始[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="7051a-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7051a-104">構文</span><span class="sxs-lookup"><span data-stu-id="7051a-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7051a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7051a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7051a-106">インポート先のアセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="7051a-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7051a-107">インポートするファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="7051a-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="7051a-108">インポートする 0 から始まるスコープです。</span><span class="sxs-lookup"><span data-stu-id="7051a-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="7051a-109">このスコープの種類の列挙子のハンドルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7051a-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="7051a-110">必要に応じて受信[IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="7051a-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="7051a-111">オプションで指定されたスコープ内で型の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7051a-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7051a-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="7051a-112">Return Value</span></span>  
 <span data-ttu-id="7051a-113">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="7051a-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7051a-114">要件</span><span class="sxs-lookup"><span data-stu-id="7051a-114">Requirements</span></span>  
 <span data-ttu-id="7051a-115">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="7051a-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7051a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7051a-116">See Also</span></span>  
 [<span data-ttu-id="7051a-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7051a-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7051a-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7051a-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7051a-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="7051a-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
