---
title: SetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed553a3a8d54b5229a122e76b61e3e58d4af3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401967"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="ae4dc-102">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="ae4dc-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="ae4dc-103">アセンブリ レベルのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4dc-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae4dc-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae4dc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae4dc-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ae4dc-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ae4dc-107">プロパティを定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-107">File that defines the property.</span></span> <span data-ttu-id="ae4dc-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="ae4dc-109">変更するためのオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="ae4dc-110">オプションの新しい値。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae4dc-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae4dc-111">Return Value</span></span>  
 <span data-ttu-id="ae4dc-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4dc-113">要件</span><span class="sxs-lookup"><span data-stu-id="ae4dc-113">Requirements</span></span>  
 <span data-ttu-id="ae4dc-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae4dc-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4dc-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae4dc-115">See Also</span></span>  
 [<span data-ttu-id="ae4dc-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae4dc-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ae4dc-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae4dc-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ae4dc-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="ae4dc-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
