---
title: GetFileDef メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b772ae37baed44b90e4f5420e0f7724201a56abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401812"
---
# <a name="getfiledef-method"></a><span data-ttu-id="9e55c-102">GetFileDef メソッド</span><span class="sxs-lookup"><span data-stu-id="9e55c-102">GetFileDef Method</span></span>
<span data-ttu-id="9e55c-103">(ALink によって割り当てられたトークン) ではなくメタデータで使用される実際の FileDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="9e55c-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e55c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e55c-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e55c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9e55c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9e55c-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="9e55c-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="9e55c-107">追加されたファイルのトークン AddFile メソッドまたは AddImport メソッドから取得します。</span><span class="sxs-lookup"><span data-stu-id="9e55c-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="9e55c-108">FileDef トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9e55c-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e55c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9e55c-109">Return Value</span></span>  
 <span data-ttu-id="9e55c-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="9e55c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e55c-111">要件</span><span class="sxs-lookup"><span data-stu-id="9e55c-111">Requirements</span></span>  
 <span data-ttu-id="9e55c-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="9e55c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e55c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e55c-113">See Also</span></span>  
 [<span data-ttu-id="9e55c-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e55c-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9e55c-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e55c-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9e55c-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="9e55c-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
