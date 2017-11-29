---
title: "GetPublicKeyToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f41c8088f095802cf35239afab279d6324adb55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="f9b47-102">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="f9b47-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="f9b47-103">指定された keyfile またはキー コンテナーの公開キー トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9b47-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b47-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9b47-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b47-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9b47-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="f9b47-106">キーのファイル名。</span><span class="sxs-lookup"><span data-stu-id="f9b47-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="f9b47-107">キー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="f9b47-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="f9b47-108">キー トークンが格納されるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="f9b47-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="f9b47-109">(バイト単位) で示されたバッファーのサイズを指定`pvPublicKeyToken`です。</span><span class="sxs-lookup"><span data-stu-id="f9b47-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="f9b47-110">関数が戻るときに、実際の使用バイト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f9b47-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9b47-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9b47-111">Return Value</span></span>  
 <span data-ttu-id="f9b47-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="f9b47-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b47-113">要件</span><span class="sxs-lookup"><span data-stu-id="f9b47-113">Requirements</span></span>  
 <span data-ttu-id="f9b47-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="f9b47-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b47-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9b47-115">See Also</span></span>  
 [<span data-ttu-id="f9b47-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9b47-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f9b47-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9b47-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f9b47-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="f9b47-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
