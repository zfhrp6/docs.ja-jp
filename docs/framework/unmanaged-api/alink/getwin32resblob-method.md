---
title: "GetWin32ResBlob メソッド"
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
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="4dcff-102">GetWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="4dcff-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="4dcff-103">Win32 リソースの blob を取得します。</span><span class="sxs-lookup"><span data-stu-id="4dcff-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="4dcff-104">アセンブリ オプションを設定した後、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4dcff-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcff-105">構文</span><span class="sxs-lookup"><span data-stu-id="4dcff-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dcff-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4dcff-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4dcff-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="4dcff-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4dcff-108">Win32 バージョン リソースを構築するときに使用されるファイル名の取得に使用されるファイルのトークン</span><span class="sxs-lookup"><span data-stu-id="4dcff-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="4dcff-109">ファイルが DLL の場合、false は EXE の場合は TRUE です。</span><span class="sxs-lookup"><span data-stu-id="4dcff-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="4dcff-110">リソースの blob に挿入する省略可能なアイコンです。</span><span class="sxs-lookup"><span data-stu-id="4dcff-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="4dcff-111">リソースの blob を受信します。</span><span class="sxs-lookup"><span data-stu-id="4dcff-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="4dcff-112">Blob のサイズを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4dcff-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dcff-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="4dcff-113">Return Value</span></span>  
 <span data-ttu-id="4dcff-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="4dcff-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcff-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="4dcff-115">Requirements</span></span>  
 <span data-ttu-id="4dcff-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="4dcff-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcff-117">参照</span><span class="sxs-lookup"><span data-stu-id="4dcff-117">See Also</span></span>  
 [<span data-ttu-id="4dcff-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dcff-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4dcff-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dcff-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4dcff-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="4dcff-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
