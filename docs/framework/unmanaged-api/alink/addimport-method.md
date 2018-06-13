---
title: AddImport Method1
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fefc0240f6496a3e7bfb491e27a57e98cfea1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404067"
---
# <a name="addimport-method1"></a><span data-ttu-id="49d90-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="49d90-102">AddImport Method1</span></span>
<span data-ttu-id="49d90-103">アセンブリにインポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="49d90-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d90-104">構文</span><span class="sxs-lookup"><span data-stu-id="49d90-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49d90-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49d90-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="49d90-106">追加する対象のアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="49d90-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="49d90-107">一意の ID から取得[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)ファイルをインポートするのです。</span><span class="sxs-lookup"><span data-stu-id="49d90-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="49d90-108">COM + FileDef フラグなど`ffContainsNoMetaData`と`ffWriteable`です。</span><span class="sxs-lookup"><span data-stu-id="49d90-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="49d90-109">`dwFlags` 渡される[DefineFile メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="49d90-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="49d90-110">トークンへのポインターは、結果のファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="49d90-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49d90-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="49d90-111">Return Value</span></span>  
 <span data-ttu-id="49d90-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="49d90-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d90-113">要件</span><span class="sxs-lookup"><span data-stu-id="49d90-113">Requirements</span></span>  
 <span data-ttu-id="49d90-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="49d90-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d90-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="49d90-115">See Also</span></span>  
 [<span data-ttu-id="49d90-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49d90-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="49d90-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49d90-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="49d90-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="49d90-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
