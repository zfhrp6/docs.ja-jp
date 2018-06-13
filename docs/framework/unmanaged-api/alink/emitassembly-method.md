---
title: EmitAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cd1c077a8f2a5fe3b2b46c2e1da2e92b5a797a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402058"
---
# <a name="emitassembly-method"></a><span data-ttu-id="5f1c5-102">EmitAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="5f1c5-102">EmitAssembly Method</span></span>
<span data-ttu-id="5f1c5-103">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-103">Creates the assembly.</span></span> <span data-ttu-id="5f1c5-104">アセンブリ ファイルを除く他のすべてのファイルが閉じられた後は、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="5f1c5-105">非バインド モジュールを生成するときに、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f1c5-106">構文</span><span class="sxs-lookup"><span data-stu-id="5f1c5-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f1c5-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f1c5-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5f1c5-108">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f1c5-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5f1c5-109">Return Value</span></span>  
 <span data-ttu-id="5f1c5-110">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f1c5-111">要件</span><span class="sxs-lookup"><span data-stu-id="5f1c5-111">Requirements</span></span>  
 <span data-ttu-id="5f1c5-112">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="5f1c5-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f1c5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f1c5-113">See Also</span></span>  
 [<span data-ttu-id="5f1c5-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f1c5-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5f1c5-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f1c5-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5f1c5-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="5f1c5-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
