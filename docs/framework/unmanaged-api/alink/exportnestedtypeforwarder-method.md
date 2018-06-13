---
title: ExportNestedTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dfb31a2fad8a07b3821ac85bbb43b25693f11d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404107"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="7714d-102">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="7714d-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="7714d-103">指定したアセンブリの型のテーブルを入れ子にされた型の型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="7714d-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7714d-104">構文</span><span class="sxs-lookup"><span data-stu-id="7714d-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7714d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7714d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7714d-106">エクスポートするアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="7714d-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7714d-107">ファイルの種類を定義するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="7714d-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="7714d-108">型のトークンです。</span><span class="sxs-lookup"><span data-stu-id="7714d-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="7714d-109">親の種類のトークンです。</span><span class="sxs-lookup"><span data-stu-id="7714d-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="7714d-110">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="7714d-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7714d-111">`ComType` フラグのように`tdPublic`または`tdNested`です。</span><span class="sxs-lookup"><span data-stu-id="7714d-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="7714d-112">エクスポート型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7714d-112">Receives token of export type.</span></span> <span data-ttu-id="7714d-113">これは、入れ子にされた型の生成にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="7714d-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7714d-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="7714d-114">Return Value</span></span>  
 <span data-ttu-id="7714d-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="7714d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7714d-116">要件</span><span class="sxs-lookup"><span data-stu-id="7714d-116">Requirements</span></span>  
 <span data-ttu-id="7714d-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="7714d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7714d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7714d-118">See Also</span></span>  
 [<span data-ttu-id="7714d-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7714d-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7714d-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7714d-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7714d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="7714d-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
