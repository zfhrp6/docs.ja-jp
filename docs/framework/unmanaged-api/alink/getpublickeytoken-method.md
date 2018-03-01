---
title: "GetPublicKeyToken メソッド"
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
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="69033-102">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="69033-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="69033-103">指定された keyfile またはキー コンテナーの公開キー トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="69033-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69033-104">構文</span><span class="sxs-lookup"><span data-stu-id="69033-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69033-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69033-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="69033-106">キーのファイル名。</span><span class="sxs-lookup"><span data-stu-id="69033-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="69033-107">キー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="69033-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="69033-108">キー トークンが格納されるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="69033-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="69033-109">(バイト単位) で示されたバッファーのサイズを指定`pvPublicKeyToken`です。</span><span class="sxs-lookup"><span data-stu-id="69033-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="69033-110">関数が戻るときに、実際の使用バイト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69033-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69033-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="69033-111">Return Value</span></span>  
 <span data-ttu-id="69033-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="69033-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69033-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="69033-113">Requirements</span></span>  
 <span data-ttu-id="69033-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="69033-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69033-115">参照</span><span class="sxs-lookup"><span data-stu-id="69033-115">See Also</span></span>  
 [<span data-ttu-id="69033-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69033-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="69033-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69033-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="69033-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="69033-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
