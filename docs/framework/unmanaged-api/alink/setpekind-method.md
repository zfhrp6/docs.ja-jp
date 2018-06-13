---
title: SetPEKind メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405894"
---
# <a name="setpekind-method"></a><span data-ttu-id="09199-102">SetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="09199-102">SetPEKind Method</span></span>
<span data-ttu-id="09199-103">ポータブル実行可能ファイルの種類、コンピューター固有またはコンピューターにもとらわれないのいずれかを判断します。</span><span class="sxs-lookup"><span data-stu-id="09199-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09199-104">構文</span><span class="sxs-lookup"><span data-stu-id="09199-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="09199-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09199-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="09199-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="09199-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="09199-107">PE の種類を設定する対象のファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="09199-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="09199-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="09199-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="09199-109">によって示される、PE の種類、 [CorPEKind 列挙型](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="09199-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="09199-110">ターゲット コンピューターのアーキテクチャ、NT ヘッダーで指定されています。</span><span class="sxs-lookup"><span data-stu-id="09199-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09199-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="09199-111">Return Value</span></span>  
 <span data-ttu-id="09199-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="09199-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09199-113">要件</span><span class="sxs-lookup"><span data-stu-id="09199-113">Requirements</span></span>  
 <span data-ttu-id="09199-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="09199-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09199-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="09199-115">See Also</span></span>  
 [<span data-ttu-id="09199-116">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="09199-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="09199-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09199-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="09199-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09199-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="09199-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="09199-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
